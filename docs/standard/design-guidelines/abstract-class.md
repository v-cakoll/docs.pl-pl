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
ms.openlocfilehash: 19482199648a8fb9c4b2c796fb1ab5d62c896abc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709598"
---
# <a name="abstract-class-design"></a>Projekt klasy abstrakcyjnej
**X DO NOT** zdefiniuj public lub protected wewnętrzny konstruktorów w typach abstrakcyjnych.  
  
 Konstruktory powinny być publiczne tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia typu. Ponieważ nie można tworzyć wystąpień typu abstrakcyjnego, typ abstrakcyjny z konstruktorem publicznym jest niepoprawnie zaprojektowany i mylący dla użytkowników.  
  
 **✓ DO** Definiowanie chronionych lub wewnętrzny konstruktora w klas abstrakcyjnych.  
  
 Chroniony Konstruktor jest bardziej powszechny, a po prostu pozwala klasie bazowej na wykonywanie własnej inicjalizacji podczas tworzenia podtypów.  
  
 Wewnętrzny Konstruktor może służyć do ograniczania konkretnych implementacji klasy abstrakcyjnej do zestawu definiującego klasę.  
  
 **✓ DO** Podaj co najmniej jednego typu konkretnego, która dziedziczy po każdej klasy abstrakcyjnej, którą można wysłać.  
  
 Dzięki temu można sprawdzić poprawność projektu klasy abstrakcyjnej. Na przykład <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją klasy abstrakcyjnej <xref:System.IO.Stream?displayProperty=nameWithType>.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
