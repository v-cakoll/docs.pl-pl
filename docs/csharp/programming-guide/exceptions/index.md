---
title: Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
ms.openlocfilehash: 6cacf3cc613ffb23c6656d5d5718064a91b777a6
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "50744226"
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)
Obsługa funkcji pomocy wyjątków języka C# zajmuje nieoczekiwane lub wyjątkowych sytuacji, które występują, gdy program jest uruchomiony. Używa obsługi wyjątków `try`, `catch`, i `finally` słów kluczowych obsługi błędów w przypadku podjęcia decyzji, że jest uzasadnione, aby to zrobić, a potem wyczyścić zasoby, aby spróbować akcje, które mogą się nie powieść. Wyjątki mogą być generowane przez środowisko uruchomieniowe języka wspólnego (CLR) .NET Framework lub żadnych bibliotek innych firm lub przez kod aplikacji. Wyjątki są tworzone za pomocą `throw` — słowo kluczowe.  
  
 W wielu przypadkach wyjątek może zostać wygenerowany nie za pomocą metody, który wywołał kod bezpośrednio, ale przy użyciu innej metody w dalszej części stosu wywołań. W takiej sytuacji środowiska CLR będzie odkręcanie stosu, wyszukiwanie metody z `catch` blokowania dla typu określonego wyjątku który będzie wykonywał pierwszy takich `catch` blokowania, że jeśli znajdzie. W przypadku odnalezienia nie odpowiednie `catch` blokowania w dowolnym miejscu w stosie wywołań, będzie on zakończyć proces i wyświetlić komunikat dla użytkownika.  
  
 W tym przykładzie metoda sprawdza dzielenie przez zero i przechwytuje błędu. Bez obsługi wyjątków, ten program będzie kończyć się **dividebyzeroexception — został nieobsługiwany** błędu.  
  
 [!code-csharp[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Wyjątki — omówienie  
 Wyjątki mają następujące właściwości:  
  
-   Wyjątki są typy, które wszystkie ostatecznie pochodzą z `System.Exception`.  
  
-   Użyj `try` bloku wokół instrukcji, które może zgłaszać wyjątki.  
  
-   Gdy wystąpi wyjątek w `try` zablokować, przepływu sterowania przechodzi do pierwszego programu obsługi wyjątków skojarzone, który znajduje się w dowolnym miejscu w stosie wywołań. W języku C# `catch` — słowo kluczowe jest używane do definiowania obsługi wyjątków.  
  
-   Jeśli ma nie aparatu obsługi wyjątków dany wyjątek, program zatrzymuje wykonywanie komunikatu o błędzie.  
  
-   Nie przechwytuj wyjątek, chyba że można go obsłużyć i pozostawić ją w znanym stanie. Jeśli przechwytujesz `System.Exception`, zgłoś ponownie go za pomocą `throw` — słowo kluczowe na końcu `catch` bloku.  
  
-   Jeśli `catch` bloku definiuje zmienną wyjątek, służy do uzyskania dalszych informacji o typ wyjątku, który wystąpił.  
  
-   Wyjątki mogą jawnie generowane przez program przy użyciu `throw` — słowo kluczowe.  
  
-   Obiekty wyjątków zawierają szczegółowe informacje o błędzie, takie jak stan stos wywołań i tekst opisu błędu.  
  
-   Możesz pisać kod w `finally` blok jest wykonywany, nawet wtedy, gdy zostanie zgłoszony wyjątek. Użyj `finally` bloku, aby zwolnić zasoby, na przykład zamknąć wszystkie strumienie lub pliki, które zostały otwarte w `try` bloku.  
  
-   Zarządzane wyjątki w programie .NET Framework są wdrażane na podstawie mechanizm obsługi wyjątków strukturalnych Win32. Aby uzyskać więcej informacji, zobacz [obsługi wyjątków strukturalnych, (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) i [awarii kurs w głębi systemu Win32 ze strukturą wyjątków](https://bytepointer.com/resources/pietrek_crash_course_depths_of_win32_seh.htm).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Zobacz następujące tematy, aby uzyskać więcej informacji dotyczących wyjątków i wyjątków:  
  
-   [Używanie wyjątków](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Tworzenie i zgłaszanie wyjątków](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Wyjątki generowane przez kompilator](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Porady: obsługa wyjątków za pomocą bloku try/catch (C# Programming Guide)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Instrukcje: wykonywanie czyszczenia kodu za pomocą instrukcji finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [wyjątki](~/_csharplang/spec/exceptions.md) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.SystemException>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [throw](../../../csharp/language-reference/keywords/throw.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
- [Wyjątki](../../../standard/exceptions/index.md)  
