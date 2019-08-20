---
title: Wyjątki i obsługa wyjątków — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: c2b991a45a53ce4a8295d6181da11cb09fda6ddb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590193"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)
Funkcje C# obsługi wyjątków języka ułatwiają postępowanie z wszelkimi nieoczekiwanymi lub wyjątkowymi sytuacjami, które występują, gdy program jest uruchomiony. Obsługa wyjątków używa `try`słów kluczowych `catch`, i `finally` , aby wypróbować akcje, które mogą się nie powieść, aby obsłużyć błędy w przypadku podjęcia decyzji o tym, że jest to uzasadnione, a następnie w celu późniejszego oczyszczenia zasobów. Wyjątki mogą być generowane przez środowisko uruchomieniowe języka wspólnego (CLR) przez .NET Framework lub wszystkie biblioteki innych firm lub przez kod aplikacji. Wyjątki są tworzone za pomocą `throw` słowa kluczowego.  
  
 W wielu przypadkach wyjątek może zostać wygenerowany nie przez metodę, którą kod został wywołany bezpośrednio, ale przez inną metodę w stosie wywołań. W takim przypadku środowisko CLR spowoduje przewinięcie stosu, wyszukanie metody z `catch` blokiem dla określonego typu wyjątku i spowoduje wykonanie pierwszego takiego `catch` bloku, który w przypadku znalezienia. Jeśli nie znajdzie odpowiedniego `catch` bloku w dowolnym miejscu w stosie wywołań, zakończy proces i wyświetli komunikat dla użytkownika.  
  
 W tym przykładzie metoda testów dla dzielenia przez zero i przechwytywania błędu. Bez obsługi wyjątków ten program zostanie przerwany z powodu nieobsługiwanego błędu **DivideByZeroException** .  
  
 [!code-csharp[csProgGuideExceptions#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#18)]  
  
## <a name="exceptions-overview"></a>Przegląd wyjątków  
 Wyjątki mają następujące właściwości:  
  
- Wyjątki są typami, do `System.Exception`których wszystkie ostatecznie pochodzą.  
  
- `try` Użyj bloku wokół instrukcji, które mogą zgłaszać wyjątki.  
  
- Gdy w `try` bloku wystąpi wyjątek, przepływ sterowania przechodzi do pierwszej powiązanej procedury obsługi wyjątku, która jest obecna w dowolnym miejscu w stosie wywołań. W programie C#jest używane do definiowania programu obsługi wyjątków. `catch`  
  
- Jeśli nie ma obsługi wyjątków dla danego wyjątku, program przestanie działać z komunikatem o błędzie.  
  
- Nie należy przechwytywać wyjątku, chyba że można go obsłużyć i pozostawić aplikację w znanym stanie. Jeśli przechwytujesz `System.Exception`, ponownie zgłoś go `throw` przy użyciu słowa kluczowego `catch` na końcu bloku.  
  
- `catch` Jeśli blok definiuje zmienną wyjątku, można jej użyć, aby uzyskać więcej informacji na temat typu wyjątku, który wystąpił.  
  
- Wyjątki mogą być jawnie generowane przez program za pomocą `throw` słowa kluczowego.  
  
- Obiekty wyjątków zawierają szczegółowe informacje o błędzie, takie jak stan stosu wywołań i opis tekstowy błędu.  
  
- Kod w `finally` bloku jest wykonywany nawet wtedy, gdy zostanie zgłoszony wyjątek. Użyj bloku, aby zwolnić zasoby, na przykład aby zamknąć wszystkie strumienie lub pliki, które zostały otwarte `try` w bloku. `finally`  
  
- Wyjątki zarządzane w .NET Framework są implementowane na podstawie mechanizmu obsługi wyjątków strukturalnych Win32. Aby uzyskać więcej informacji, zobacz [strukturalna obsługa wyjątków (C++C/)](/cpp/cpp/structured-exception-handling-c-cpp) i [kurs awarii na głębokości obsługi wyjątków strukturalnych Win32](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Więcej informacji o wyjątkach i obsłudze wyjątków można znaleźć w następujących tematach:  
  
- [Używanie wyjątków](./using-exceptions.md)  
  
- [Obsługa wyjątków](./exception-handling.md)  
  
- [Tworzenie i zgłaszanie wyjątków](./creating-and-throwing-exceptions.md)  
  
- [Wyjątki generowane przez kompilator](./compiler-generated-exceptions.md)  
  
- [Instrukcje: Obsługuj wyjątek za pomocą try/catch (C# Przewodnik programowania)](./how-to-handle-an-exception-using-try-catch.md)  
  
- [Instrukcje: Wykonaj czyszczenie kodu przy użyciu instrukcji finally](./how-to-execute-cleanup-code-using-finally.md)  
  
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
