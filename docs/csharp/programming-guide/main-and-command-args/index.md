---
title: Main () i argumenty wiersza polecenia — C# Przewodnik programowania
ms.custom: seodec18
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
ms.openlocfilehash: 5de7e565560928b1867ba96c8937fd354c276806
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774122"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () i argumenty wiersza polecenia (C# Przewodnik programowania)

Metoda `Main` jest punktem wejścia C# aplikacji. (Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, Metoda `Main` jest pierwszą metodą, która jest wywoływana.

 W C# programie może istnieć tylko jeden punkt wejścia. Jeśli masz więcej niż jedną klasę, która ma metodę `Main`, musisz skompilować program z opcją kompilatora **/Main** , aby określić, która metoda `Main` ma być używana jako punkt wejścia. Aby uzyskać więcej informacji, zobacz [— MainC# (opcje kompilatora)](../../language-reference/compiler-options/main-compiler-option.md).

[!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Omówienie

- Metoda `Main` jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.
- `Main` jest zadeklarowana wewnątrz klasy lub struktury. `Main` musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md). (W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.
- `Main` może mieć `void`, `int` lub, zaczynając od C# 7,1, `Task` lub `Task<int>` typu zwracanego.
- Jeśli i tylko wtedy, gdy `Main` zwraca `Task` lub `Task<int>`, deklaracja `Main` może zawierać modyfikator [`async`](../../language-reference/keywords/async.md) . Należy zauważyć, że ta metoda nie wyklucza metody `async void Main`.
- Metodę `Main` można zadeklarować z parametrem `string[]` zawierającym argumenty wiersza polecenia lub bez niego. W przypadku tworzenia aplikacji systemu Windows przy użyciu programu Visual Studio można dodać parametr ręcznie lub użyć metody <xref:System.Environment.GetCommandLineArgs>, aby uzyskać [argumenty wiersza polecenia](command-line-arguments.md). Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero. W przeciwieństwie do C++języka C, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia w tablicy `args`, ale jest to pierwszy element metody <xref:System.Environment.GetCommandLineArgs>.

Dodanie `async` i `Task` `Task<int>` typy zwracane upraszcza kod programu, gdy aplikacje konsolowe muszą uruchamiać i `await` operacje asynchroniczne w `Main`.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [Konstrukcja programu C#](../inside-a-program/index.md)
