---
title: Atrybuty
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 3c0e1b8c20042c085d4ace996a084cbd464d3b21
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617564"
---
# <a name="attributes"></a>Atrybuty
<xref:System.Attribute?displayProperty=nameWithType>jest klasą bazową służącą do definiowania atrybutów niestandardowych.

 Atrybuty są adnotacjami, które mogą być dodawane do elementów programistycznych, takich jak zestawy, typy, elementy członkowskie i parametry. Są one przechowywane w metadanych zestawu i dostępne w czasie wykonywania przy użyciu interfejsów API odbicia. Na przykład struktura definiuje <xref:System.ObsoleteAttribute> , który można zastosować do typu lub elementu członkowskiego, aby wskazać, że typ lub element członkowski jest przestarzały.

 Atrybuty mogą zawierać jedną lub więcej właściwości, które zawierają dodatkowe dane związane z atrybutem. Na przykład `ObsoleteAttribute` może zawierać dodatkowe informacje o wersji, w której typ lub element członkowski został uznany za przestarzały, a także opis nowych interfejsów API zastępujących przestarzały interfejs API.

 Podczas stosowania atrybutu należy określić pewne właściwości atrybutu. Są one określane jako wymagane właściwości lub wymagane argumenty, ponieważ są reprezentowane jako parametry konstruktora pozycyjnyego. Na przykład <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> Właściwość <xref:System.Diagnostics.ConditionalAttribute> jest właściwością wymaganą.

 Właściwości, które nie muszą być określone, gdy atrybut jest stosowany, nazywa się opcjonalnymi właściwościami (lub argumentami opcjonalnymi). Są one reprezentowane przez właściwości settable. Kompilatory zapewniają specjalną składnię do ustawiania tych właściwości podczas stosowania atrybutu. Na przykład <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> Właściwość reprezentuje opcjonalny argument.

 ✔️ Nadaj nazwę klasom atrybutów niestandardowych z sufiksem "Attribute".

 ✔️ zastosować <xref:System.AttributeUsageAttribute> do atrybutów niestandardowych.

 ✔️ udostępniają właściwości settable dla opcjonalnych argumentów.

 ✔️ udostępniają właściwości tylko do pobrania dla wymaganych argumentów.

 ✔️ udostępniają parametry konstruktora, aby inicjować właściwości odpowiadające argumentom wymaganym. Każdy parametr powinien mieć taką samą nazwę (choć z inną wielkością liter) jako odpowiednią właściwość.

 ❌UNIKAj udostępniania parametrów konstruktora, aby inicjować właściwości odpowiadające argumentom opcjonalnym.

 Innymi słowy, nie mają właściwości, które można ustawić przy użyciu zarówno konstruktora, jak i metody ustawiającej. Te wytyczne czynią bardzo jawne, które argumenty są opcjonalne i które są wymagane i nie mają dwóch sposobów na wykonanie tego samego działania.

 ❌UNIKAj przeciążania konstruktorów atrybutów niestandardowych.

 Posiadanie tylko jednego konstruktora jasno komunikuje się z użytkownikiem, które argumenty są wymagane i które są opcjonalne.

 ✔️ należy zapieczętować klasy atrybutów niestandardowych, jeśli jest to możliwe. Powoduje to szybsze wyszukiwanie atrybutu.

 *Fragmenty &copy; 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące użycia](usage-guidelines.md)
