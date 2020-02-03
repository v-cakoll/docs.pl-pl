---
title: Atrybuty
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: c7bbbda88bd2fddb235b9ae639848e08a452c913
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741787"
---
# <a name="attributes"></a>Atrybuty
<xref:System.Attribute?displayProperty=nameWithType> jest klasą bazową służącą do definiowania atrybutów niestandardowych.

 Atrybuty są adnotacjami, które mogą być dodawane do elementów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry. Są one przechowywane w metadanych zestawu i dostępne w czasie wykonywania przy użyciu interfejsów API odbicia. Na przykład struktura definiuje <xref:System.ObsoleteAttribute>, które mogą być stosowane do typu lub elementu członkowskiego, aby wskazać, że typ lub element członkowski jest przestarzały.

 Atrybuty mogą zawierać jedną lub więcej właściwości, które zawierają dodatkowe dane związane z atrybutem. Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji, w której typ lub element członkowski został uznany za przestarzały, a także opis nowych interfejsów API zastępujących przestarzały interfejs API.

 Podczas stosowania atrybutu należy określić pewne właściwości atrybutu. Są one określane jako wymagane właściwości lub wymagane argumenty, ponieważ są reprezentowane jako parametry konstruktora pozycyjnyego. Na przykład właściwość <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.

 Właściwości, które nie muszą być określone, gdy atrybut jest stosowany, nazywa się opcjonalnymi właściwościami (lub argumentami opcjonalnymi). Są one reprezentowane przez właściwości settable. Kompilatory zapewniają specjalną składnię do ustawiania tych właściwości podczas stosowania atrybutu. Na przykład właściwość <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> reprezentuje opcjonalny argument.

 ✔️ Nadaj nazwę klasom atrybutów niestandardowych z sufiksem "Attribute".

 ✔️ zastosować <xref:System.AttributeUsageAttribute> do atrybutów niestandardowych.

 ✔️ udostępniają właściwości settable dla opcjonalnych argumentów.

 ✔️ udostępniają właściwości tylko do pobrania dla wymaganych argumentów.

 ✔️ udostępniają parametry konstruktora, aby inicjować właściwości odpowiadające argumentom wymaganym. Każdy parametr powinien mieć taką samą nazwę (choć z inną wielkością liter) jako odpowiednią właściwość.

 ❌ unikać udostępniania parametrów konstruktora, aby inicjować właściwości odpowiadające argumentom opcjonalnym.

 Innymi słowy, nie mają właściwości, które można ustawić przy użyciu zarówno konstruktora, jak i metody ustawiającej. Te wytyczne czynią bardzo jawne, które argumenty są opcjonalne i które są wymagane i nie mają dwóch sposobów na wykonanie tego samego działania.

 ❌ uniknąć przeładowania konstruktorów atrybutów niestandardowych.

 Posiadanie tylko jednego konstruktora jasno komunikuje się z użytkownikiem, które argumenty są wymagane i które są opcjonalne.

 ✔️ należy zapieczętować klasy atrybutów niestandardowych, jeśli jest to możliwe. Powoduje to szybsze wyszukiwanie atrybutu.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
