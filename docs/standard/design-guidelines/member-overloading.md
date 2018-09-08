---
title: Przeciążanie elementu członkowskiego
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2127497d294cbfd4e1bb24d033f432378627ff13
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208234"
---
# <a name="member-overloading"></a>Przeciążanie elementu członkowskiego
Przeciążanie elementu członkowskiego oznacza, że tworzenie dwóch lub więcej elementów członkowskich do tego samego typu, które różnią się jedynie liczby lub typu parametrów, ale mają taką samą nazwę. Na przykład w następujących `WriteLine` jest przeciążona metoda:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Ponieważ metody, konstruktorów i właściwości indeksowanych może mieć parametrów, tylko te elementy Członkowskie mogą być przeciążone.  
  
 Przeciążenie jest jednym z najważniejszych technik dla poprawy użyteczność, produktywności i czytelności biblioteki do ponownego wykorzystania. Przeciążanie liczby parametrów umożliwia zapewnienie prostsze wersje konstruktorów i metod. Przeciążenie dla typu parametru umożliwia do korzystania z tej samej nazwy elementu członkowskiego dla elementów członkowskich, wykonywanie operacji identyczne na wybranym zestawem różnych typów.  
  
 **✓ DO** próby Użyj nazwy opisowej parametrów, aby wskazać, wartość domyślna używana przez krótszy przeciążenia.  
  
 **X AVOID** arbitralnie różne nazwy parametrów w przeciążenia. Jeśli parametr w kilkoma przeciążeniami przedstawia to samo wejście jako parametr w innego przeciążenia metody, parametry powinny mieć taką samą nazwę.  
  
 **X AVOID** niespójne w kolejności parametrów w przeciążeniu elementy członkowskie. Parametry o takiej samej nazwie powinna pojawić się w tej samej pozycji w wszystkie przeciążenia.  
  
 **✓ DO** Tworzenie wirtualnego najdłuższym przeciążenia (Jeśli wymagane jest rozszerzalności). Przeciążenia krótszy należy po prostu wykonywać wywołania za pośrednictwem dłużej przeciążenia.  
  
 **X DO NOT** użyj `ref` lub `out` Modyfikatory do przeciążenia elementów członkowskich.  
  
 W przypadku niektórych języków nie można rozpoznać wywołania przeciążenia następująco. Ponadto takimi przeciążeniami zazwyczaj mają całkowicie różną semantykę i prawdopodobnie nie powinny być przeciążenia, ale dwie odrębne metody zamiast tego.  
  
 **X DO NOT** mają przeciążenia z parametrami w tej samej pozycji i podobnych typów jeszcze z różnych semantyki.  
  
 **✓ DO** Zezwalaj `null` do przekazania na argumenty opcjonalne.  
  
 **✓ DO** używać elementu członkowskiego przeładowanie, a nie Definiowanie elementów członkowskich z argumentami domyślnymi.  
  
 Argumenty domyślne nie są zgodne ze specyfikacją CLS.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
