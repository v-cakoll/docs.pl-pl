---
title: Projekt klasy statycznej
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261579"
---
# <a name="static-class-design"></a>Projekt klasy statycznej
Klasa statyczna jest zdefiniowany jako klasę, która zawiera tylko statyczne elementy członkowskie (oczywiście oprócz składowych wystąpienia dziedziczonych po elemencie <xref:System.Object?displayProperty=nameWithType> i prawdopodobnie Konstruktor prywatny). Niektóre języki zapewniają obsługę wbudowanych klas statycznych. W języku C# w wersji 2.0 i nowszych wersjach gdy klasa jest zadeklarowany jako statyczny, jest zapieczętowany, abstract, a nie składowych wystąpienia mogą zostać zastąpione lub zadeklarowana.  
  
 Klasy statyczne są kompromis między czystego programowania obiektowego i prostota. Często są one używane do zapewnienia skróty do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType>), posiadaczy metody rozszerzenia lub funkcji, dla którego jest nieuzasadnione otokę pełnej zorientowane obiektowo (takie jak <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** oszczędnie używać klas statycznych.  
  
 Klasy statyczne powinna służyć tylko jako klasy pomocnicze dla core zorientowane obiektowo Framework.  
  
 **X DO NOT** Traktuj klas statycznych jako różne zasobnika.  
  
 **X DO NOT** zadeklarować lub zastąpienie elementów członkowskich wystąpienia w klasie statycznej.  
  
 **✓ DO** zadeklarować klas statycznych jako sealed, abstrakcyjny i dodać Konstruktor prywatny wystąpienia, jeśli język programowania nie ma wbudowaną obsługę klas statycznych.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
