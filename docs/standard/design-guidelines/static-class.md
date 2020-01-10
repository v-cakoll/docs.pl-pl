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
ms.openlocfilehash: 35bcf1d403c78cdfcbb476b2eb5de2251a564b9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709065"
---
# <a name="static-class-design"></a>Projekt klasy statycznej
Klasa statyczna jest definiowana jako Klasa, która zawiera tylko statyczne elementy członkowskie (oczywiście oprócz członków wystąpienia dziedziczonych z <xref:System.Object?displayProperty=nameWithType> i ewentualnie konstruktora prywatnego). Niektóre języki zapewniają wbudowaną obsługę klas statycznych. W C# 2,0 i nowszych, gdy Klasa jest zadeklarowana jako statyczna, jest zapieczętowana, abstrakcyjna i nie można zastępować ani deklarować elementów członkowskich wystąpienia.  
  
 Klasy statyczne są kompromisem między czystym i prostotą zorientowanym na obiektem. Są one często używane do udostępniania skrótów do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType>), posiadaczy metod rozszerzających lub funkcji, dla których pełna otoka zorientowana obiektowo jest nieuzasadniona (na przykład <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** oszczędnie używać klas statycznych.  
  
 Klasy statyczne powinny być używane tylko jako klasy pomocnicze dla rdzenia zorientowanego obiektowo struktury.  
  
 **X DO NOT** Traktuj klas statycznych jako różne zasobnika.  
  
 **X DO NOT** zadeklarować lub zastąpienie elementów członkowskich wystąpienia w klasie statycznej.  
  
 **✓ DO** zadeklarować klas statycznych jako sealed, abstrakcyjny i dodać Konstruktor prywatny wystąpienia, jeśli język programowania nie ma wbudowaną obsługę klas statycznych.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
