---
title: Pieczętowanie
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: a54c68efb4ac114fe0e5a5712eca877bef35c103
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290113"
---
# <a name="sealing"></a>Pieczętowanie
Jedną z funkcji platform zorientowanych na obiektach jest to, że deweloperzy mogą je rozwijać i dostosowywać w sposób nieoczekiwany przez projektantów struktury. Jest to zarówno moc, jak i niebezpieczeństwo rozszerzalnego projektu. Podczas projektowania platformy, dlatego bardzo ważne jest staranne projektowanie pod kątem rozszerzalności, gdy jest to potrzebne, i ograniczanie rozszerzalności, gdy jest to niebezpieczne.

 Zaawansowany mechanizm, który uniemożliwia rozszerzanie rozszerzalności. Możesz zapieczętować klasę lub poszczególnych członków. Opieczętowanie klasy uniemożliwia użytkownikom dziedziczenie z klasy. Zapieczętowania elementu członkowskiego uniemożliwia użytkownikom zastępowanie określonego elementu członkowskiego.

 ❌NIE należy zapieczętować klas bez dobrego powodu.

 Pieczętowanie klasy, ponieważ nie można myśleć, że scenariusz rozszerzalności nie jest dobrym powodem. Użytkownicy platformy, którzy mają dziedziczyć z klas z różnych nieoczywistych powodów, takich jak dodawanie wygodnych członków. Zobacz [niezapieczętowane klasy](unsealed-classes.md) , aby poznać przykłady nieoczywistych przyczyn, które użytkownicy chcą dziedziczyć z typu.

 Dobrym przyczynami zapieczętowania klasy są następujące:

- Klasa jest klasą statyczną. Zobacz [projekt klasy statycznej](static-class.md).

- Klasa przechowuje wpisy tajne z uwzględnieniem zabezpieczeń w dziedziczonych chronionych składowych.

- Klasa dziedziczy wiele wirtualnych elementów członkowskich, a koszt ich pieczętowania jest większa niż korzyści wynikające z pozostawienia niezapieczętowanej klasy.

- Klasa jest atrybutem, który wymaga bardzo szybkiego wyszukiwania w środowisku uruchomieniowym. Zapieczętowane atrybuty mają nieco wyższy poziom wydajności niż niezapieczętowany. Zobacz [atrybuty](attributes.md).

 ❌Nie deklaruj chronionych ani wirtualnych elementów członkowskich w typach zapieczętowanych.

 Z definicji typy zapieczętowane nie mogą być dziedziczone z. Oznacza to, że nie można wywoływać chronionych elementów członkowskich w typach zapieczętowanych, a metody wirtualne w typach zapieczętowanych nie mogą zostać zastąpione.

 ✔️ ROZWAŻYĆ zastępowanie zastąpień elementów członkowskich.

 Problemy, które mogą skutkować wprowadzeniem wirtualnych elementów członkowskich (omówione w [wirtualnych elementach członkowskich](virtual-members.md)), są również stosowane do zastąpień, chociaż mają nieco mniejszy stopień. Nałożenie przesłonięcia osłony przed tymi problemami rozpoczyna się od tego momentu w hierarchii dziedziczenia.

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Projektowanie pod kątem rozszerzalności](designing-for-extensibility.md)
- [Niezapieczętowane klasy](unsealed-classes.md)
