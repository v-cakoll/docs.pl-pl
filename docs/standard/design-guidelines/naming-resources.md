---
title: Nazewnictwo zasobów
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: KrzysztofCwalina
ms.openlocfilehash: 5331c82069bb289c282e746841f5a328e2e628f2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130912"
---
# <a name="naming-resources"></a>Nazewnictwo zasobów
Ponieważ lokalizowalne zasoby mogą być przywoływane za pośrednictwem niektórych obiektów, tak jakby były one właściwości, wskazówkami nazewnictwa dla zasobów są podobne do wytycznych właściwości.  
  
 **✓ DO** programu PascalCasing klucze zasobów.  
  
 **✓ DO** Podaj opisową zamiast krótkich identyfikatorów.  
  
 **X DO NOT** użyj słowa kluczowe specyficzne dla języka głównego języków CLR.  
  
 **✓ DO** Użyj tylko znaki alfanumeryczne oraz znaki podkreślenia w nazw zasobów.  
  
 **✓ DO** używać następującej konwencji nazewnictwa dla zasobów komunikat wyjątku.  
  
 Identyfikator zasobu powinna być nazwa typu wyjątku oraz krótki identyfikator wyjątku:  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
