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
author: KrzysztofCwalina
ms.openlocfilehash: 16f2a095f461a406eedbd2b34b0c91d3ac43bbe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650105"
---
# <a name="type-design-guidelines"></a>Typy — zalecenia dotyczące projektowania
Z perspektywy CLR są tylko dwie kategorie typów — typy referencyjne i typy wartości — ale na potrzeby dyskusji na temat projektowania framework, możemy podzielić typy bardziej logiczne, grup, każda z regułach określonego projektu.  
  
 Klasy są generalnie w przypadku typów referencyjnych. Stanowią one większość typów w większości środowisk. Klasy zobowiązań ich popularność do zaawansowanych funkcji zorientowanych obiektowo, które obsługują zestaw i ich ogólnego zastosowania. Klas podstawowych i klasy abstrakcyjne są specjalne grupy logiczne, dotyczące rozszerzalności.  
  
 Interfejsy są typy, które może być implementowany przez typy odwołań i typy wartości. Ten sposób mogą one służyć jako elementy główne w hierarchii polimorficzne typy odwołań i typów wartości. Ponadto interfejsów może służyć do symulacji wielokrotnego dziedziczenia, która nie jest natywnie obsługiwane przez środowisko CLR.  
  
 Struktury są generalnie w przypadku typów wartości i powinna być zarezerwowana dla małych, prostych typów, podobne do elementów podstawowych języka.  
  
 Typy wyliczeniowe są w wyjątkowym przypadku okna typy wartości używane do definiowania krótkie zestawy wartości, takich jak dni tygodnia, kolory konsoli i tak dalej.  
  
 Klasy statyczne są typy, które mają być kontenery dla statycznych elementów członkowskich. Często służą one do zapewnienia skróty do innych operacji.  
  
 Delegatów, wyjątki, atrybuty, tablice i kolekcje są wszystkie przypadki specjalne typy odwołań, przeznaczone dla konkretnych zastosowań i wytyczne dotyczące ich projektów i użycia są omówione w innym miejscu w tym podręczniku.  
  
 **✓ DO** upewnij się, że każdy typ jest dobrze zdefiniowany zestaw elementów członkowskich powiązane, nie tylko losowe kolekcji funkcji niepowiązanych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wybieranie między klasą i strukturą](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [Projekt klasy abstrakcyjnej](../../../docs/standard/design-guidelines/abstract-class.md)  
 [Projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md)  
 [Projekt interfejsu](../../../docs/standard/design-guidelines/interface.md)  
 [Projekt struktury](../../../docs/standard/design-guidelines/struct.md)  
 [Projekt wyliczeń](../../../docs/standard/design-guidelines/enum.md)  
 [Zagnieżdżone typy](../../../docs/standard/design-guidelines/nested-types.md)  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
