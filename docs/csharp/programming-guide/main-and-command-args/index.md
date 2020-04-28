---
title: Main () i argumenty wiersza polecenia — Przewodnik programowania w języku C#
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
ms.openlocfilehash: 190216b01ea416aedbca270a6d7a5acbf0c2e797
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200122"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () i argumenty wiersza polecenia (Przewodnik programowania w języku C#)

`Main` Metoda jest punktem wejścia aplikacji języka C#. (Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, `Main` jest to pierwsza metoda wywoływana.

 W programie w języku C# może istnieć tylko jeden punkt wejścia. Jeśli masz więcej niż jedną klasę, która ma `Main` metodę, musisz skompilować program z opcją kompilatora **/Main** , aby określić, która `Main` Metoda ma być używana jako punkt wejścia. Aby uzyskać więcej informacji, zobacz [— Main (opcje kompilatora C#)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Omówienie

- `Main` Metoda jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.
- `Main`jest zadeklarowany wewnątrz klasy lub struktury. `Main`musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md). (W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.
- `Main``void`może mieć parametr `int`,, lub, zaczynając od języka C# 7,1 `Task`lub `Task<int>` typu zwracanego.
- Jeśli i tylko wtedy `Main` , gdy `Task` zwraca `Task<int>`lub, deklaracja `Main` może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator. Należy zauważyć, że ta `async void Main` Metoda nie wyklucza metody.
- `Main` Metodę można zadeklarować z parametrem zawierającym `string[]` argumenty wiersza polecenia lub bez niego. Korzystając z programu Visual Studio do tworzenia aplikacji systemu Windows, można dodać parametr ręcznie lub użyć <xref:System.Environment.GetCommandLineArgs> metody do uzyskania [argumentów wiersza polecenia](command-line-arguments.md). Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero. W przeciwieństwie do języka C i C++, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w `args` tablicy, ale jest to pierwszy element <xref:System.Environment.GetCommandLineArgs> metody.

Poniżej znajduje się lista prawidłowych `Main` podpisów:

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

Powyższe przykłady używają modyfikatora Public akcesor. Jest to typowy, ale nie jest wymagany.

Dodawanie `async` `Task`i, `Task<int>` typy zwracane upraszczają kod programu, gdy aplikacje konsolowe muszą rozpoczynać pracę `await` i asynchroniczne operacje `Main`w programie.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [Wewnątrz programu C#](../inside-a-program/index.md)
