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
ms.openlocfilehash: 17bd300277a039818a3d563c8f2d5f99eb2fc68d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289567"
---
# <a name="type-design-guidelines"></a>Typy — zalecenia dotyczące projektowania
Z perspektywy środowiska CLR istnieją tylko dwie kategorie typów — typy referencyjne i typy wartości — ale na potrzeby dyskusji na temat projektu struktury dzielą typy na więcej grup logicznych, z których każda ma własne specyficzne reguły projektowania.

 Klasy są ogólną wielkością liter typów referencyjnych. Składają się na siebie zbiory typów w większości platform. Klasy są długoterminowe w rozbudowanym zestawie funkcji opartych na obiektach, które obsługują i do ich ogólnego zastosowania. Klasy bazowe i klasy abstrakcyjne są specjalnymi grupami logicznymi związanymi z rozszerzalnością.

 Interfejsy to typy, które mogą być implementowane przez oba typy odwołań i typy wartości. Mogą to być jako elementy główne hierarchii polimorficznych typów referencyjnych i typów wartości. Ponadto interfejsy mogą służyć do symulowania wielokrotnego dziedziczenia, które nie jest natywnie obsługiwane przez środowisko CLR.

 Struktury są ogólną wielkością liter typów wartości i powinny być zarezerwowane dla małych, prostych typów, podobnie jak w przypadku elementów podstawowych języka.

 Wyliczenia są szczególnym przypadkiem typów wartości używanych do definiowania krótkich zestawów wartości, takich jak dni tygodnia, kolory konsoli i tak dalej.

 Klasy statyczne są typami przeznaczonymi do kontenerów dla statycznych elementów członkowskich. Są one często używane do udostępniania skrótów do innych operacji.

 Delegaty, wyjątki, atrybuty, tablice i kolekcje są szczególnymi przypadkami typów referencyjnych, które są przeznaczone do określonych zastosowań, oraz wskazówki dotyczące ich projektowania i użycia zostały omówione w innym miejscu w tej książce.

 ✔️ Upewnij się, że każdy typ jest dobrze zdefiniowanym zestawem powiązanych członków, a nie tylko losową kolekcją niepowiązanych funkcji.

## <a name="in-this-section"></a>W tej sekcji
 [Wybór między klasą](choosing-between-class-and-struct.md) [abstrakcyjną](abstract-class.md) klasy a strukturą projektowanie klasy [statycznej](static-class.md) [Interface Design](interface.md) projekt struktura projektu [struktury](struct.md) projekt [Wyliczenie](enum.md) elementy [zagnieżdżone typy](nested-types.md) *części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
