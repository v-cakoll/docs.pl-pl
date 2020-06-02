---
title: Projekt interfejsu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: f589d47d5b945179430275598996b2fb77e92848
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289034"
---
# <a name="interface-design"></a>Projekt interfejsu
Chociaż większość interfejsów API jest najlepszym modelem przy użyciu klas i struktur, istnieją przypadki, w których interfejsy są bardziej odpowiednie lub są jedyną opcją.

 Środowisko CLR nie obsługuje dziedziczenia wielokrotnego (tj. klasy CLR nie mogą dziedziczyć z więcej niż jednej klasy bazowej), ale w przypadku dziedziczenia z klasy bazowej są dozwolone typy implementujące jeden lub więcej interfejsów. W związku z tym interfejsy są często używane do osiągnięcia efektu wielokrotnego dziedziczenia. Na przykład <xref:System.IDisposable> jest interfejsem, który umożliwia obsługę typów disposability niezależnie od innych hierarchii dziedziczenia, w których chcą uczestniczyć.

 Inną sytuacją, w której jest właściwy Definiowanie interfejsu, jest utworzenie wspólnego interfejsu, który może być obsługiwany przez kilka typów, w tym niektóre typy wartości. Typy wartości nie mogą dziedziczyć po typach innych niż <xref:System.ValueType> , ale mogą implementować interfejsy, dlatego użycie interfejsu jest jedyną opcją w celu zapewnienia wspólnego typu podstawowego.

 ✔️ zdefiniować interfejs, jeśli potrzebujesz wspólnego interfejsu API, który ma być obsługiwany przez zestaw typów, które zawierają typy wartości.

 ✔️ ROZWAŻYĆ zdefiniowanie interfejsu, jeśli musisz obsługiwać jego funkcje na typach, które już dziedziczą z innego typu.

 ❌UNIKAj używania interfejsów znaczników (interfejsy bez elementów członkowskich).

 Jeśli konieczne jest oznaczenie klasy jako posiadającej konkretną charakterystykę (znacznik), w ogólności należy użyć atrybutu niestandardowego, a nie interfejsu.

 ✔️ zapewnić co najmniej jeden typ, który jest implementacją interfejsu.

 Dzięki temu można sprawdzić poprawność projektu interfejsu. Na przykład <xref:System.Collections.Generic.List%601> jest implementacją <xref:System.Collections.Generic.IList%601> interfejsu.

 ✔️ zapewnić co najmniej jeden interfejs API, który wykorzystuje każdy zdefiniowany przez siebie interfejs (metodę pobierającą interfejs jako parametr lub właściwość wpisaną jako interfejs).

 Dzięki temu można sprawdzić poprawność projektu interfejsu. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> korzysta z <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interfejsu.

 ❌NIE należy dodawać członków do interfejsu, który został wcześniej dostarczony.

 Wykonanie tej operacji spowodowałoby uszkodzenie implementacji interfejsu. Należy utworzyć nowy interfejs, aby uniknąć problemów z wersją.

 Z wyjątkiem przypadków opisanych w tych wytycznych, należy, ogólnie rzecz biorąc,, zamiast interfejsów projektowania bibliotek do wielokrotnego użytku.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania typów](type.md)
- [Wskazówki dotyczące projektowania struktury](index.md)
