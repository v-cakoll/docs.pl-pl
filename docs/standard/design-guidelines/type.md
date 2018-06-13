---
title: Wytyczne dotyczące projektowania typu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af7511f4159fdbfe2d3f972dc927e9ee11fd586f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572892"
---
# <a name="type-design-guidelines"></a>Wytyczne dotyczące projektowania typu
Z punktu widzenia środowiska CLR, dostępne są tylko dwie kategorie typów — odwołanie typy i wartość — ale dyskusji dotyczących framework projektu na potrzeby możemy podział typy bardziej logiczne, grup, każda z własne zasady określonego projektu.  
  
 Klasy są generalnie w przypadku typów referencyjnych. Tworzą one zbiorczego rodzaje w większości platform. Klasy należnych firmie ich popularne zaawansowanej zestaw zorientowane obiektowo funkcje, których obsługują oraz ogólne możliwości ich zastosowania. Klasy podstawowe i klasy abstrakcyjne są specjalne logiczne grupy związane z rozszerzeń.  
  
 Interfejsy są typy, które może być zaimplementowany przez typy wartości i typy referencyjne. W związku z tym można służą jako katalogów głównych polimorficznych hierarchii typów referencyjnych i typów wartości. Ponadto interfejsy może służyć do symulowania dziedziczenie wielokrotne, który nie jest obsługiwany natywnie przez środowisko CLR.  
  
 Struktury są generalnie w przypadku typów wartości i powinna być zarezerwowana dla małych, prostych typów, podobnie jak w nim elementów podstawowych języka.  
  
 Typy wyliczeniowe są szczególnych przypadkach typów wartości używane do definiowania krótkie zestawy wartości, takich jak dni tygodnia, kolory konsoli i tak dalej.  
  
 Klasy statyczne są przeznaczone do kontenerów dla statycznych elementów członkowskich typów. Często są używane do zapewnienia skróty do innych operacji.  
  
 Delegatów, wyjątki atrybuty, tablic i kolekcje są wszystkie szczególnych przypadkach typy referencyjne przeznaczonych do określonych celów i wskazówki dotyczące ich projektowania i użycia w innym miejscu, omówiono w książce.  
  
 **CZY ✓** upewnij się, że każdy typ jest dobrze zdefiniowany zestaw elementów członkowskich powiązane, nie tylko losowe kolekcji funkcji niepowiązanych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie między klasą i strukturą](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Projekt klasy abstrakcyjnej](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md)  
 [Projekt interfejsu](../../../docs/standard/design-guidelines/interface.md)  
 [Projekt struktury](../../../docs/standard/design-guidelines/struct.md)  
 [Projekt wyliczeń](../../../docs/standard/design-guidelines/enum.md)  
 [Zagnieżdżone typy](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
