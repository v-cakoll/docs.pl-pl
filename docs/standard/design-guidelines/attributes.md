---
title: Attributes1
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 493ac709123c67311ba570894fb324ae7148bfae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="attributes"></a>Atrybuty
<xref:System.Attribute?displayProperty=nameWithType> Klasa podstawowa służy do definiowania atrybutów niestandardowych.  
  
 Atrybuty są adnotacje, które mogą być dodawane do elementów programowania, takich jak zestawy, typy elementów członkowskich i parametry. Są przechowywane w metadanych zestawu i jest dostępny w czasie wykonywania za pomocą odbicia interfejsów API. Na przykład platformę definiuje <xref:System.ObsoleteAttribute>, które można zastosować do typu lub elementu członkowskiego, aby wskazać, że typ lub element członkowski jest przestarzała.  
  
 Atrybuty mogą mieć co najmniej jednej właściwości zawierających dodatkowe dane powiązany z atrybutem. Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji w którym typ lub element członkowski został przestarzałe i opis nowych interfejsów API, zastępując przestarzałe interfejsu API.  
  
 Niektóre właściwości atrybutu należy określić, gdy jest stosowany atrybut. Te są określane jako wymagane właściwości lub liczbą wymaganych argumentów, ponieważ są one reprezentowane jako parametry pozycyjne konstruktora. Na przykład <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> właściwość <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.  
  
 Właściwości, które nie muszą być określone, gdy jest stosowany atrybut są nazywane właściwości opcjonalnych (lub argumentów opcjonalnych). Są one reprezentowane przez można ustawić właściwości. Kompilatory Podaj specjalnej składni ustawić te właściwości, gdy jest stosowany atrybut. Na przykład <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> właściwość reprezentuje opcjonalny argument.  
  
 **CZY ✓** nazwy klas atrybutów niestandardowych z sufiksem "Atrybutu".  
  
 **CZY ✓** zastosować <xref:System.AttributeUsageAttribute> atrybutów niestandardowych.  
  
 **CZY ✓** Podaj można ustawić właściwości dla argumentów opcjonalnych.  
  
 **CZY ✓** Podaj właściwości tylko do pobrania dla wymaganych argumentów.  
  
 **CZY ✓** podać parametry konstruktora zainicjować właściwości odpowiadającej wymaganych argumentów. Każdy parametr powinien mieć taką samą nazwę (mimo że za pomocą innej wielkości liter), jak odpowiadających im właściwości.  
  
 **X należy UNIKAĆ** podając parametrami konstruktora zainicjować właściwości odpowiadającej Argumenty opcjonalne.  
  
 Innymi słowy nie ma właściwości, które można ustawić za pomocą metody konstruktora, jak i ustawiającej. Niniejsze wytyczne sprawia, że bardzo jawne argumenty, które są opcjonalne i które są wymagane i pozwala uniknąć konieczności ten sam efekt na dwa sposoby.  
  
 **X należy UNIKAĆ** przeładowania konstruktorów atrybutu niestandardowego.  
  
 Wyraźnie mających tylko jeden konstruktor komunikuje się użytkownika, które argumentów wymaganych i opcjonalnych.  
  
 **CZY ✓** zapieczętować klas atrybutów niestandardowych, jeśli to możliwe. Dzięki temu można szybciej wyszukiwania dla atrybutu.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
