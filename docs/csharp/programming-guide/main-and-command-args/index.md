---
title: Argumenty Main() i command-line — Przewodnik programowania C#
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: 0571ec6dbc42f103ec922a6b2b13a52510640a78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75700604"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Argumenty Main() i command-line (Przewodnik programowania C#)

Metoda `Main` jest punktem wejścia aplikacji C#. (Biblioteki i usługi nie `Main` wymagają metody jako punktu wejścia). Po uruchomieniu aplikacji `Main` metoda jest pierwszą metodą, która jest wywoływana.

 W programie C# może być tylko jeden punkt wejścia. Jeśli masz więcej niż jedną `Main` klasę, która ma metodę, należy skompilować program `Main` z **/main** kompilator opcji, aby określić metodę do użycia jako punkt wejścia. Aby uzyskać więcej informacji, zobacz [-main (Opcje kompilatora C#)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Omówienie

- Metoda `Main` jest punktem wejścia programu wykonywalnego; to jest miejsce, w którym rozpoczyna się i kończy kontrolka programu.
- `Main`jest zadeklarowana wewnątrz klasy lub struktury. `Main`musi być [statyczny](../../language-reference/keywords/static.md) i nie musi być [publiczny.](../../language-reference/keywords/public.md) (We wcześniejszym przykładzie otrzymuje domyślny dostęp [prywatnych](../../language-reference/keywords/private.md).) Otaczającej klasy lub struktury nie jest wymagane, aby być statyczne.
- `Main`może mieć `void`, `int`lub, począwszy od C `Task`# `Task<int>` 7.1, lub typu zwracanego.
- Jeśli i `Main` tylko `Task` wtedy, gdy zwraca `Task<int>`lub , deklaracja `Main` może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator. Należy zauważyć, że to `async void Main` wyraźnie wyklucza metodę.
- Metodę `Main` można zadeklarować z `string[]` parametrem lub bez, który zawiera argumenty wiersza polecenia. Korzystając z programu Visual Studio do tworzenia aplikacji systemu Windows, można dodać parametr ręcznie lub użyć <xref:System.Environment.GetCommandLineArgs> tej metody do uzyskania [argumentów wiersza polecenia](command-line-arguments.md). Parametry są odczytywane jako argumenty wiersza polecenia indeksowane zero. W przeciwieństwie do C i C++, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w `args` tablicy, ale jest pierwszym elementem <xref:System.Environment.GetCommandLineArgs> metody.

Poniżej znajduje się lista `Main` prawidłowych podpisów:

```csharp
public static void Main() { }
public static int Main() { }
public static void Main(string[] args) { }
public static int Main(string[] args) { }
public static async Task Main() { }
public static async Task<int> Main() { }
public static async Task Main(string[] args) { }
public static async Task<int> Main(string[] args) { }
```

Dodawanie `async` i `Task`, `Task<int>` zwraca typy upraszcza kod programu, gdy aplikacje konsoli trzeba uruchomić i `await` operacji asynchronicznych w `Main`programie .

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Przewodnik programowania języka C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [Konstrukcja programu C#](../inside-a-program/index.md)
