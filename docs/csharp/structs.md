---
title: "構造体 - C# ガイド"
description: "構造体型と、構造体を作成する方法について説明します"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/12/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e2a4bfdb46a69113d5eb8949df4ccf902acf9dee
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="structs"></a>構造体
"*構造体*" は値の型です。 構造体が作成されると、構造体が割り当てられている変数にはその構造体の実際のデータが設定されます。 構造体が新しい変数に割り当てられると、そのデータがコピーされます。 したがって、新しい変数と元の変数には、同じデータのコピーが別個に含まれることになります。 一方のコピーに対して行われた変更は、もう一方のコピーには影響しません。

値型の変数は、その値を直接含みます。つまり、変数がどのようなコンテキストで宣言されたとしても、必ずメモリがインラインで割り当てられます。 値型の変数には、独立したヒープ割り当てやガベージ コレクションのオーバーヘッドはありません。  
  
値型には、[構造体](./language-reference/keywords/struct.md)と[列挙体](./language-reference/keywords/enum.md)の 2 つのカテゴリがあります。  
  
組み込みの数値型は構造体であり、次のようにしてアクセスできるプロパティとメソッドを持ちます。  
  
[!code-csharp[静的メソッド](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
ただし、宣言とそこへの値の代入は、あたかも単純な非集約型であるかのように行うことができます。  
  
[!code-csharp[値の割り当て](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
値型は、"*シール*" されています。たとえば @System.Int32 から値型を派生させることはできません。構造体は @System.ValueType からしか継承できないため、任意のユーザー定義型または構造体を継承する構造体を定義することはできません。 ただし、構造体は 1 つ以上のインターフェイスを実装できます。 構造体型は、インターフェイス型にキャストできます。これを行うと、"*ボックス化*" 操作によって、構造体がマネージ ヒープ上の参照型オブジェクト内にラップされます。 ボックス化操作が発生するのは、入力パラメーターとして @System.Object を受け取るメソッドに値型を渡した場合です。 詳細については、「[ボックス化とボックス化解除](./programming-guide/types/boxing-and-unboxing.md )」を参照してください。  
  
独自のカスタム値型を作成するには、[struct](./language-reference/keywords/struct.md) キーワードを使用します。 通常、構造体は、次の例に示すように、少数の関連する変数のコンテナーとして使用します。  
  
[!code-csharp[struct キーワード](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
.NET Framework における値の型の詳細については、「[共通型システム](../standard/common-type-system.md)」を参照してください。  
    
構造体は、構文上はクラスとほとんど変わりませんが、次のようにクラスよりも制限されます。  
  
-   構造体宣言内では、`const` または `static` と宣言されているフィールド以外は初期化できません。  
  
-   構造体では、既定のコンストラクター (パラメーターなしのコンストラクター) やファイナライザーを宣言できません。  
  
-   構造体は、割り当て時にコピーされます。 構造体を新しい変数に割り当てると、すべてのデータがコピーされ、新しいコピーを変更しても、元のコピーのデータは変更されません。 これは、Dictionary<string, myStruct> などの値の型のコレクションを使用する際に重要です。  
  
-   構造体は値型ですが、クラスは参照型です。  
  
-   クラスとは異なり、構造体は `new` 演算子を使用せずにインスタンス化できます。  
  
-   構造体は、パラメーターのあるコンストラクターを宣言できます。  
  
-   構造体は、他の構造体やクラスから継承できず、基本クラスになることはできません。 すべての構造体が @System.ValueType を直接継承し、System.ValueType は @System.Object を継承します。  
  
-   構造体は、インターフェイスを実装できます。

## <a name="literal-values"></a>リテラル値  
C# では、リテラル値の型がコンパイラによって決定されます。 数値リテラルの型指定の方法を指定するには、その数値の末尾に文字を付加します。 たとえば、値 4.56 を float 型として扱うには、数値の後に "f" または "F" を付加して、`4.56f` のように指定します。 文字を付加しない場合、リテラルの `double` 型はコンパイラによって推論されます。 文字サフィックスによって指定できる型の詳細については、「[値型](./language-reference/keywords/value-types.md)」の各型のリファレンス ページを参照してください。  
  
リテラルは型指定され、すべての型は最終的に @System.Object から派生するため、次のようなコードを記述してコンパイルできます。  
  
[!code-csharp[リテラル値](../../samples/snippets/csharp/concepts/structs/literals.cs)]

最後の 2 つの例では、C# 7.0 で導入された言語機能を紹介します。 最初の機能を使用すると、アンダースコア文字を、数値リテラルの "*桁区切り記号*" として使用できます。 このアンダースコア文字を数字の任意の場所に配置して、読みやすくすることができます。 値には影響はありません。

もう 1 つの機能は "*バイナリ リテラル*" で、これにより 16 進数表記ではなく、ビット パターンを直接指定できます。

## <a name="nullable-types"></a>Null 許容型  
値型には、通常、[null](./language-reference/keywords/null.md) 値を割り当てることができません。 しかし、型の後ろに **?**  を付けることによって、null 値を設定できる値型を作成できます。 たとえば、**int?** は、[null](./language-reference/keywords/null.md) も設定できる **int** 型です。 CTS では、null 許容型は一般的な構造体型 @System.Nullable%601 のインスタンスです。 Null 許容型は、数値が null になる可能性のあるデータベースとの間でデータを受け渡しする場合に、特に便利です。 詳細については、「[null 許容型 (C# プログラミング ガイド)](./programming-guide/nullable-types/index.md)」を参照してください。

## <a name="see-also"></a>関連項目
[クラス](classes.md)

[基本型](basic-types.md)

