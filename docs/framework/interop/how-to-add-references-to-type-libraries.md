---
title: "方法: タイプ ライブラリへの参照を追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a0c4fc9b96ec310e20839be851cfddbb34e09201
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-add-references-to-type-libraries"></a>方法: タイプ ライブラリへの参照を追加する
Visual Studio は、タイプ ライブラリに参照を追加する際に、メタデータを含む相互運用機能アセンブリを生成します。 プライマリ相互運用機能アセンブリが使用可能な場合、Visual Studio では、新しい相互運用機能アセンブリを生成する前に既存のアセンブリが使用されます。  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Visual Studio でタイプ ライブラリへの参照を追加するには  
  
1.  Windows Setup.exe ファイルで COM DLL ファイルまたは EXE ファイルがインストールされない場合は、このファイルをコンピューターにインストールします。  
  
2.  **[プロジェクト]**、**[参照の追加]** の順に選択します。  
  
3.  参照マネージャーで、**[COM]** を選択します。  
  
4.  一覧からタイプ ライブラリを選択するか、.tlb ファイルを参照します。  
  
5.  **[OK]**をクリックします。  
  
6.  ソリューション エクスプローラーで、追加した参照のショートカット メニューを開き、**[プロパティ]** を選択します。  
  
7.  **[プロパティ]** ウィンドウで、**[相互運用機能型の埋め込み]** プロパティが **[True]** に設定されていることを確認します。 その結果、Visual Studio により、COM 型の型情報が実行可能ファイルに埋め込まれ、アプリでプライマリ相互運用機能アセンブリを配置する必要がなくなります。  
  
> [!NOTE]
>  メニュー オプションおよびダイアログ ボックス オプションは、使用中の Visula Studio のバージョンによって異なる場合があります。  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>コマンド ライン コンパイルのために参照をタイプ ライブラリに追加するには  
  
1.  「[How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)」(方法: 相互運用機能アセンブリをタイプ ライブラリから生成する) の説明に従って、相互運用機能アセンブリを生成します。  
  
2.  相互運用機能アセンブリ名を指定して [/link (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) または [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) コンパイラ オプションを使用し、COM 型の型情報を実行可能ファイルに埋め込みます。  
  
## <a name="see-also"></a>関連項目  
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)   
 [チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)   
 [チュートリアル: マネージ アセンブリからの型の埋め込み](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [-link (C# コンパイラ オプション)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)   
 [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md)

