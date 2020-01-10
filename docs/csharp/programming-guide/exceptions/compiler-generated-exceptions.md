---
title: Wyjątki generowane przez kompilator — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
ms.openlocfilehash: 2a6b2c3fa053f1c555856df8098975340e78e2b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705317"
---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Wyjątki generowane przez kompilator (Przewodnik programowania w języku C#)
Niektóre wyjątki są generowane automatycznie przez środowisko uruchomieniowe języka wspólnego (CLR) .NET Framework, gdy podstawowe operacje kończą się niepowodzeniem. Te wyjątki i ich warunki błędu są wymienione w poniższej tabeli.  
  
|Wyjątek|Opis|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Klasa bazowa dla wyjątków, które występują podczas operacji arytmetycznych, takich jak <xref:System.DivideByZeroException> i <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Zgłaszany, gdy tablica nie może przechowywać danego elementu, ponieważ rzeczywisty typ elementu jest niezgodny z rzeczywistym typem tablicy.|  
|<xref:System.DivideByZeroException>|Zgłaszany, gdy podejmowana jest próba dzielenia wartości całkowitej przez zero.|  
|<xref:System.IndexOutOfRangeException>|Zgłaszany, gdy podejmowana jest próba indeksowania tablicy, gdy indeks jest mniejszy od zera lub poza granicami tablicy.|  
|<xref:System.InvalidCastException>|Zgłaszany, gdy jawna konwersja z typu podstawowego do interfejsu lub typu pochodnego kończy się niepowodzeniem w czasie wykonywania.|  
|<xref:System.NullReferenceException>|Zgłaszany, gdy podejmowana jest próba odwołująca się do obiektu, którego wartość jest [równa null](../../language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Zgłaszany, gdy próba przydzielenia pamięci przy użyciu operatora [New](../../language-reference/operators/new-operator.md) zakończy się niepowodzeniem. Oznacza to wyczerpanie pamięci dostępnej dla środowiska uruchomieniowego języka wspólnego.|  
|<xref:System.OverflowException>|Zgłaszany w przypadku przepełnienia operacji arytmetycznej w kontekście `checked`.|  
|<xref:System.StackOverflowException>|Zgłaszany, gdy stos wykonywania został wyczerpany przez zbyt wiele oczekujących wywołań metod; zwykle wskazuje bardzo głęboką lub nieskończoną rekursję.|  
|<xref:System.TypeInitializationException>|Zgłaszany, gdy Konstruktor statyczny zgłasza wyjątek i nie istnieje zgodna klauzula `catch`, aby go przechwycić.|  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Wyjątki i obsługa wyjątków](./index.md)
- [Obsługa wyjątków](./exception-handling.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
