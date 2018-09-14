---
title: Main() i argumenty wiersza poleceń (C# Programming Guide)
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
ms.openlocfilehash: 144d03edf28464717430bd0ae83db637578d8296
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45590913"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() i argumenty wiersza poleceń (C# Programming Guide)

`Main` Metodą jest punkt wejścia aplikacji w języku C#. (Biblioteki i usługi nie wymagają `Main` metodę jako punkt wejścia.) Po uruchomieniu aplikacji `Main` metodą jest pierwsza metoda, która jest wywoływana.

 Może istnieć tylko jeden punkt wejścia w programie C#. Jeśli masz więcej niż jedną klasę, która ma `Main` metody, należy skompilować program jest połączony z **/main** opcję kompilatora, aby określić, które `Main` metoda do użycia jako punkt wejścia. Aby uzyskać więcej informacji, zobacz [/main (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Omówienie

- `Main` Metodą jest punkt wejścia programu wykonywalnego; gdzie kontrolę nad programem rozpoczyna i kończy.
- `Main` jest zadeklarowana wewnątrz klasy lub struktury. `Main` musi być [statyczne](../../../csharp/language-reference/keywords/static.md) i nie muszą być [publicznych](../../../csharp/language-reference/keywords/public.md). (We wcześniejszym przykładzie otrzymuje dostęp do domyślnej [prywatnej](../../../csharp/language-reference/keywords/private.md).) Otaczającej klasy lub struktury nie musi być statyczna.
- `Main` można albo mieć `void`, `int`, lub rozpocząć budowanie C# 7.1 `Task`, lub `Task<int>` typ zwracany.
- Tylko wtedy, gdy `Main` zwraca `Task` lub `Task<int>`, deklaracja `Main` mogą obejmować [ `async` ](../../language-reference/keywords/async.md) modyfikator. Należy zauważyć, że specjalnie nie obejmuje to `async void Main` metody.
- `Main` Metody mogą być deklarowane z lub bez `string[]` parametr, który zawiera argumenty wiersza polecenia. Przy użyciu programu Visual Studio do tworzenia aplikacji Windows, użytkownik może ręcznie dodaj parametr — w przeciwnym razie użyj <xref:System.Environment> klasy w celu uzyskiwania argumentów wiersza polecenia. Parametry są odczytywane jako argumenty wiersza polecenia o indeksie zero. W przeciwieństwie do C i C++ nazwę programu, nie jest traktowana jako pierwszy argument wiersza polecenia.

Dodanie `async` i `Task`, `Task<int>` zwraca typy upraszcza kod programu, gdy aplikacje konsoli, musisz uruchomić i `await` operacji asynchronicznych w `Main`.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Konstrukcja programu C#](../../../csharp/programming-guide/inside-a-program/index.md)  
