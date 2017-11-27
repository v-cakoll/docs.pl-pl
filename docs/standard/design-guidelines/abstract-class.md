---
title: Projekt klasy abstrakcyjnej
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d7b680c3377cbfa40734a57f9408d9487dbf3769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-class-design"></a>Projekt klasy abstrakcyjnej
**X nie** zdefiniuj public lub protected wewnętrzny konstruktorów w typach abstrakcyjnych.  
  
 Konstruktory powinny być publiczne, tylko wtedy, gdy użytkownicy będą musieli tworzyć wystąpienia typu. Ponieważ nie można utworzyć wystąpienia typu abstrakcyjnego, typ ogólny z publicznym konstruktorem jest niepoprawnie zaprojektowany i mylące dla użytkowników.  
  
 **CZY ✓** Definiowanie chronionych lub wewnętrzny konstruktora w klas abstrakcyjnych.  
  
 Konstruktor chroniony jest najczęściej i po prostu umożliwia klasy podstawowej w celu własną inicjowania podczas tworzenia podtypów.  
  
 Wewnętrzny Konstruktor może służyć do ograniczania konkretnych implementacji klasy abstrakcyjnej do zestawu Definiowanie klasy.  
  
 **CZY ✓** Podaj co najmniej jednego typu konkretnego, która dziedziczy po każdej klasy abstrakcyjnej, którą można wysłać.  
  
 Wykonywanie dzięki temu można sprawdzić poprawności projektu klasy abstrakcyjnej. Na przykład <xref:System.IO.FileStream?displayProperty=nameWithType> jest implementacją <xref:System.IO.Stream?displayProperty=nameWithType> klasy abstrakcyjnej.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania typu](../../../docs/standard/design-guidelines/type.md)  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)
