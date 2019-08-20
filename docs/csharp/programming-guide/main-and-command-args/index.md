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
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588906"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main () i argumenty wiersza polecenia (C# Przewodnik programowania)

Metoda jest punktem wejścia C# aplikacji. `Main` (Biblioteki i usługi nie wymagają `Main` metody jako punktu wejścia.) Gdy aplikacja jest uruchomiona, `Main` jest to pierwsza metoda wywoływana.

 W C# programie może istnieć tylko jeden punkt wejścia. Jeśli masz więcej niż jedną klasę, która ma `Main` metodę, musisz skompilować program z opcją kompilatora **/Main** , aby określić, która `Main` Metoda ma być używana jako punkt wejścia. Aby uzyskać więcej informacji, zobacz [/MainC# (opcje kompilatora)](../../language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>Omówienie

- `Main` Metoda jest punktem wejścia programu wykonywalnego; jest to miejsce, w którym kontrola programu zaczyna się i skończy.
- `Main`jest zadeklarowany wewnątrz klasy lub struktury. `Main`musi być [statyczna](../../language-reference/keywords/static.md) i nie musi być [publiczny](../../language-reference/keywords/public.md). (W poprzednim przykładzie otrzymuje on domyślny dostęp do [prywatnego](../../language-reference/keywords/private.md)). Otaczająca Klasa lub struktura nie musi być statyczna.
- `Main``void`może mieć, `int`, lub, zaczynając od C# 7,1, `Task`lub `Task<int>` typ zwracany.
- Jeśli i tylko wtedy `Main` , gdy `Task` zwraca `Task<int>` `Main` lub, deklaracja może zawierać [`async`](../../language-reference/keywords/async.md) modyfikator. Należy zauważyć, że ta `async void Main` Metoda nie wyklucza metody.
- Metodę można zadeklarować z parametrem zawierającym argumenty wiersza polecenia lub bez niego `string[]`. `Main` W przypadku tworzenia aplikacji systemu Windows przy użyciu programu Visual Studio można dodać parametr ręcznie lub użyć <xref:System.Environment> klasy w celu uzyskania argumentów wiersza polecenia. Parametry są odczytywane jako argumenty wiersza polecenia indeksowane przez zero. W przeciwieństwie do C++języka C i, nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia.

`async` Dodawanie i, `await` `Task` `Main`typy zwracane upraszczają kod programu, gdy aplikacje konsolowe muszą rozpoczynać pracę i asynchroniczne operacje w programie. `Task<int>`

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Metody](../classes-and-structs/methods.md)
- [Konstrukcja programu C#](../inside-a-program/index.md)
