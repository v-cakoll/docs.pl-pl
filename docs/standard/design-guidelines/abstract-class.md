---
title: Projekt klasy abstrakcyjnej
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: e6a5923f293ed536fb272f6fe6c805067aede0ab
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280780"
---
# <a name="abstract-class-design"></a>Projekt klasy abstrakcyjnej

❌NIE należy definiować publicznych lub chronionych wewnętrznych konstruktorów w typach abstrakcyjnych.

 Konstruktory powinny być publiczne tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia typu. Ponieważ nie można tworzyć wystąpień typu abstrakcyjnego, typ abstrakcyjny z konstruktorem publicznym jest niepoprawnie zaprojektowany i mylący dla użytkowników.

 ✔️ zdefiniować chroniony lub wewnętrzny Konstruktor w klasach abstrakcyjnych.

 Chroniony Konstruktor jest bardziej powszechny, a po prostu pozwala klasie bazowej na wykonywanie własnej inicjalizacji podczas tworzenia podtypów.

 Wewnętrzny Konstruktor może służyć do ograniczania konkretnych implementacji klasy abstrakcyjnej do zestawu definiującego klasę.

 ✔️ zapewnić co najmniej jeden konkretny typ, który dziedziczy z każdej klasy abstrakcyjnej, którą dostarczasz.

 Dzięki temu można sprawdzić poprawność projektu klasy abstrakcyjnej. Na przykład, <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją <xref:System.IO.Stream?displayProperty=nameWithType> klasy abstrakcyjnej.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania typów](type.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
