---
title: Projekt klasy abstrakcyjnej
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5b9dacc4995a126e1ee3f6062dca796194d4882
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128527"
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
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
