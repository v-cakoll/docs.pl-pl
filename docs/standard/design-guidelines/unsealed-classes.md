---
title: Niezapieczętowane klasy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743554"
---
# <a name="unsealed-classes"></a>Niezapieczętowane klasy
Klasy zapieczętowane nie mogą być dziedziczone z i uniemożliwiają rozszerzanie. Z kolei klasy, które mogą być dziedziczone z, są nazywane niezapieczętowanymi klasami.

 ✔️ ROZWAŻYĆ użycie niezapieczętowanych klas bez dodanych wirtualnych lub chronionych elementów członkowskich jako doskonały sposób zapewnienia niedrogiej jeszcze bardziej łatwiejszej rozszerzalności na platformę.

 Deweloperzy często chcą dziedziczyć z niezapieczętowanych klas, aby dodać wygodną składową, taką jak konstruktory niestandardowe, nowe metody lub przeciążenia metod. Na przykład `System.Messaging.MessageQueue` jest niezapieczętowany i w ten sposób użytkownicy mogą tworzyć niestandardowe kolejki, które są domyślne dla określonej ścieżki kolejki lub dodać niestandardowe metody upraszczające interfejs API dla konkretnych scenariuszy.

 Klasy są domyślnie niezapieczętowane w większości języków programowania i jest to również zalecane domyślnie dla większości klas w strukturach. Rozszerzalność zapewniona przez niezapieczętowane typy jest znacznie doceniana przez użytkowników struktury i całkiem niedrogie, aby zapewnić z powodu stosunkowo niskich kosztów testów związanych z niezapieczętowanymi typami.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Projektowanie pod kątem rozszerzalności](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Pieczętowanie](../../../docs/standard/design-guidelines/sealing.md)
