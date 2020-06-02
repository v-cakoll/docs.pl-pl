---
title: Projekt klasy statycznej
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: c906502ed071e8515f101996ec42a04772f72b12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291932"
---
# <a name="static-class-design"></a>Projekt klasy statycznej
Klasa statyczna jest definiowana jako Klasa, która zawiera tylko statyczne elementy członkowskie (oczywiście oprócz członków wystąpienia dziedziczonych z <xref:System.Object?displayProperty=nameWithType> i prawdopodobnie konstruktora prywatnego). Niektóre języki zapewniają wbudowaną obsługę klas statycznych. W języku C# 2,0 i nowszych, gdy Klasa jest zadeklarowana jako statyczna, jest zapieczętowana, abstrakcyjna i nie można zastąpić jej elementów członkowskich wystąpienia.

 Klasy statyczne są kompromisem między czystym i prostotą zorientowanym na obiektem. Są one często używane do udostępniania skrótów do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType> ), posiadaczy metod rozszerzających lub funkcji, dla których pełna otoka zorientowana obiektowo jest nieuzasadniona (na przykład <xref:System.Environment?displayProperty=nameWithType> ).

 ✔️ używać klas statycznych oszczędnie.

 Klasy statyczne powinny być używane tylko jako klasy pomocnicze dla rdzenia zorientowanego obiektowo struktury.

 ❌NIE Traktuj klas statycznych jako zasobników dodatkowych.

 ❌Nie deklaruj ani nie Przesłoń składowych wystąpienia w klasach statycznych.

 ✔️ NALEŻY zadeklarować klasy statyczne jako zapieczętowane, abstrakcyjne i dodać konstruktora wystąpienia prywatnego, jeśli język programowania nie ma wbudowanej obsługi dla klas statycznych.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania typów](type.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
