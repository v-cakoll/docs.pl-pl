---
title: Pieczętowanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8c445de44a69f6c0cb1eaefa0e59d682288318
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336917"
---
# <a name="sealing"></a>Pieczętowanie
Jest jedną z funkcji struktury zorientowane obiektowo, deweloperzy mogą rozszerzać i dostosowywać je w sposób nieoczekiwany przez projektantów framework. Jest to, możliwości i zagrożenia extensible projektu. Podczas projektowania preferowanej struktury, dlatego też jest bardzo ważne, uważnie projektować pod kątem rozszerzalności, jeśli pożądane jest i ograniczyć rozszerzalności, gdy jest niebezpieczne.  
  
 Pieczętowanie jest zaawansowany mechanizm, który uniemożliwia rozszerzalności. Można Zapieczętuj klasę lub poszczególnych elementów członkowskich. Pieczętowanie klasę uniemożliwia użytkownikom dziedziczy z klasy. Pieczętowanie członka uniemożliwia użytkownikom zastępowanie określonego elementu członkowskiego.  
  
 **X DO NOT** zapieczętować klasy bez konieczności powody, aby to zrobić.  
  
 Pieczętowanie klasy, ponieważ nie można traktować scenariusza rozszerzalności nie jest dobrze przemyślane. Użytkownicy Framework, takich jak dziedziczyć z klas z różnych powodów nonobvious, takich jak dodawanie członków wygody. Zobacz [Niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md) przykładów dotyczących powodów nonobvious użytkownicy chcą dziedziczyć z typu.  
  
 Powody do zamykania klasy są następujące:  
  
-   Klasa jest klasą statyczną. Zobacz [projekt klasy statycznej](../../../docs/standard/design-guidelines/static-class.md).  
  
-   Klasa przechowuje wpisy tajne z istotnymi dla zabezpieczeń w elementy chronione dziedziczone.  
  
-   Klasa dziedziczy wielu wirtualnych elementów członkowskich, a koszt pieczętowania je pojedynczo może przeważyć zalety opuszczania klasy niezapieczętowane.  
  
-   Klasa jest atrybut, który wymaga bardzo szybkie środowiska uruchomieniowego wyszukiwania. Zapieczętowane atrybuty mają nieznacznie wyższe poziomy wydajności niż te niezapieczętowany. zobacz [atrybuty](../../../docs/standard/design-guidelines/attributes.md).  
  
 **X DO NOT** deklaruj chronionych i wirtualnych elementów członkowskich w typach zapieczętowanych.  
  
 Z definicji po typach zapieczętowanych nie można dziedziczyć z. Oznacza to, że chronionych elementów członkowskich w typach zapieczętowanych nie można wywołać metody, a wirtualne metody w typach zapieczętowanych nie można zastąpić.  
  
 **✓ CONSIDER** pieczętowania elementów członkowskich, które można zastąpić.  
  
 Problemy, które mogą wynikać z jej poziomu wprowadzać wirtualnych elementów członkowskich (omówionych w [wirtualnych elementów członkowskich](../../../docs/standard/design-guidelines/virtual-members.md)) dotyczą przesłonięć, mimo że trochę mniejszym stopniu. Pieczętowanie zastąpienia ochronnym możesz z tych problemów, począwszy od tego momentu w hierarchii dziedziczenia.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
- [Niezapieczętowane klasy](../../../docs/standard/design-guidelines/unsealed-classes.md)
