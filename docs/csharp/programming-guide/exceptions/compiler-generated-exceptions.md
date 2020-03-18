---
title: Wyjątki wygenerowane przez kompilator — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705317"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
Niektóre wyjątki są generowane automatycznie przez program runtime wspólnego języka .NET Framework (CLR), gdy podstawowe operacje nie powiodą się. Te wyjątki i ich warunki błędu są wymienione w poniższej tabeli.  
  
|Wyjątek|Opis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Klasa podstawowa dla wyjątków występujących podczas operacji <xref:System.DivideByZeroException> arytmetycznych, takich jak i <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Generowane, gdy tablica nie może przechowywać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywistym typem tablicy.|  
|<xref:System.DivideByZeroException>|Thrown, gdy podejmowano próbę podzielenia wartości integralnej przez zero.|  
|<xref:System.IndexOutOfRangeException>|Generowane podczas próby indeksowania tablicy, gdy indeks jest mniejszy niż zero lub poza granicami tablicy.|  
|<xref:System.InvalidCastException>|Generowane, gdy jawna konwersja z typu podstawowego do interfejsu lub typu pochodnego kończy się niepowodzeniem w czasie wykonywania.|  
|<xref:System.NullReferenceException>|Generowane, gdy podejmowano próbę odwołania się do obiektu, którego wartość jest [null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Generowane, gdy próba przydzielenia pamięci przy użyciu [nowego](../../language-reference/operators/new-operator.md) operatora nie powiedzie się. Oznacza to, że pamięć dostępna dla wspólnego języka w czasie wykonywania została wyczerpana.|  
|<xref:System.OverflowException>|Generowane, gdy operacja arytmetyczna w `checked` kontekście przepełnia.|  
|<xref:System.StackOverflowException>|Generowane, gdy stos wykonania jest wyczerpany przez zbyt wiele wywołań metody oczekujące; zazwyczaj wskazuje na bardzo głęboką lub nieskończoną rekursję.|  
|<xref:System.TypeInitializationException>|Generowane, gdy konstruktor statyczny `catch` zgłasza wyjątek i nie istnieje zgodna klauzula, aby go przechwycić.|  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
