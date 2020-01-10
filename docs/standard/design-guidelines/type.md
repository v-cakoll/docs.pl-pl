---
title: Typy — zalecenia dotyczące projektowania
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709026"
---
# <a name="type-design-guidelines"></a>Typy — zalecenia dotyczące projektowania
Z perspektywy środowiska CLR istnieją tylko dwie kategorie typów — typy referencyjne i typy wartości — ale na potrzeby dyskusji na temat projektu struktury dzielą typy na więcej grup logicznych, z których każda ma własne specyficzne reguły projektowania.  
  
 Klasy są ogólną wielkością liter typów referencyjnych. Składają się na siebie zbiory typów w większości platform. Klasy są długoterminowe w rozbudowanym zestawie funkcji opartych na obiektach, które obsługują i do ich ogólnego zastosowania. Klasy bazowe i klasy abstrakcyjne są specjalnymi grupami logicznymi związanymi z rozszerzalnością.  
  
 Interfejsy to typy, które mogą być implementowane przez oba typy odwołań i typy wartości. Mogą to być jako elementy główne hierarchii polimorficznych typów referencyjnych i typów wartości. Ponadto interfejsy mogą służyć do symulowania wielokrotnego dziedziczenia, które nie jest natywnie obsługiwane przez środowisko CLR.  
  
 Struktury są ogólną wielkością liter typów wartości i powinny być zarezerwowane dla małych, prostych typów, podobnie jak w przypadku elementów podstawowych języka.  
  
 Wyliczenia są szczególnym przypadkiem typów wartości używanych do definiowania krótkich zestawów wartości, takich jak dni tygodnia, kolory konsoli i tak dalej.  
  
 Klasy statyczne są typami przeznaczonymi do kontenerów dla statycznych elementów członkowskich. Są one często używane do udostępniania skrótów do innych operacji.  
  
 Delegaty, wyjątki, atrybuty, tablice i kolekcje są szczególnymi przypadkami typów referencyjnych, które są przeznaczone do określonych zastosowań, oraz wskazówki dotyczące ich projektowania i użycia zostały omówione w innym miejscu w tej książce.  
  
 **✓ DO** upewnij się, że każdy typ jest dobrze zdefiniowany zestaw elementów członkowskich powiązane, nie tylko losowe kolekcji funkcji niepowiązanych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie między klasą i strukturą](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Projekt klasy abstrakcyjnej](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md)  
 [Projekt interfejsu](../../../docs/standard/design-guidelines/interface.md)  
 [Projekt struktury](../../../docs/standard/design-guidelines/struct.md)  
 [Projekt wyliczeń](../../../docs/standard/design-guidelines/enum.md)  
 [Zagnieżdżone typy](../../../docs/standard/design-guidelines/nested-types.md)  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
