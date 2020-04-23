---
title: Zagadnienia dotyczące zabezpieczeń XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071690"
---
# <a name="xaml-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń XAML

W tym artykule opisano najlepsze rozwiązania dotyczące zabezpieczeń w aplikacjach podczas korzystania z interfejsu API usług XAML i .NET XAML.

## <a name="untrusted-xaml-in-applications"></a>Niezaufany kod XAML w aplikacjach

W najbardziej ogólnym znaczeniu niezaufany kod XAML jest dowolnym źródłem XAML, którego aplikacja nie zawierała specjalnie ani nie emitowała.

XAML, który jest kompilowany `resx`do lub przechowywane jako zasób typu typu w zaufanym i podpisanym zestawie nie jest z natury niezaufane. Można ufać XAML tak samo, jak ufasz zestawowi jako całości. W większości przypadków dotyczy to tylko aspektów zaufania luźnego kodu XAML, który jest źródłem XAML, które można załadować ze strumienia lub innych we/wy. Luźny kod XAML nie jest określonym składnikiem ani funkcją modelu aplikacji z infrastrukturą wdrażania i pakowania. Jednak zestaw może implementować zachowanie, które polega na załadowaniu luźne XAML.

W przypadku niezaufanego kodu XAML należy traktować go ogólnie tak samo, jak gdyby był niezaufanym kodem. Użyj piaskownicy lub innych metafor, aby uniemożliwić potencjalnie niezaufanym kodom XAML dostęp do zaufanego kodu.

Charakter możliwości XAML daje XAML prawo do konstruowania obiektów i ustawić ich właściwości. Te możliwości obejmują również uzyskiwanie dostępu do konwerterów typów, mapowanie i `x:Code` uzyskiwanie dostępu do zestawów w domenie aplikacji, przy użyciu rozszerzeń znaczników, bloków i tak dalej.

Oprócz możliwości na poziomie języka XAML jest używany do definicji interfejsu użytkownika w wielu technologiach. Ładowanie niezaufanego kodu XAML może oznaczać załadowanie złośliwego interfejsu użytkownika fałszowania.

## <a name="sharing-context-between-readers-and-writers"></a>Udostępnianie kontekstu między czytelnikami i pisarzami

Architektura usług .NET XAML services dla czytników XAML i modułów zapisu XAML często wymaga udostępniania czytnika XAML modułowi zapisującego XAML lub udostępnionego kontekstu schematu XAML. Udostępnianie obiektów lub kontekstów może być wymagane, jeśli piszesz logikę pętli węzła XAML lub udostępniasz niestandardową ścieżkę zapisu. Nie udostępniaj wystąpień czytnika XAML, kontekstu schematu XAML niedefault ani ustawień dla klas czytnika/modułu zapisującego XAML między zaufanym i niezaufanym kodem.

Większość scenariuszy i operacji obejmujących zapisywanie obiektów XAML dla kopii zapasowej typu opartego na programie CLR można po prostu użyć domyślnego kontekstu schematu XAML. Domyślny kontekst schematu XAML nie zawiera jawnie ustawień, które mogłyby naruszyć pełne zaufanie. Dlatego bezpiecznie jest udostępniać kontekst między zaufanymi i niezaufanymi składnikami czytnika/modułu zapisującego XAML. Jednak jeśli to zrobisz, nadal jest najlepszym rozwiązaniem, aby zachować takich czytelników i pisarzy w oddzielnych <xref:System.AppDomain> zakresach, z jednym z nich specjalnie przeznaczone/piaskownicy dla częściowego zaufania.

## <a name="xaml-namespaces-and-assembly-trust"></a>Przestrzenie nazw xaml i zaufanie do zestawu

Podstawowa niewykwalifikowanych składni i definicja sposobu, w jaki XAML interpretuje niestandardowe mapowanie przestrzeni nazw XAML do zestawu, nie rozróżnia zestawu zaufanego i niezaufanego jako załadowanego do domeny aplikacji. W związku z tym jest technicznie możliwe dla niezaufanego zestawu do fałszowania zaufanego zestawu zamierzonego mapowania przestrzeni nazw XAML i przechwytywania źródła XAML zadeklarowanych informacji o obiekcie i właściwości. Jeśli masz wymagania dotyczące zabezpieczeń, aby uniknąć tej sytuacji, zamierzone mapowanie obszaru nazw XAML powinno być wykonane przy użyciu jednej z następujących technik:

- Użyj w pełni kwalifikowanej nazwy zestawu o silnej nazwie w dowolnym mapowaniu przestrzeni nazw XAML wykonanego przez xaml aplikacji.

- Ogranicz mapowanie zestawu do stałego zestawu zestawów odwołań, konstruując określone <xref:System.Xaml.XamlSchemaContext> dla czytników XAML i modułów zapisujących obiekt XAML. Zobacz: <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.

## <a name="xaml-type-mapping-and-type-system-access"></a>Mapowanie typu XAML i dostęp do systemu typu

XAML obsługuje swój własny system typów, który pod wieloma względami jest równorzędnym sposobem implementowania podstawowego systemu typu CLR. Jednak w przypadku niektórych aspektów świadomości typu, w którym podejmujesz decyzje dotyczące zaufania dotyczące typu na podstawie informacji o typie, należy odroczyć informacje o typie w typach kopii CLR. Dzieje się tak, ponieważ niektóre z określonych możliwości raportowania systemu typu XAML pozostają otwarte jako metody wirtualne i dlatego nie są w pełni pod kontrolą oryginalnych implementacji usług .NET XAML Services. Te punkty rozszerzalności istnieją, ponieważ system typu XAML jest rozszerzalny, aby dopasować rozszerzalność samego XAML i jego możliwych alternatywnych strategii mapowania typów w porównaniu z domyślną implementacją wspieraną przez program CLR i domyślnym kontekstem schematu XAML. Aby uzyskać więcej informacji, zobacz szczegółowe uwagi <xref:System.Xaml.XamlType> na <xref:System.Xaml.XamlMember>temat kilku właściwości i .

## <a name="see-also"></a>Zobacz też

- <xref:System.Xaml.Permissions.XamlAccessLevel>
