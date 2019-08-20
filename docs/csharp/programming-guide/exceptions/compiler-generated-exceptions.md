---
title: Wyjątki generowane przez kompilator — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: d0e0a304c8f7d77e7ba5c89b643fc5658c458558
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590369"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
Niektóre wyjątki są generowane automatycznie przez środowisko uruchomieniowe języka wspólnego (CLR) .NET Framework, gdy podstawowe operacje kończą się niepowodzeniem. Te wyjątki i ich warunki błędu są wymienione w poniższej tabeli.  
  
|Wyjątek|Opis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Klasa bazowa dla wyjątków, które występują podczas operacji arytmetycznych, takich <xref:System.DivideByZeroException> jak <xref:System.OverflowException>i.|  
|<xref:System.ArrayTypeMismatchException>|Zgłaszany, gdy tablica nie może przechowywać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywistym typem tablicy.|  
|<xref:System.DivideByZeroException>|Zgłaszany, gdy podejmowana jest próba dzielenia wartości całkowitej przez zero.|  
|<xref:System.IndexOutOfRangeException>|Zgłaszany, gdy podejmowana jest próba indeksowania tablicy, gdy indeks jest mniejszy od zera lub poza granicami tablicy.|  
|<xref:System.InvalidCastException>|Zgłaszany, gdy jawna konwersja z typu podstawowego do interfejsu lub typu pochodnego kończy się niepowodzeniem w czasie wykonywania.|  
|<xref:System.NullReferenceException>|Zgłaszany podczas próby odwołania się do obiektu, którego wartość jest [równa null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Zgłaszany, gdy próba przydzielenia pamięci przy użyciu operatora [New](../../language-reference/operators/new-operator.md) zakończy się niepowodzeniem. Oznacza to wyczerpanie pamięci dostępnej dla środowiska uruchomieniowego języka wspólnego.|  
|<xref:System.OverflowException>|Zgłaszane w przypadku przepełnienia operacji `checked` arytmetycznej w kontekście.|  
|<xref:System.StackOverflowException>|Zgłaszany, gdy stos wykonywania został wyczerpany przez zbyt wiele oczekujących wywołań metod; zwykle wskazuje bardzo głęboką lub nieskończoną rekursję.|  
|<xref:System.TypeInitializationException>|Zgłaszany, gdy Konstruktor statyczny zgłasza wyjątek i nie `catch` istnieje zgodna klauzula, aby ją przechwycić.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
