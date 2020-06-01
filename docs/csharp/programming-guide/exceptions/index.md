---
title: Wyjątki i obsługa wyjątków — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 0ba123fa9f9aacd0876f07bdf3ae7bb9159a6834
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241711"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)

Funkcje obsługi wyjątków języka C# ułatwiają potraktowanie wszelkich nieoczekiwanych lub wyjątkowych sytuacji, które występują, gdy program jest uruchomiony. Obsługa wyjątków używa `try` `catch` słów kluczowych, i, `finally` Aby wypróbować akcje, które mogą się nie powieść, aby obsłużyć błędy w przypadku podjęcia decyzji o tym, że jest to uzasadnione, a następnie w celu późniejszego oczyszczenia zasobów. Wyjątki mogą być generowane przez środowisko uruchomieniowe języka wspólnego (CLR), przez platformę .NET lub biblioteki innych firm lub przez kod aplikacji. Wyjątki są tworzone za pomocą `throw` słowa kluczowego.

W wielu przypadkach wyjątek może zostać wygenerowany nie przez metodę, którą kod został wywołany bezpośrednio, ale przez inną metodę w stosie wywołań. W takim przypadku środowisko CLR spowoduje przewinięcie stosu, wyszukanie metody z `catch` blokiem dla określonego typu wyjątku i spowoduje wykonanie pierwszego takiego `catch` bloku, który w przypadku znalezienia. Jeśli nie znajdzie odpowiedniego `catch` bloku w dowolnym miejscu w stosie wywołań, zakończy proces i wyświetli komunikat dla użytkownika.

W tym przykładzie metoda testów dla dzielenia przez zero i przechwytywania błędu. Bez obsługi wyjątków ten program zostanie przerwany z powodu **nieobsługiwanego błędu DivideByZeroException** .

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Przegląd wyjątków

Wyjątki mają następujące właściwości:

- Wyjątki są typami, do których wszystkie ostatecznie pochodzą `System.Exception` .
- Użyj `try` bloku wokół instrukcji, które mogą zgłaszać wyjątki.
- Gdy w bloku wystąpi wyjątek `try` , przepływ sterowania przechodzi do pierwszej powiązanej procedury obsługi wyjątku, która jest obecna w dowolnym miejscu w stosie wywołań. W języku C# `catch` słowo kluczowe jest używane do definiowania programu obsługi wyjątków.
- Jeśli nie ma obsługi wyjątków dla danego wyjątku, program przestanie działać z komunikatem o błędzie.
- Nie należy przechwytywać wyjątku, chyba że można go obsłużyć i pozostawić aplikację w znanym stanie. Jeśli przechwytujesz `System.Exception` , ponownie zgłoś go przy użyciu `throw` słowa kluczowego na końcu `catch` bloku.
- Jeśli `catch` blok definiuje zmienną wyjątku, można jej użyć, aby uzyskać więcej informacji na temat typu wyjątku, który wystąpił.
- Wyjątki mogą być jawnie generowane przez program za pomocą `throw` słowa kluczowego.
- Obiekty wyjątków zawierają szczegółowe informacje o błędzie, takie jak stan stosu wywołań i opis tekstowy błędu.
- Kod w `finally` bloku jest wykonywany nawet wtedy, gdy zostanie zgłoszony wyjątek. Użyj `finally` bloku, aby zwolnić zasoby, na przykład aby zamknąć wszystkie strumienie lub pliki, które zostały otwarte w `try` bloku.
- Wyjątki zarządzane w programie .NET są implementowane na podstawie mechanizmu obsługi wyjątków strukturalnych Win32. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) i [kurs awarii na głębokości obsługi wyjątków strukturalnych Win32](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Sekcje pokrewne

Więcej informacji o wyjątkach i obsłudze wyjątków można znaleźć w następujących artykułach:

- [Używanie wyjątków](using-exceptions.md)
- [Obsługa wyjątków](exception-handling.md)
- [Tworzenie i zgłaszanie wyjątków](creating-and-throwing-exceptions.md)
- [Wyjątki generowane przez kompilator](compiler-generated-exceptions.md)
- [Jak obsłużyć wyjątek przy użyciu try/catch (Przewodnik programowania w języku C#)](how-to-handle-an-exception-using-try-catch.md)
- [Wykonywanie czyszczenia kodu za pomocą instrukcji finally](how-to-execute-cleanup-code-using-finally.md)
- [Przechwytywanie wyjątku typu non-CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- <xref:System.SystemException>
- [Przewodnik programowania w języku C#](../index.md)
- [Słowa kluczowe języka C#](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Wyjątki](../../../standard/exceptions/index.md)
