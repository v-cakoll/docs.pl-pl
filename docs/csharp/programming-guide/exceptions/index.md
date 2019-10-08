---
title: Wyjątki i obsługa wyjątków — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 1442daf646a29c3822d06d0b649f462b37523fe2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002114"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)

Funkcje C# obsługi wyjątków języka ułatwiają postępowanie z wszelkimi nieoczekiwanymi lub wyjątkowymi sytuacjami, które występują, gdy program jest uruchomiony. Obsługa wyjątków używa słów kluczowych `try`, `catch` i `finally`, aby wypróbować akcje, które mogą się nie powieść, aby obsłużyć błędy w przypadku podjęcia decyzji o tym, że jest to uzasadnione, i w celu późniejszego oczyszczenia zasobów. Wyjątki mogą być generowane przez środowisko uruchomieniowe języka wspólnego (CLR) przez .NET Framework lub wszystkie biblioteki innych firm lub przez kod aplikacji. Wyjątki są tworzone za pomocą słowa kluczowego `throw`.

W wielu przypadkach wyjątek może zostać wygenerowany nie przez metodę, którą kod został wywołany bezpośrednio, ale przez inną metodę w stosie wywołań. Gdy tak się stanie, środowisko CLR spowoduje odwinięcie stosu, szukając metody z blokiem `catch` dla określonego typu wyjątku i wykona pierwszy taki blok `catch`, który zostanie znaleziony. Jeśli nie znajdzie odpowiedniego bloku `catch` w dowolnym miejscu w stosie wywołań, zakończy proces i wyświetli komunikat dla użytkownika.

W tym przykładzie metoda testów dla dzielenia przez zero i przechwytywania błędu. Bez obsługi wyjątków ten program zostanie przerwany z powodu **nieobsługiwanego błędu DivideByZeroException** .

[!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]

## <a name="exceptions-overview"></a>Przegląd wyjątków

Wyjątki mają następujące właściwości:  

- Wyjątki są typami, które ostatecznie pochodzą od `System.Exception`.
- Użyj bloku `try` wokół instrukcji, które mogą zgłaszać wyjątki.
- Gdy wystąpi wyjątek w bloku `try`, przepływ sterowania przechodzi do pierwszej powiązanej procedury obsługi wyjątku, która jest obecna w dowolnym miejscu w stosie wywołań. W C#, słowo kluczowe `catch` służy do definiowania programu obsługi wyjątków.
- Jeśli nie ma obsługi wyjątków dla danego wyjątku, program przestanie działać z komunikatem o błędzie.
- Nie należy przechwytywać wyjątku, chyba że można go obsłużyć i pozostawić aplikację w znanym stanie. Jeśli przechwytujesz `System.Exception`, ponownie zgłoś go przy użyciu słowa kluczowego `throw` na końcu bloku `catch`.
- Jeśli blok `catch` definiuje zmienną wyjątku, można jej użyć, aby uzyskać więcej informacji na temat typu wyjątku, który wystąpił.
- Wyjątki mogą być jawnie generowane przez program za pomocą słowa kluczowego `throw`.
- Obiekty wyjątków zawierają szczegółowe informacje o błędzie, takie jak stan stosu wywołań i opis tekstowy błędu.
- Kod w bloku `finally` jest wykonywany nawet wtedy, gdy zostanie zgłoszony wyjątek. Użyj bloku `finally` do zwolnienia zasobów, na przykład aby zamknąć wszystkie strumienie lub pliki, które zostały otwarte w bloku `try`.
- Wyjątki zarządzane w .NET Framework są implementowane na podstawie mechanizmu obsługi wyjątków strukturalnych Win32. Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków (C++C/)](/cpp/cpp/structured-exception-handling-c-cpp) i [kurs awarii na głębokości obsługi wyjątków strukturalnych Win32](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).

## <a name="related-sections"></a>Sekcje pokrewne

Więcej informacji o wyjątkach i obsłudze wyjątków można znaleźć w następujących artykułach:

- [Używanie wyjątków](using-exceptions.md)
- [Obsługa wyjątków](exception-handling.md)
- [Tworzenie i zgłaszanie wyjątków](creating-and-throwing-exceptions.md)
- [Wyjątki generowane przez kompilator](compiler-generated-exceptions.md)
- [Instrukcje: obsługa wyjątku za pomocą try/catch (C# Przewodnik programowania)](how-to-handle-an-exception-using-try-catch.md)
- [Instrukcje: wykonywanie czyszczenia kodu za pomocą instrukcji finally](how-to-execute-cleanup-code-using-finally.md)
- [Instrukcje: przechwytywanie wyjątku typu non-CLS](how-to-catch-a-non-cls-exception.md)

## <a name="c-language-specification"></a>Specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- <xref:System.SystemException>
- [Przewodnik programowania w języku C#](../index.md)
- [Słowa kluczowe języka C#](../../language-reference/keywords/index.md)
- [throw](../../language-reference/keywords/throw.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Wyjątki](../../../standard/exceptions/index.md)
