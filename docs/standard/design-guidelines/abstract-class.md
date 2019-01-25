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
author: KrzysztofCwalina
ms.openlocfilehash: 6eec3bb4575b89c6476e6c3410050c705141777f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550418"
---
# <a name="abstract-class-design"></a>Projekt klasy abstrakcyjnej
**X DO NOT** zdefiniuj public lub protected wewnętrzny konstruktorów w typach abstrakcyjnych.  
  
 Konstruktory powinny być publiczne, tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia tego typu. Ponieważ nie można utworzyć wystąpienia typu abstrakcyjnego, typ ogólny z publicznym konstruktorem jest niepoprawnie zaprojektowany i może być mylące dla użytkowników.  
  
 **✓ DO** Definiowanie chronionych lub wewnętrzny konstruktora w klas abstrakcyjnych.  
  
 Konstruktor chroniony jest częściej używana i po prostu umożliwia klasy bazowej o postępowaniu swój własny inicjowania podtypów są tworzone.  
  
 Konstruktor wewnętrznej może służyć do ograniczenia konkretnych implementacji klasy abstrakcyjnej do zestawu, Definiowanie klasy.  
  
 **✓ DO** Podaj co najmniej jednego typu konkretnego, która dziedziczy po każdej klasy abstrakcyjnej, którą można wysłać.  
  
 Wykonując pozwala sprawdzić projekt klasy abstrakcyjnej. Na przykład <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją <xref:System.IO.Stream?displayProperty=nameWithType> klasy abstrakcyjnej.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
