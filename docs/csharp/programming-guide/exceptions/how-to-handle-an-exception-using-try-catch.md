---
title: 'Instrukcje: Obsługa wyjątków za pomocą bloku try-catch - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: db83eca52b204df1bb8273e94ae8664e61175aa7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244940"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Instrukcje: Obsługa wyjątków za pomocą bloku try/catch (C# Programming Guide)
Celem [try-catch —](../../../csharp/language-reference/keywords/try-catch.md) blok jest zdołały wychwycić i obsłużyć wyjątek, generowane przez działającego kodu. Niektóre wyjątki mogą być obsługiwane w `catch` bloku i problem rozwiązany bez wyjątku jest zgłoszony ponownie; jednak częściej jedyną czynnością, które można wykonać jest upewnij się, że zgłoszony odpowiedni wyjątek.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie <xref:System.IndexOutOfRangeException> nie jest najbardziej odpowiedni wyjątek: <xref:System.ArgumentOutOfRangeException> zapewnia bardziej zrozumiałe dla metody, ponieważ błąd jest spowodowany przez `index` argumentu przekazanego przez obiekt wywołujący.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Komentarze  
 Kod, który powoduje wyjątek jest ujęty w `try` bloku. A `catch` instrukcja dodaje się natychmiast po do obsługi `IndexOutOfRangeException`, jeśli występuje. `catch` Block uchwyty `IndexOutOfRangeException` i zgłasza bardziej odpowiednie `ArgumentOutOfRangeException` wyjątku zamiast tego. Aby można było podać obiekt wywołujący jak najwięcej informacji, jak to możliwe, należy wziąć pod uwagę oryginalnego wyjątku, ponieważ określenie <xref:System.Exception.InnerException%2A> nowego wyjątku. Ponieważ <xref:System.Exception.InnerException%2A> właściwość [tylko do odczytu](../../../csharp/language-reference/keywords/readonly.md), należy je przypisać w Konstruktorze nowy wyjątek.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
- [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)
