---
title: "&lt;system.serviceModel&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "<system.serviceModel> 要素"
  - "system.serviceModel 要素"
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# &lt;system.serviceModel&gt;
この構成セクションは、すべての [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel 構成要素を含みます。  
  
## 構文  
  
```  
  
<system.serviceModel>  
    <behaviors>  
    </behaviors>  
    <bindings>  
    </bindings>  
    <client>  
    </client>  
    <comContracts>  
    </comContracts>  
    <commonBehaviors>  
    </commonBehaviors>  
    <diagnostics>  
    </diagnostics>  
    <extensions>  
    </extensions>  
    <protocolMapping>  
    </protocolMapping>  
    <routing>  
    </routing>  
    <serviceHostingEnvironment>  
    </serviceHostingEnvironment>  
    <services>  
    </services>  
    <standardEndpoints>  
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<behaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、エンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。  各動作要素は、その一意の `name` 属性で識別されます。|  
|[\<bindings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|このセクションには、標準バインディングおよびカスタム バインディングのコレクションが保持されます。  各エントリは、その一意の `name` により識別されます。  サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。|  
|[\<client\>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|このセクションは、クライアントがサービスの接続に使用するエンドポイントの一覧を含みます。|  
|[\<comContracts\>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|このセクションは、WCF と COM 相互運用が有効な COM コントラクトを定義します。|  
|[\<commonBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|このセクションは、machine.config ファイルでだけ定義できます。  このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。  各コレクションは、コンピューター上の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のすべてのエンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。  ある動作が `<commonBehaviors>` と `<behaviors>` の両方のセクションで定義されている場合は、\<behaviors\> セクション内の動作が優先されます。|  
|[\<extensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|このセクションには、拡張のコレクションが含まれています。これにより、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できるようになります。|  
|[\<diagnostics\>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|このセクションには、WCF の診断機能の設定が含まれます。  ユーザーはトレース、パフォーマンス カウンター、および WMI プロバイダーを有効または無効にしたり、カスタム メッセージ フィルターを追加したりできます。|  
|[\<protocolMapping\>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|このセクションは、トランスポート プロトコル スキーム \(http、net.tcp、net.pipe など\) と WCF バインディング間の既定のプロトコル マッピング セットを定義します。|  
|[\<routing\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|このセクションは、受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルター セットと、フィルターが一致するときにメッセージを送信するターゲット エンドポイントを指定するルーティング テーブルを定義します。|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|このセクションは、環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。  このセクションが空の場合は、既定の型が使用されます。|  
|[\<services\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|このセクションには、サービスのコレクションが含まれています。  アセンブリで定義された各サービスの場合、この要素は、サービスの設定を指定する `service` 要素を含みます。|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|このセクションは、再使用可能な構成済みのエンドポイントである標準エンドポイントのコレクションを定義します。  標準エンドポイントは、固定値に設定されたアドレス、バインディング、およびコントラクトの 1 つ以上の属性を持ちます。  たとえば、探索エンドポイントでは、コントラクトが固定されています。  標準エンドポイントを使用して、カスタム バインディングの定義と同様に新しいプロパティを指定して、サービス エンドポイントを拡張することもできます。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|\<configuration\>|.NET 構成ファイルのすべての構成要素のルート要素。|  
  
## 解説  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は、他の製品の構成セクションに要素を追加しません。  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスは、構成ファイルの `services` セクションで定義されます。  アセンブリには、任意の数のサービスを含めることができます。  各サービスには、独自の `service` 設定セクションがあります。  セクションとその内容は、サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。  
  
 サービスの `name` 属性だけが必須項目です。  既定では、サービスの名前は、サービスの実装に使用される、基になる CLR 型を示します。ただし、<xref:System.ServiceModel.ServiceContractAttribute> の ConfigurationName プロパティを変更して、CLR 型要件をオーバーライドすることもできます。  
  
 `behaviorConfiguration` 属性は省略できます。  サービスが使用するサービス動作を識別します。  この属性で指定された動作は、同じ構成ファイルの範囲内に定義されたサービス動作にリンクしている必要があります。  たとえば、同一ファイルまたは親ファイルです。  
  
 各サービスでは、`endpoint` 要素で定義された 1 つまたは複数のエンドポイントが公開されます。  各エンドポイントには、独自のアドレスおよびバインディングがあります。  構成ファイル内で使用されるすべてのバインディングは、そのファイルのスコープ内で定義される必要があります。  
  
 バインディングは、`name` 属性と `bindingConfiguration` 属性の組み合わせによってエンドポイントにリンクされます。  `binding` 属性は、バインディングが定義されているセクションで定義します。  `bindingConfiguration` 属性は、バインディング セクション内で使用される構成済みバインディングを定義します。  バインディング セクションでは、複数の構成済みバインディングを定義できます。  
  
## 使用例  
 これは、WCF 構成ファイルの例です。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>