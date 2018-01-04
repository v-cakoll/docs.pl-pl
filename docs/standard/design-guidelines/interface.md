---
title: Projekt interfejsu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc7185f9541952d528de38b627052239f5d8b4ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="interface-design"></a>Projekt interfejsu
Mimo że większość interfejsów API najlepiej są modelowane przy użyciu klas i struktur, istnieją przypadki, w których interfejsy są bardziej odpowiednie lub tylko opcja.  
  
 Środowisko CLR nie obsługuje dziedziczenie wielokrotne (tj. klasy CLR nie może dziedziczyć z więcej niż jedną klasę podstawową), ale możliwe typy zaimplementować jeden lub więcej interfejsów oprócz dziedziczenia z klasy podstawowej. W związku z tym interfejsy są często używane do uzyskania wpływu dziedziczenie wielokrotne. Na przykład <xref:System.IDisposable> jest interfejs, umożliwiający typy do obsługi disposability niezależnie od innych hierarchii dziedziczenia, w którym chcesz brać udział.  
  
 Sytuacja, w których definiowanie interfejsu jest jest przy tworzeniu wspólnego interfejsu, który może być obsługiwany przez kilka typów, w tym niektórych typów wartości. Typy wartości nie może dziedziczyć z typów innych niż <xref:System.ValueType>, ale miały zaimplementowane interfejsy, za pomocą interfejsu jest jedyną opcją w celu zapewnienia wspólnego typu podstawowego.  
  
 **CZY ✓** interfejs umożliwia określenie, czy należy niektórych typowych interfejsu API, obsługiwane przez zestaw typów, który zawiera typy wartości.  
  
 **ROZWAŻ ✓** Definiowanie interfejsu, jeśli zachodzi konieczność obsługi jej funkcji dla typów dziedziczących z innego typu.  
  
 **X należy UNIKAĆ** za pomocą znacznika interfejsów (interfejsy bez członków).  
  
 Jeśli potrzebujesz Oznacz klasę jako mający określonej właściwości (znacznik), ogólnie rzecz biorąc, użyj atrybutu niestandardowego zamiast interfejsu.  
  
 **CZY ✓** Podaj co najmniej jeden typ, który jest implementacją interfejsu.  
  
 Wykonywanie dzięki temu można sprawdzić poprawności projektu interfejsu. Na przykład <xref:System.Collections.Generic.List%601> jest implementacją <xref:System.Collections.Generic.IList%601> interfejsu.  
  
 **CZY ✓** Podaj co najmniej jeden interfejs API, który wykorzystuje każdego interfejsu należy zdefiniować (metody interfejsu jako parametr lub właściwość typu interfejsu).  
  
 Wykonywanie dzięki temu można sprawdzić poprawności projektu interfejsu. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> zużywa <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfejsu.  
  
 **X nie** dodawać członków do interfejsu, która została wcześniej dostarczona.  
  
 W ten sposób spowoduje przerwanie implementacji interfejsu. Aby uniknąć problemów z kontroli wersji, należy utworzyć nowy interfejs.  
  
 Z wyjątkiem sytuacji opisanych w poniższych wskazówek ogólnie rzecz biorąc, wybierz klasy, a nie interfejsy projektowanie biblioteki do ponownego użycia kodu zarządzanego.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
