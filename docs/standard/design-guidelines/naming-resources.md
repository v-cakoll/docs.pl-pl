---
title: "Nadawanie nazw zasobów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 89782b00799bfaac97780b0ffdee62c89fdfbe49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="naming-resources"></a>Nadawanie nazw zasobów
Ponieważ zlokalizowania zasobów można odwoływać się za pośrednictwem niektórych obiektów tak jakby były to właściwości, nazewnictwa wytyczne dotyczące zasobów są podobne do właściwości wytyczne.  
  
 **CZY ✓** programu PascalCasing klucze zasobów.  
  
 **CZY ✓** Podaj opisową zamiast krótkich identyfikatorów.  
  
 **X nie** użyj słowa kluczowe specyficzne dla języka głównego języków CLR.  
  
 **CZY ✓** Użyj tylko znaki alfanumeryczne oraz znaki podkreślenia w nazw zasobów.  
  
 **CZY ✓** używać następującej konwencji nazewnictwa dla zasobów komunikat wyjątku.  
  
 Identyfikator zasobu powinny być nazwa typu wyjątku plus krótki identyfikator wyjątku:  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Zasady nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
