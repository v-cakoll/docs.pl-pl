---
title: Projekt interfejsu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c687d7622e82ee206b2201760818827398f8543b
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863725"
---
# <a name="interface-design"></a>Projekt interfejsu
Mimo że większość interfejsów API najlepiej są modelowane przy użyciu klas i struktur, istnieją przypadki, w których interfejsy są bardziej odpowiednie lub są jedynym rozwiązaniem.  
  
 Środowisko CLR nie obsługuje dziedziczenie wielokrotne (czyli klas CLR nie może dziedziczyć z więcej niż jednej klasy bazowej), ale zezwala na typy zaimplementować jeden lub więcej interfejsów oprócz dziedziczy z klasy bazowej. W związku z tym interfejsy są często używane, aby osiągnąć ten efekt wielokrotnego dziedziczenia. Na przykład <xref:System.IDisposable> jest interfejsem, który zezwala na typy do obsługi disposability niezależnie od innych hierarchii dziedziczenia, w którym chcesz uczestniczyć.  
  
 Sytuacja, w określeniu, które jest odpowiednie interfejs znajduje się w tworzenie wspólny interfejs, który może być obsługiwany przez kilka typów, w tym niektóre typy wartości. Typy wartości nie może dziedziczyć z typu innego niż <xref:System.ValueType>, ale mogące implementować interfejsy, za pomocą interfejsu jest jedyną opcją, aby zapewnić wspólny typ podstawowy.  
  
 **✓ DO** interfejs umożliwia określenie, czy należy niektórych typowych interfejsu API, obsługiwane przez zestaw typów, który zawiera typy wartości.  
  
 **✓ CONSIDER** Definiowanie interfejsu, jeśli zachodzi konieczność obsługi jej funkcji dla typów dziedziczących z innego typu.  
  
 **X AVOID** za pomocą znacznika interfejsów (interfejsy bez członków).  
  
 Jeśli potrzebujesz oznaczyć klasę jako posiadające szczególne cechy (znacznik), ogólnie rzecz biorąc, użyj atrybutu niestandardowego, a nie interfejsu.  
  
 **✓ DO** Podaj co najmniej jeden typ, który jest implementacją interfejsu.  
  
 Wykonując pozwala sprawdzić projekt interfejsu. Na przykład <xref:System.Collections.Generic.List%601> jest implementacją <xref:System.Collections.Generic.IList%601> interfejsu.  
  
 **✓ DO** Podaj co najmniej jeden interfejs API, który wykorzystuje każdego interfejsu należy zdefiniować (metody interfejsu jako parametr lub właściwość typu interfejsu).  
  
 Wykonując pozwala sprawdzić projekt interfejsu. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> zużywa <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfejsu.  
  
 **X DO NOT** dodawać członków do interfejsu, która została wcześniej dostarczona.  
  
 To spowoduje przerwanie implementacje interfejsu. Aby zapobiec problemom z wersjami, należy utworzyć nowy interfejs.  
  
 Z wyjątkiem sytuacji określonych w niniejszych wytycznych ogólnie rzecz biorąc, wybierz klasy, a nie interfejsy projektowanie biblioteki do ponownego wykorzystania kodu zarządzanego.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)  
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
