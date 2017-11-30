---
title: "Nazwy parametrów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b61f2b56b3b8bab67cec6db68a76916c6d7fa05a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="naming-parameters"></a>Nazwy parametrów
Poza oczywiste Przyczyna czytelności koniecznie postępuj zgodnie z wytycznymi dla nazw parametrów, ponieważ parametry są wyświetlane w dokumentacji i w projektancie, podając Intellisense i przeglądania funkcje klasy narzędzi do projektowania visual.  
  
 **CZY ✓** Użyj camelCasing w nazwach parametrów.  
  
 **CZY ✓** Użyj nazwy opisowej parametrów.  
  
 **ROZWAŻ ✓** przy użyciu nazwy parametru znaczenie niż typ parametru.  
  
### <a name="naming-operator-overload-parameters"></a>Nazwy parametrów przeciążenia operatora  
 **CZY ✓** użyj `left` i `right` dla nazw parametrów przeciążenia operatora binarnego Jeśli znaczenia parametrów nie istnieje.  
  
 **CZY ✓** użyj `value` dla Jednoargumentowy operator przeciążenia nazwy parametrów, jeśli żadnego znaczenia parametrów nie istnieje.  
  
 **ROZWAŻ ✓** łatwy do rozpoznania nazwy dla operatora przeciążenia parametrów, jeśli wykonanie tej tak dodaje wartość.  
  
 **X nie** Użyj skrótów lub wskaźniki liczbowe dla operatora przeciążenia nazwy parametrów.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Zasady nazewnictwa](../../../docs/standard/design-guidelines/naming-guidelines.md)
