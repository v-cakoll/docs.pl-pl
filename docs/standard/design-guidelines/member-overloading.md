---
title: Przeciążenie elementu członkowskiego
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
ms.openlocfilehash: 2c77f08cd573dc40083718b783ae01233ca00766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573558"
---
# <a name="member-overloading"></a>Przeciążenie elementu członkowskiego
Przeciążenie elementu członkowskiego oznacza, że utworzenie dwóch lub więcej elementów członkowskich do tego samego typu, które różnią się jedynie liczby lub typów parametrów, ale mają taką samą nazwę. Na przykład w poniższych `WriteLine` metody jest przeciążona:  
  
```  
public static class Console {  
    public void WriteLine();  
    public void WriteLine(string value);  
    public void WriteLine(bool value);  
    ...  
}  
```  
  
 Ponieważ metody, konstruktorów i właściwości indeksowanych może mieć parametrów, tylko te elementy Członkowskie mogą być przeciążony.  
  
 Przeciążanie jest jednym z najważniejszych technik dla poprawy użyteczność, wydajności i czytelność biblioteki do ponownego użycia. Przeciążanie liczby parametrów umożliwia zapewnienie prostsze wersje konstruktory i metody. Przeciążanie na typ parametru umożliwia Użyj takiej samej nazwie elementu członkowskiego dla operacji identyczne na wybrany zestaw różnych typów elementów członkowskich.  
  
 **✓ DO** próby Użyj nazwy opisowej parametrów, aby wskazać, wartość domyślna używana przez krótszy przeciążenia.  
  
 **X AVOID** arbitralnie różne nazwy parametrów w przeciążenia. Jeśli parametr w przeciążeniami reprezentuje dane wejściowe tego samego jako parametru w innego przeciążenia, parametry muszą mieć taką samą nazwę.  
  
 **X AVOID** niespójne w kolejności parametrów w przeciążeniu elementy członkowskie. Parametry o takiej samej nazwie powinna pojawić się w tej samej pozycji w wszystkie przeciążenia.  
  
 **✓ DO** Tworzenie wirtualnego najdłuższym przeciążenia (Jeśli wymagane jest rozszerzalności). Przeciążenia krótszą po prostu powinny wywoływać za pomocą przeciążenia dłużej.  
  
 **X DO NOT** użyj `ref` lub `out` Modyfikatory do przeciążenia elementów członkowskich.  
  
 W przypadku niektórych języków nie można rozpoznać wywołania przeciążenia następująco. Ponadto takie przeciążenia zwykle ma semantykę różną całkowicie i prawdopodobnie nie powinien być przeciążenia, ale dwa oddzielne metody zamiast tego.  
  
 **X DO NOT** mają przeciążenia z parametrami w tej samej pozycji i podobnych typów jeszcze z różnych semantyki.  
  
 **✓ DO** Zezwalaj `null` do przekazania na argumenty opcjonalne.  
  
 **✓ DO** używać elementu członkowskiego przeładowanie, a nie Definiowanie elementów członkowskich z argumentami domyślnymi.  
  
 Argumenty domyślne nie są zgodne ze specyfikacją CLS.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
