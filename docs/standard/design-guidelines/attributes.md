---
title: Atrybuty
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: KrzysztofCwalina
ms.openlocfilehash: 6d4cc6615b7f7346e9c8fc2a7264025f318c8a3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698898"
---
# <a name="attributes"></a>Atrybuty
<xref:System.Attribute?displayProperty=nameWithType> Klasa bazowa służy do definiowania atrybutów niestandardowych.  
  
 Atrybuty są adnotacji, które mogą być dodawane do elementów programowania, takich jak zestawy, typy, elementy członkowskie i parametry. Są przechowywane w metadanych zestawu i można uzyskać dostęp w czasie wykonywania za pomocą odbicia interfejsów API. Na przykład definiuje platformę <xref:System.ObsoleteAttribute>, które można zastosować do typu lub elementu członkowskiego, aby wskazać, że typ lub składowa jest przestarzała.  
  
 Atrybuty mogą mieć jedną lub więcej właściwości, wykonujących dodatkowych danych powiązany z atrybutem. Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji, w którym typu lub elementu członkowskiego stało się przestarzałe i opis nowych interfejsów API, zastępując przestarzałych API.  
  
 Niektóre właściwości atrybutu musi być określona, jeśli ten atrybut jest stosowany. Są one określane jako wymagane właściwości lub wymagane argumenty, ponieważ są one reprezentowane jako parametry pozycyjne konstruktora. Na przykład <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> właściwość <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.  
  
 Właściwości, które nie muszą być określone, gdy ten atrybut jest stosowany noszą nazwę właściwości opcjonalnych (lub opcjonalne argumenty). Są one reprezentowane przez właściwości do ustawienia. Kompilatory zapewniają specjalnej składni, aby ustawić te właściwości, jeśli atrybut jest stosowany. Na przykład <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> właściwość reprezentuje opcjonalny argument.  
  
 **✓ DO** nazwy klas atrybutów niestandardowych z sufiksem "Atrybutu".  
  
 **✓ DO** zastosować <xref:System.AttributeUsageAttribute> atrybutów niestandardowych.  
  
 **✓ DO** Podaj można ustawić właściwości dla argumentów opcjonalnych.  
  
 **✓ DO** Podaj właściwości tylko do pobrania dla wymaganych argumentów.  
  
 **✓ DO** podać parametry konstruktora zainicjować właściwości odpowiadającej wymaganych argumentów. Każdy parametr powinien mieć taką samą nazwę (mimo że przy użyciu innej wielkości liter), jak odpowiadającą właściwość.  
  
 **X AVOID** podając parametrami konstruktora zainicjować właściwości odpowiadającej Argumenty opcjonalne.  
  
 Innymi słowy nie ma właściwości, które można ustawić za pomocą zarówno konstruktora, jak i metody ustawiającej. Ta wytyczna sprawia, że bardzo jawnych argumentów, które są opcjonalne i które są wymagane i pozwala uniknąć konieczności wykonując ten sam efekt na dwa sposoby.  
  
 **X AVOID** przeładowania konstruktorów atrybutu niestandardowego.  
  
 Wyraźnie posiadanie tylko jednego konstruktora komunikuje się użytkownik, który argumentów wymaganych i opcjonalnych.  
  
 **✓ DO** zapieczętować klas atrybutów niestandardowych, jeśli to możliwe. Dzięki temu szybsze wyszukiwania dla atrybutu.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
