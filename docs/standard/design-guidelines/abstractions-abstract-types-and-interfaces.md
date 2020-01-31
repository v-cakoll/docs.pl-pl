---
title: Abstrakcje (typy abstrakcyjne i interfejsy)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 6a4f511af72aad916d367153090504e2a8e11cb8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741810"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrakcje (typy abstrakcyjne i interfejsy)
Streszczenie to typ, który opisuje kontrakt, ale nie zapewnia pełnej implementacji kontraktu. Streszczenia są zwykle implementowane jako klasy abstrakcyjne lub interfejsy i są one ze dobrze zdefiniowanym zestawem dokumentacji referencyjnej opisującym wymaganą semantykę typów implementujących kontrakt. Niektóre z najważniejszych streszczeń w .NET Framework obejmują <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>i <xref:System.Object>.

 Struktury można rozciągnąć przez implementację konkretnego typu, który obsługuje umowę abstrakcji i używa tego konkretnego typu z interfejsami API platformy, które używają (działającego na) abstrakcji.

 Zrozumiałe i przydatne streszczenie, które jest w stanie przetrzymywać testy czasu, są bardzo trudne do zaprojektowania. Głównym trudnością jest uzyskanie właściwego zestawu elementów członkowskich, nie więcej i mniej. Jeśli streszczenie ma zbyt wiele elementów członkowskich, stanie się trudne lub nawet niemożliwe do zaimplementowania. Jeśli ma za mało elementów członkowskich dla pozostałej funkcjonalności, będzie bezużyteczny w wielu interesujących scenariuszach.

 Zbyt wiele abstrakcji w strukturze również negatywnie wpływa na użyteczność struktury. Często trudno jest zrozumieć abstrakcję bez zrozumienia, jak pasuje do większego obrazu konkretnych implementacji i interfejsów API działających na potrzeby abstrakcji. Ponadto nazwy abstrakcji i ich składowe są niekoniecznie abstrakcyjne, co często sprawia, że są one tajemnicze i nieodpowiednie, bez uprzedniego poznania szerszego kontekstu ich użycia.

 Jednakże abstrakcje zapewniają wyjątkowo zaawansowane rozszerzalność, która nie jest często zgodna z innymi mechanizmami rozszerzalności. Są one podstawą wielu wzorców architektonicznych, takich jak wtyczki, niewersja kontroli (IoC), potoki itd. Są one również niezwykle ważne do testowania struktur. Dobre abstrakcje sprawiają, że istnieje możliwość wypróbowania dużych zależności na potrzeby testowania jednostkowego. Podsumowując, abstrakcje są odpowiedzialne za pomyślne zamiar — po rozbudowaniu nowoczesnych platform zorientowanych obiektowo.

 ❌ nie zapewniają abstrakcji, chyba że są testowane przez opracowywanie kilku konkretnych implementacji i interfejsów API korzystających z abstrakcji.

 ✔️ NALEŻY uważnie wybierać między klasą abstrakcyjną i interfejsem podczas projektowania abstrakcji.

 ✔️ ROZWAŻYĆ dostarczenie testów referencyjnych dla konkretnych implementacji abstrakcji. Takie testy powinny pozwolić użytkownikom na przetestowanie, czy ich implementacje prawidłowo implementują kontrakt.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
