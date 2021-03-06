---
title: "Visual Studio 2017 での Hello World アプリケーションの発行"
description: "発行では、アプリケーションを実行するために必要なファイルのセットを作成します。"
keywords: ".NET, .NET Core, コンソール アプリケーション, 発行, 配置"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.translationtype: HT
ms.sourcegitcommit: e0271ba3392ce8861dc916714af8c16d4581ce4f
ms.openlocfilehash: 025e132cd5b6a44e98a1270e24ba6b2f9f12812c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/14/2017

---

# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a>Visual Studio 2017 での Hello World アプリケーションの発行

「[Visual Studio 2017 での .NET Core を使用した C# Hello World アプリケーションの構築](with-visual-studio.md)」または「[Visual Studio 2017 での .NET Core を使用した Visual Basic Hello World アプリケーションの構築](vb-with-visual-studio.md)」では、Hello World コンソール アプリケーションを構築しました。 「[Visual Studio 2017 での C# Hello World アプリケーションのデバッグ](debugging-with-visual-studio.md)」では、Visual Studio デバッガーを使ってアプリケーションをテストしました。 正しく動作することが確認できたので、他のユーザーが使用できるように発行することができます。 発行では、アプリケーションを実行するために必要なファイルのセットが作成されます。これらのファイルは、対象コンピューターにコピーすることで配置できます。

アプリケーションを発行および実行するには 

1. Visual Studio がアプリケーションのリリース バージョンをビルドしていることを確認します。 必要に応じて、ツール バーのビルド構成の設定を **[デバッグ]** から **[リリース]** に変更します。

   ![Visual Studio ツール バー](media/publishing-with-visual-studio/toolbar.png)

1. **HelloWorld** プロジェクト (HelloWorld ソリューションではなく) を右クリックし、メニューから **[発行]** を選びます。 Visual Studio のメイン メニューの **[ビルド]** から **[HelloWorld を発行]** を選択することもできます。

   ![Visual Studio ツール バー](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio ツール バー](media/publishing-with-visual-studio/publishwindow.png)

1. コンソール ウィンドウが開きます。 たとえば、Windows タスク バーの **[検索するテキストをここに入力]** テキスト ボックスに「`Command Prompt`」 (または省略して「`cmd`」) と入力し、**コマンド プロンプト** デスクトップ アプリを選ぶか、コマンド プロンプトが検索結果で選択されている場合は Enter キーを押して、コンソール ウィンドウを開きます。

1. アプリケーションのプロジェクト ディレクトリの `bin\release\PublishOutput` サブディレクトリで、発行されたアプリケーションに移動します。 次の図に示すように、発行された出力には次の 4 つのファイルが含まれます。

      * *HelloWorld.deps.json*
      * *HelloWorld.dll*
      * *HelloWorld.pdb* (配置は省略可能)
      * *HelloWorld.runtimeconfig.json*

   *HelloWorld.pdb* ファイルには、デバッグ シンボルが含まれています。 このファイルはアプリケーションと一緒に配置する必要はありませんが、発行されるバージョンのアプリケーションをデバッグする必要がある場合に保存しておく必要があります。

   ![発行されたファイルが表示されているコンソール ウィンドウ](media/publishing-with-visual-studio/publishedfiles.png)

発行プロセスでは、フレームワークに依存する展開が作成されます。これは、.NET Core がシステムにインストールされていれば、.NET Core によってサポートされる任意のプラットフォームで発行されたアプリケーションが動作する配置の種類です。 ユーザーはコンソール ウィンドウから `dotnet HelloWorld.dll` コマンドを発行することによって、アプリケーションを実行できます。

.NET Core アプリケーションの発行と展開の詳細については、「[.NET Core アプリケーション展開](../../core/deploying/index.md)」を参照してください。

