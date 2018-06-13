---
title: Main() i argumenty wiersza poleceń (C# przewodnik programowania w języku)
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
ms.openlocfilehash: 03d6e7185a0a16589fb612724be52ce51e813173
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332371"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() i argumenty wiersza poleceń (C# przewodnik programowania w języku)

`Main` Metoda jest punkt wejścia aplikacji C#. (Bibliotek, usług i nie wymagają `Main` metody jako punkt wejścia.) Po uruchomieniu aplikacji `Main` pierwsza metoda wywoływana jest metoda.

 Może istnieć tylko jeden punkt wejścia w programie C#. Jeśli masz więcej niż jedną klasę, która ma `Main` metody, należy skompilować programu z **/main** opcję kompilatora, aby określić, które `Main` metoda do użycia jako punkt wejścia. Aby uzyskać więcej informacji, zobacz [/main (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Omówienie

- `Main` Metody jest punkt wejścia programu wykonywalnego, a gdzie formantu programu początkowej i końcowej.
- `Main` jest zadeklarowana w klasie lub strukturze. `Main` musi być [statycznych](../../../csharp/language-reference/keywords/static.md) i nie muszą być [publicznego](../../../csharp/language-reference/keywords/public.md). (W poprzedniego przykładu, otrzymuje dostęp do domyślnej z [prywatnej](../../../csharp/language-reference/keywords/private.md).) Otaczającej klasy lub struktury nie musi być statyczna.
- `Main` może posiadać `void`, `int`, lub w programie C# 7.1, `Task`, lub `Task<int>` typ zwracany.
- Tylko wtedy, gdy `Main` zwraca `Task` lub `Task<int>`, deklaracja `Main` mogą obejmować [ `async` ](../../language-reference/keywords/async.md) modyfikator. Należy pamiętać, że jest to wyraźnie wyklucza `async void Main` metody.
- `Main` Metody mogą być deklarowane z lub bez `string[]` parametr, który zawiera argumenty wiersza polecenia. Przy użyciu programu Visual Studio do tworzenia aplikacji systemu Windows, użytkownik może ręcznie dodaj parametr w przeciwnym razie użyj <xref:System.Environment> klasy uzyskanie argumenty wiersza polecenia. Parametry są odczytywane jako indeksie zero argumentów wiersza polecenia. W przeciwieństwie do C i C++ nazwa programu nie jest traktowana jako pierwszy argument wiersza polecenia.

Dodanie `async` i `Task`, `Task<int>` zwracać typów upraszcza kodu programu, gdy konieczne uruchomienie aplikacji konsoli i `await` operacji asynchronicznych w `Main`.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także
[Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
[Konstrukcja programu C#](../../../csharp/programming-guide/inside-a-program/index.md)  
