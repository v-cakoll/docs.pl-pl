---
title: '{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}'
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: ff38cfdc228fd1eae1ace734ed2688c62c66499a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709559"
---
# <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}
<xref:System.Attribute?displayProperty=nameWithType> jest klasą bazową służącą do definiowania atrybutów niestandardowych.  
  
 Atrybuty są adnotacjami, które mogą być dodawane do elementów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry. Są one przechowywane w metadanych zestawu i dostępne w czasie wykonywania przy użyciu interfejsów API odbicia. Na przykład struktura definiuje <xref:System.ObsoleteAttribute>, które mogą być stosowane do typu lub elementu członkowskiego, aby wskazać, że typ lub element członkowski jest przestarzały.  
  
 Atrybuty mogą zawierać jedną lub więcej właściwości, które zawierają dodatkowe dane związane z atrybutem. Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji, w której typ lub element członkowski został uznany za przestarzały, a także opis nowych interfejsów API zastępujących przestarzały interfejs API.  
  
 Podczas stosowania atrybutu należy określić pewne właściwości atrybutu. Są one określane jako wymagane właściwości lub wymagane argumenty, ponieważ są reprezentowane jako parametry konstruktora pozycyjnyego. Na przykład właściwość <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.  
  
 Właściwości, które nie muszą być określone, gdy atrybut jest stosowany, nazywa się opcjonalnymi właściwościami (lub argumentami opcjonalnymi). Są one reprezentowane przez właściwości settable. Kompilatory zapewniają specjalną składnię do ustawiania tych właściwości podczas stosowania atrybutu. Na przykład właściwość <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> reprezentuje opcjonalny argument.  
  
 **✓ DO** nazwy klas atrybutów niestandardowych z sufiksem "Atrybutu".  
  
 **✓ DO** zastosować <xref:System.AttributeUsageAttribute> atrybutów niestandardowych.  
  
 **✓ DO** Podaj można ustawić właściwości dla argumentów opcjonalnych.  
  
 **✓ DO** Podaj właściwości tylko do pobrania dla wymaganych argumentów.  
  
 **✓ DO** podać parametry konstruktora zainicjować właściwości odpowiadającej wymaganych argumentów. Każdy parametr powinien mieć taką samą nazwę (choć z inną wielkością liter) jako odpowiednią właściwość.  
  
 **X AVOID** podając parametrami konstruktora zainicjować właściwości odpowiadającej Argumenty opcjonalne.  
  
 Innymi słowy, nie mają właściwości, które można ustawić przy użyciu zarówno konstruktora, jak i metody ustawiającej. Te wytyczne czynią bardzo jawne, które argumenty są opcjonalne i które są wymagane i nie mają dwóch sposobów na wykonanie tego samego działania.  
  
 **X AVOID** przeładowania konstruktorów atrybutu niestandardowego.  
  
 Posiadanie tylko jednego konstruktora jasno komunikuje się z użytkownikiem, które argumenty są wymagane i które są opcjonalne.  
  
 **✓ DO** zapieczętować klas atrybutów niestandardowych, jeśli to możliwe. Powoduje to szybsze wyszukiwanie atrybutu.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
