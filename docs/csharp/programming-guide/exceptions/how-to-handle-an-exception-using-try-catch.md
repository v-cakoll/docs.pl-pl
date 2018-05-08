---
title: 'Porady: obsługa wyjątków za pomocą bloku try-catch (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: b67a3d7b6d2e10519363a273b7dd1d8b61317d1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Porady: obsługa wyjątków za pomocą bloku try/catch (Przewodnik programowania w języku C#)
Celem [try-catch](../../../csharp/language-reference/keywords/try-catch.md) blok jest zdołały wychwycić i obsłużyć wyjątek, generowane przez kod pracy. Niektóre wyjątki mogą być obsługiwane w `catch` blok i ten problem można rozwiązać bez wyjątek zostanie zgłoszony ponownie, jednak częściej jedyną operacją, które można wykonać upewnij się, że odpowiednie wyjątku.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.IndexOutOfRangeException> nie jest najbardziej odpowiednia wyjątek: <xref:System.ArgumentOutOfRangeException> przesyła bardziej zrozumiałe dla metody, ponieważ błąd jest spowodowany przez `index` argument przekazany przez wywołującego.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Komentarze  
 Kod, który powoduje zgłoszenie wyjątku jest ujęta w `try` bloku. A `catch` instrukcji dodawany jest od razu po do obsługi `IndexOutOfRangeException`, jeśli występuje. `catch` Zablokować uchwytów `IndexOutOfRangeException` i zgłasza wyjątek, bardziej odpowiednie `ArgumentOutOfRangeException` wyjątek zamiast tego. Aby zapewnić wywołującego tylu informacji jak to możliwe, należy rozważyć określenie pierwotny wyjątek jako <xref:System.Exception.InnerException%2A> nowe wyjątku. Ponieważ <xref:System.Exception.InnerException%2A> właściwość jest [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md), należy go przypisać w Konstruktorze nowego wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
 [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)
