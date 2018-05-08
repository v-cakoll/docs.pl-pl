---
title: Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: a1746a492685cf25869bd06935bfd056de257fea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
Niektóre wyjątki zostaną zgłoszone automatycznie przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR), gdy podstawowe operacje nie powiedzie się. W poniższej tabeli wymieniono te wyjątki i ich warunki błędów.  
  
|Wyjątek|Opis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Klasa podstawowa dla wyjątków występujących podczas operacje arytmetyczne, takie jak <xref:System.DivideByZeroException> i <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Element zgłaszany, gdy tablicy nie może przechowywać danego elementu, ponieważ typ rzeczywistego elementu jest niezgodny z rzeczywisty typ tablicy.|  
|<xref:System.DivideByZeroException>|Element zgłaszany, gdy jest podejmowana próba wartością całkowitą dzielenia przez zero.|  
|<xref:System.IndexOutOfRangeException>|Element zgłaszany, gdy podejmowana jest próba do indeksu tablicy, gdy indeks jest mniejszy od zera lub poza granice tablicy.|  
|<xref:System.InvalidCastException>|Element zgłaszany, gdy jawna konwersja z typu podstawowego interfejsu lub typu pochodnego nie powiedzie się w czasie wykonywania.|  
|<xref:System.NullReferenceException>|Wyjątek podczas próby odwołuje się do obiektu, którego wartość jest [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Element zgłaszany, gdy próba przydzielenia pamięci przy użyciu [nowe](../../../csharp/language-reference/keywords/new-operator.md) operator nie powiedzie się. To ustawienie określa wyczerpaniu pamięci dostępnej dla środowiska CLR.|  
|<xref:System.OverflowException>|Element zgłaszany, gdy w operacji arytmetycznej `checked` przelewa kontekstu.|  
|<xref:System.StackOverflowException>|Element zgłaszany, gdy stos wykonywania wyczerpaniem przez zbyt wiele wywołań metody oczekujące; zwykle wskazuje bardzo bezpośrednich lub nieskończoną rekursję.|  
|<xref:System.TypeInitializationException>|Element zgłaszany, gdy Konstruktor statyczny zgłasza wyjątek i zgodnego `catch` istnieje klauzuli catch go.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
 [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
