---
title: "Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#]
- exceptions [C#]
- C# language, exceptions
ms.assetid: 0001887f-4fa2-47e2-8034-2819477e2344
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 458f6770a89f28dce1e441cd38ec9a56a1c58bc1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exceptions-and-exception-handling-c-programming-guide"></a>Wyjątki i obsługa wyjątków (Przewodnik programowania w języku C#)
Obsługa funkcji pomocy wyjątków języka C# uwzględniać nieoczekiwany lub wyjątkowych sytuacji, które wystąpić, gdy program jest uruchomiony. Obsługa używa wyjątków `try`, `catch`, i `finally` słów kluczowych, aby spróbować akcje, które może się nie powieść, do obsługi błędów w przypadku podjęcia decyzji, czy jest uzasadnione, aby to zrobić, a także aby wyczyścić zasoby później. Wyjątki mogą być generowane przez środowisko uruchomieniowe języka wspólnego (CLR) programu .NET Framework lub żadnych bibliotek innej firmy lub przez kod aplikacji. Wyjątki są tworzone za pomocą `throw` — słowo kluczowe.  
  
 W wielu przypadkach wyjątek może zostać zgłoszony, nie za pomocą metody, która kodu została wywołana bezpośrednio, ale przy użyciu innej metody bardziej szczegółowo w dół w stosie wywołań. W takim przypadku CLR będzie unwind stosu, wyszukiwanie metodę o `catch` zablokować dla na określony typ wyjątku który zostanie wykonany pierwszy takie `catch` zablokować, jeśli znajduje. W przypadku odnalezienia nie odpowiednie `catch` bloków w dowolnym miejscu w stosie wywołań, spowoduje zakończenie procesu i wyświetlić wiadomość do użytkownika.  
  
 W tym przykładzie metoda testów dla dzielenia przez zero i przechwytuje błędu. Bez obsługi wyjątków, ten program będzie kończyć się **nieobsługiwany wyjątek dividebyzeroexception —** błędu.  
  
 [!code-csharp[csProgGuideExceptions#18](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exceptions-and-exception-handling_1.cs)]  
  
## <a name="exceptions-overview"></a>Omówienie wyjątków  
 Wyjątki mają następujące właściwości:  
  
-   Wyjątki są typów wyprowadzonych wszystkie ostatecznie z `System.Exception`.  
  
-   Użyj `try` bloku wokół instrukcji, które mogą zgłaszać wyjątków.  
  
-   Gdy wystąpi wyjątek w `try` zablokować przepływu sterowania przechodzi do pierwszego programu obsługi skojarzony wyjątek, który znajduje się w dowolnym miejscu w stosie wywołań. W języku C# `catch` — słowo kluczowe jest używane do definiowania obsługi wyjątków.  
  
-   Jeśli żaden moduł obsługi wyjątku dla danego wyjątku, program zatrzymuje wykonywanie komunikat o błędzie.  
  
-   Nie przechwytuj wyjątek, chyba że można go obsłużyć i pozostawić aplikacji w znanego stanu. Jeśli zostaną wychwycone `System.Exception`, za pomocą rethrow `throw` — słowo kluczowe na końcu `catch` bloku.  
  
-   Jeśli `catch` bloku definiuje zmienną wyjątek, można go uzyskać więcej informacji na temat typ wyjątku, który wystąpił.  
  
-   Wyjątki można jawnie wygenerowanych przez program przy użyciu `throw` — słowo kluczowe.  
  
-   Obiekty wyjątków zawiera szczegółowe informacje na temat tego błędu, takie jak stan stosu wywołań i opis błędu.  
  
-   Kod w `finally` blok jest wykonywana nawet wtedy, gdy jest zgłaszany wyjątek. Użyj `finally` bloku, aby zwolnić zasoby, na przykład zamknąć wszystkie strumienie lub pliki, które były otwarte w `try` bloku.  
  
-   Zarządzane wyjątki w programie .NET Framework są wdrażane na podstawie mechanizmu obsługi wyjątków strukturalnych Win32. Aby uzyskać więcej informacji, zobacz [strukturalnych obsługi wyjątków (C/C++)](/cpp/cpp/structured-exception-handling-c-cpp) i [A awarii kursu na głębokości systemu Win32 strukturalnych obsługi wyjątków](http://go.microsoft.com/fwlink/?LinkId=119654).  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Zobacz następujące tematy, aby uzyskać więcej informacji na temat wyjątki i obsługa wyjątków:  
  
-   [Używanie wyjątków](../../../csharp/programming-guide/exceptions/using-exceptions.md)  
  
-   [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)  
  
-   [Tworzenie i zgłaszanie wyjątków](../../../csharp/programming-guide/exceptions/creating-and-throwing-exceptions.md)  
  
-   [Wyjątki generowane przez kompilator](../../../csharp/programming-guide/exceptions/compiler-generated-exceptions.md)  
  
-   [Porady: obsługa wyjątków za pomocą bloku try/catch (C# przewodnik programowania w języku)](../../../csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch.md)  
  
-   [Porady: wykonywanie czyszczenia kodu za pomocą instrukcji finally](../../../csharp/programming-guide/exceptions/how-to-execute-cleanup-code-using-finally.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.SystemException>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [throw](../../../csharp/language-reference/keywords/throw.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [Wyjątki](../../../standard/exceptions/index.md)  
 [Hierarchia wyjątków](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [Pisanie kodu .NET niezawodnej](http://go.microsoft.com/fwlink/?LinkId=112400)  
 [Minizrzutów dla określonych wyjątków](http://go.microsoft.com/fwlink/?LinkId=112408)
