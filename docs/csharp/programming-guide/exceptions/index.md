---
title: Wyjątki i obsługa wyjątków — przewodnik programowania c#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: b883012cf8f72247ff4e0b47a46eee1854e2d534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76735649"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)

Funkcje obsługi wyjątków języka C# ułatwiają radzenie sobie z nieoczekiwanymi lub wyjątkowymi sytuacjami, które występują, gdy program jest uruchomiony. Obsługa wyjątków `try` `catch`używa `finally` , i słów kluczowych, aby wypróbować akcje, które mogą się nie powieść, do obsługi błędów, gdy zdecydujesz, że jest to uzasadnione, a następnie oczyścić zasoby. Wyjątki mogą być generowane przez program runtime języka wspólnego (CLR), przez .NET Framework lub biblioteki innych firm lub przez kod aplikacji. Wyjątki są tworzone przy `throw` użyciu słowa kluczowego.

W wielu przypadkach wyjątek może być generowany nie przez metodę, która została wywołana bezpośrednio przez kod, ale przez inną metodę w dół w stosie wywołań. W takim przypadku CLR będzie odwijać stosu, szukając metody z blokiem `catch` `catch` dla określonego typu wyjątku i wykona pierwszy taki blok, który w przypadku znalezienia. Jeśli nie znajdzie `catch` odpowiedniego bloku w dowolnym miejscu w stosie wywołań, zakończy proces i wyświetli komunikat do użytkownika.

W tym przykładzie metoda testuje podział przez zero i przechwytuje błąd. Bez obsługi wyjątków ten program zakończy się z **DivideByZeroException był nieobsługiwany** błąd.

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Przegląd wyjątków

Wyjątki mają następujące właściwości:

- Wyjątki to typy, które ostatecznie `System.Exception`pochodzą z .
- Użyj `try` bloku wokół instrukcji, które mogą zgłaszać wyjątki.
- Gdy wystąpi wyjątek `try` w bloku, przepływ kontroli skacze do pierwszego skojarzonego programu obsługi wyjątków, który jest obecny w dowolnym miejscu w stosie wywołań. W języku `catch` C#słowo kluczowe służy do definiowania programu obsługi wyjątków.
- Jeśli nie jest program obsługi wyjątków dla danego wyjątku, program przestaje wykonywać z komunikatem o błędzie.
- Nie łapiesz wyjątku, chyba że można go obsłużyć i pozostawić aplikację w znanym stanie. Jeśli złapiesz `System.Exception`, ponownie `throw` wrzuć go za `catch` pomocą słowa kluczowego na końcu bloku.
- Jeśli `catch` blok definiuje zmienną wyjątku, można go użyć, aby uzyskać więcej informacji na temat typu wyjątku, który wystąpił.
- Wyjątki mogą być jawnie generowane przez `throw` program przy użyciu słowa kluczowego.
- Obiekty wyjątku zawierają szczegółowe informacje o błędzie, takie jak stan stosu wywołań i opis tekstowy błędu.
- Kod w `finally` bloku jest wykonywany, nawet jeśli wyjątek. Użyj `finally` bloku, aby zwolnić zasoby, na przykład, aby zamknąć `try` wszystkie strumienie lub pliki, które zostały otwarte w bloku.
- Wyjątki zarządzane w platformie .NET Framework są implementowane na podstawie mechanizmu obsługi wyjątków strukturalnych Win32. Aby uzyskać więcej informacji, zobacz [Obsługa wyjątków strukturalnych (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) i [Kurs awarii na głębokości win32 obsługa wyjątków strukturalnych](http://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Sekcje pokrewne

Zobacz następujące artykuły, aby uzyskać więcej informacji na temat wyjątków i obsługi wyjątków:

- [Używanie wyjątków](using-exceptions.md)
- [Obsługa wyjątków](exception-handling.md)
- [Tworzenie i zgłaszanie wyjątków](creating-and-throwing-exceptions.md)
- [Wyjątki generowane przez kompilator](compiler-generated-exceptions.md)
- [Jak obsługiwać wyjątek przy użyciu try/catch (Przewodnik programowania C#)](how-to-handle-an-exception-using-try-catch.md)
- [Wykonywanie czyszczenia kodu za pomocą instrukcji finally](how-to-execute-cleanup-code-using-finally.md)
- [Przechwytywanie wyjątku typu non-CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- <xref:System.SystemException>
- [Przewodnik programowania języka C#](../index.md)
- [Słowa kluczowe języka C#](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Wyjątki](../../../standard/exceptions/index.md)
