---
title: Nazwy zestawów i bibliotek DLL
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], DLLs
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
- DLLs, names
ms.assetid: e800b610-31b4-4949-9c14-cb60e9f254be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97bd152cff53fb1c2edb107b6d6b34bd91ca1c49
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45613719"
---
# <a name="names-of-assemblies-and-dlls"></a>Nazwy zestawów i bibliotek DLL
Zestaw jest jednostką wdrożenia i tożsamości dla programów kodu zarządzanego. Mimo że zestawy może obejmować jeden lub więcej plików, zwykle zestawu mapuje jeden do jednego z biblioteką DLL. W związku z tym w tej sekcji opisano tylko DLL konwencje nazewnictwa, które następnie mogą zostać zmapowane do konwencji nazewnictwa zestawu.  
  
 **✓ DO** wybierz nazw dla Twojego zestawu bibliotek DLL, które sugeruje duże zestawy funkcji, takich jak dane systemowe.  
  
 Nazwy zestawów i biblioteki DLL nie muszą odpowiadać na nazwy przestrzeni nazw, ale jest postępuj zgodnie z nazwą przestrzeni nazw podczas nadawania nazw zestawów. Regułą jest nazwa biblioteki DLL, w oparciu o Wspólny prefiks przestrzeni nazw są zawarte w zestawie. Na przykład zestaw o dwie przestrzenie nazw, `MyCompany.MyTechnology.FirstFeature` i `MyCompany.MyTechnology.SecondFeature`, może być wywoływana `MyCompany.MyTechnology.dll`.  
  
 **✓ CONSIDER** nazewnictwa bibliotek DLL według następującego wzorca:  
  
 `<Company>.<Component>.dll`  
  
 gdzie `<Component>` zawiera jedną lub więcej klauzul oddzielone kropką. Na przykład:  
  
 `Litware.Controls.dll`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wskazówki dotyczące nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
