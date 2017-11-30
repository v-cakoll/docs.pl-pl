---
title: "Pieczętowanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8caa253a3f17c58f542317de579c4f7832c4efac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sealing"></a>Pieczętowanie
Jedną z funkcji zorientowane obiektowo struktury jest deweloperzy może rozszerzyć i dostosować je w sposób nieprzewidziane przez projektantów framework. Jest to możliwości i zagrożenia extensible projektu. Podczas projektowania sieci framework, dlatego też jest bardzo ważne, dokładnie projektować pod kątem rozszerzalności, gdy wymagane jest i ograniczyć rozszerzalności, gdy jest niebezpieczne.  
  
 Pieczętowanie jest zaawansowanym mechanizmem, który uniemożliwia rozszerzalności. Można Zapieczętuj klasę lub poszczególne elementy. Klasa pieczętowania uniemożliwia użytkownikom dziedziczenia z klasy. Element członkowski pieczętowania uniemożliwia użytkownikom zastępowania określonego elementu członkowskiego.  
  
 **X nie** zapieczętować klasy bez konieczności powody, aby to zrobić.  
  
 Pieczętowania klasy, ponieważ nie można traktować scenariusza rozszerzalności nie jest dobrym przyczyny. Dziedziczenie z klasy z różnych powodów nonobvious, takich jak dodawanie członków wygody, takich jak użytkownicy Framework. Zobacz [niezapieczętowanych klas](../../../docs/standard/design-guidelines/unsealed-classes.md) przykłady nonobvious powodów użytkownik chce dziedziczyć po typie.  
  
 Powody do zamykania klasy są następujące:  
  
-   Klasa jest klasie statycznej. Zobacz [projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md).  
  
-   Klasa przechowuje klucze tajne istotnych dla zabezpieczeń w dziedziczonych chronionych elementów członkowskich.  
  
-   Klasa dziedziczy wiele wirtualnych elementów członkowskich i koszt pieczętowania je pojedynczo czy przeważają korzyści opuszczania klasy niezapieczętowane.  
  
-   Klasa jest atrybut, który wymaga środowiska uruchomieniowego bardzo szybko wyszukiwania. Atrybuty zapieczętowanego mają nieco wyższego poziomu wydajności niż niezapieczętowany z nich. Zobacz [atrybutów](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X nie** deklaruj chronionych i wirtualnych elementów członkowskich w typach zapieczętowanych.  
  
 Zgodnie z definicją typów zapieczętowanych nie może być dziedziczona z. To oznacza, że nie można wywołać chronionych elementów członkowskich w typach zapieczętowanych i wirtualnych metod w typach zapieczętowanych nie można zastąpić.  
  
 **ROZWAŻ ✓** pieczętowania elementów członkowskich, które można zastąpić.  
  
 Problemy, które mogą być wynikiem wprowadzenie wirtualnych elementów członkowskich (omówiona w [wirtualne elementy członkowskie](../../../docs/standard/design-guidelines/virtual-members.md)) dotyczą również zastąpienia chociaż nieco mniejszym stopniu. Pieczętowanie zastąpienia osłony można z tych problemów, począwszy od tego momentu w hierarchii dziedziczenia.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące projektowania Framework](../../../docs/standard/design-guidelines/index.md)  
 [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [Niezapieczętowanych klas](../../../docs/standard/design-guidelines/unsealed-classes.md)
