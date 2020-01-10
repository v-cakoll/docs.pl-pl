---
title: Projekt interfejsu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 06b2e0d281314f3bd6346a7dbbd8bb56928fe58b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709299"
---
# <a name="interface-design"></a>Projekt interfejsu
Chociaż większość interfejsów API jest najlepszym modelem przy użyciu klas i struktur, istnieją przypadki, w których interfejsy są bardziej odpowiednie lub są jedyną opcją.  
  
 Środowisko CLR nie obsługuje dziedziczenia wielokrotnego (tj. klasy CLR nie mogą dziedziczyć z więcej niż jednej klasy bazowej), ale w przypadku dziedziczenia z klasy bazowej są dozwolone typy implementujące jeden lub więcej interfejsów. W związku z tym interfejsy są często używane do osiągnięcia efektu wielokrotnego dziedziczenia. Na przykład <xref:System.IDisposable> jest interfejsem, który pozwala na obsługę disposability niezależnie od innych hierarchii dziedziczenia, w których chcą uczestniczyć.  
  
 Inną sytuacją, w której jest właściwy Definiowanie interfejsu, jest utworzenie wspólnego interfejsu, który może być obsługiwany przez kilka typów, w tym niektóre typy wartości. Typy wartości nie mogą dziedziczyć po typach innych niż <xref:System.ValueType>, ale mogą implementować interfejsy, dlatego użycie interfejsu jest jedyną opcją w celu zapewnienia wspólnego typu podstawowego.  
  
 **✓ DO** interfejs umożliwia określenie, czy należy niektórych typowych interfejsu API, obsługiwane przez zestaw typów, który zawiera typy wartości.  
  
 **✓ CONSIDER** Definiowanie interfejsu, jeśli zachodzi konieczność obsługi jej funkcji dla typów dziedziczących z innego typu.  
  
 **X AVOID** za pomocą znacznika interfejsów (interfejsy bez członków).  
  
 Jeśli konieczne jest oznaczenie klasy jako posiadającej konkretną charakterystykę (znacznik), w ogólności należy użyć atrybutu niestandardowego, a nie interfejsu.  
  
 **✓ DO** Podaj co najmniej jeden typ, który jest implementacją interfejsu.  
  
 Dzięki temu można sprawdzić poprawność projektu interfejsu. Na przykład <xref:System.Collections.Generic.List%601> jest implementacją interfejsu <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** Podaj co najmniej jeden interfejs API, który wykorzystuje każdego interfejsu należy zdefiniować (metody interfejsu jako parametr lub właściwość typu interfejsu).  
  
 Dzięki temu można sprawdzić poprawność projektu interfejsu. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> zużywa interfejs <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.  
  
 **X DO NOT** dodawać członków do interfejsu, która została wcześniej dostarczona.  
  
 Wykonanie tej operacji spowodowałoby uszkodzenie implementacji interfejsu. Należy utworzyć nowy interfejs, aby uniknąć problemów z wersją.  
  
 Z wyjątkiem przypadków opisanych w tych wytycznych, należy, ogólnie rzecz biorąc,, zamiast interfejsów projektowania bibliotek do wielokrotnego użytku.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Typy — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/type.md)
- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
