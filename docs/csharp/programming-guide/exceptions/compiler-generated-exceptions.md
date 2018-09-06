---
title: Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 476f5940b0b93d0c28bcd2bc9ca73147bc7bf3eb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43786008"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
Niektóre wyjątki są zgłaszane w automatycznie przez .NET Framework środowisko uruchomieniowe języka wspólnego (CLR), gdy podstawowe operacje kończą się niepowodzeniem. W poniższej tabeli wymieniono te wyjątki i ich warunków błędów.  
  
|Wyjątek|Opis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Klasa bazowa dla wyjątków, które występują podczas operacje arytmetyczne, takie jak <xref:System.DivideByZeroException> i <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Element zgłaszany, gdy tablica nie można zapisać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywisty typ tablicy.|  
|<xref:System.DivideByZeroException>|Element zgłaszany, gdy podejmowana jest próba dzielenia wartości całkowitej przez zero.|  
|<xref:System.IndexOutOfRangeException>|Element zgłaszany, gdy podejmowana jest próba indeksu tablicy, gdy indeks jest mniejsza od zera lub poza granice tablicy.|  
|<xref:System.InvalidCastException>|Element zgłaszany, gdy konwersja jawna z typu podstawowego interfejsu lub typu pochodnego nie powiedzie się w czasie wykonywania.|  
|<xref:System.NullReferenceException>|Zgłaszany, gdy użytkownik podejmie próbę odwołują się do obiektu, którego wartością jest [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Zgłaszany, gdy próba przydzielenia pamięci za pomocą [nowe](../../../csharp/language-reference/keywords/new-operator.md) operator nie powiedzie się. Oznacza to, dostępna dla środowiska uruchomieniowego języka wspólnego pamięci została wyczerpana.|  
|<xref:System.OverflowException>|Zgłaszany, gdy operacja arytmetyczna w `checked` przepełnienia kontekstu.|  
|<xref:System.StackOverflowException>|Zgłaszany, gdy stos wykonywania wyczerpaniu przez zbyt wiele wywołań metod oczekujące; Wskazuje zazwyczaj bardzo szczegółowe lub nieskończoną rekursję.|  
|<xref:System.TypeInitializationException>|Zgłaszany, gdy statyczny Konstruktor zgłasza wyjątek i zgodnego `catch` istnieje klauzuli catch go.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Wyjątki i obsługa wyjątków](../../../csharp/programming-guide/exceptions/index.md)  
- [Obsługa wyjątków](../../../csharp/programming-guide/exceptions/exception-handling.md)  
- [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
- [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
- [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)
