---
title: Projekt klasy statyczne
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
ms.openlocfilehash: 92152600d317c04e3fef26400b11e94a549fde4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571062"
---
# <a name="static-class-design"></a>Projekt klasy statyczne
Klasa statyczna jest zdefiniowany jako klasa, która zawiera tylko elementy członkowskie static (oczywiście oprócz elementów członkowskich wystąpień odziedziczone <xref:System.Object?displayProperty=nameWithType> i prawdopodobnie Konstruktor prywatny). W przypadku niektórych języków zapewniają obsługę wbudowanych klas statycznych. W języku C# 2.0 lub nowszy po klasie został zadeklarowany jako statyczny, jest zapieczętowany, abstrakcyjny i żadnych członków wystąpienia można zastąpić lub zadeklarowana.  
  
 Klasy statyczne są kompromis między czystym obiektowego i prostota. Często są one używane do zapewnienia skróty do innych operacji (takich jak <xref:System.IO.File?displayProperty=nameWithType>), posiadaczy metody rozszerzenia lub funkcji, dla którego jest nieuzasadnione otoka pełnej zorientowane obiektowo (takie jak <xref:System.Environment?displayProperty=nameWithType>).  
  
 **✓ DO** oszczędnie używać klas statycznych.  
  
 Klasy statyczne należy używać tylko jako klasy pomocnicze dla core zorientowane obiektowo platformy.  
  
 **X DO NOT** Traktuj klas statycznych jako różne zasobnika.  
  
 **X DO NOT** zadeklarować lub zastąpienie elementów członkowskich wystąpienia w klasie statycznej.  
  
 **✓ DO** zadeklarować klas statycznych jako sealed, abstrakcyjny i dodać Konstruktor prywatny wystąpienia, jeśli język programowania nie ma wbudowaną obsługę klas statycznych.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
