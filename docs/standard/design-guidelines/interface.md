---
title: Projekt interfejsu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: KrzysztofCwalina
ms.openlocfilehash: 1f982aa37f92b7270725574d949989ca120297d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026370"
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
  
 *Przedrukowano za uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: Konwencje, Idiomy i wzorców dla wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams publikowane 22 Oct 2008 przez Addison Wesley Professional w ramach serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
