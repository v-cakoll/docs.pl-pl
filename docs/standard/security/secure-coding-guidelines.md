---
title: Bezpieczne wskazówki dotyczące kodowania dla programu .NET
description: Kod projektu do pracy z . Uprawnienia wymuszane przez sieć NET i inne wymuszanie w celu zapobiegania uzyskiwaniu dostępu do danych lub wykonywaniu innych działań przez złośliwy kod.
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187730"
---
# <a name="secure-coding-guidelines"></a>Bezpieczne wskazówki dotyczące kodowania

Zabezpieczenia zabezpieczeń opartych na dowodach i zabezpieczenia dostępu do kodu zapewniają bardzo zaawansowane, jawne mechanizmy implementowania zabezpieczeń. Większość kodu aplikacji można po prostu korzystać z infrastruktury zaimplementowanej przez .NET. W niektórych przypadkach wymagane są dodatkowe zabezpieczenia specyficzne dla aplikacji, zbudowane przez rozszerzenie systemu zabezpieczeń lub przy użyciu nowych metod ad hoc.

Za pomocą .NET wymuszane uprawnienia i inne wymuszanie w kodzie, należy wznieść bariery, aby zapobiec złośliwemu kodowi dostępu do informacji, które nie mają mieć lub wykonywania innych niepożądanych akcji. Ponadto należy zachować równowagę między zabezpieczeniami i użytecznością we wszystkich oczekiwanych scenariuszach przy użyciu zaufanego kodu.

W tym oznajmiającym różne sposoby projektowania kodu do pracy z systemem zabezpieczeń.

## <a name="securing-resource-access"></a>Zabezpieczanie dostępu do zasobów

Podczas projektowania i pisania kodu, należy chronić i ograniczyć dostęp, który kod ma do zasobów, szczególnie podczas używania lub wywoływania kodu nieznanego pochodzenia. Dlatego należy pamiętać o następujących technikach, aby upewnić się, że kod jest bezpieczny:

- Nie należy używać zabezpieczeń dostępu do kodu (CAS).

- Nie należy używać częściowego zaufanego kodu.

- Nie należy używać [atrybutu AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).

- Nie należy używać komunikacji zdalnej .NET.

- Nie należy używać modelu obiektów składników rozproszonych (DCOM).

- Nie należy używać formatters binarne.

Zabezpieczenia dostępu do kodu i kod przezroczysty zabezpieczeń nie są obsługiwane jako granica zabezpieczeń z częściowo zaufanym kodem. Odradzamy ładowanie i wykonywanie kodu z nieznanego źródła bez zapewnienia alternatywnych środków bezpieczeństwa. Alternatywne środki bezpieczeństwa to:

- Wirtualizacja

- Kontenery aplikacji

- Użytkownicy systemu operacyjnego (OS) i uprawnienia

- Pojemniki Hyper-V

## <a name="security-neutral-code"></a>Kod neutralny pod względem zabezpieczeń

Kod neutralny pod względem zabezpieczeń nie działa jawnie z systemem zabezpieczeń. Działa z dowolnych uprawnień, które otrzymuje. Chociaż aplikacje, które nie mogą przechwycić wyjątków zabezpieczeń skojarzonych z chronionymi operacjami (takimi jak używanie plików, sieci itd.) mogą spowodować nieobsługiwany wyjątek, kod neutralny pod względem zabezpieczeń nadal korzysta z technologii zabezpieczeń w platformie .NET .

Biblioteka neutralna pod względem zabezpieczeń ma specjalne cechy, które należy zrozumieć. Załóżmy, że biblioteka zawiera elementy interfejsu API, które używają plików lub wywołać kod niezarządzany. Jeśli kod nie ma odpowiednich uprawnień, nie będzie działać zgodnie z opisem. Jednak nawet jeśli kod ma uprawnienia, każdy kod aplikacji, który wywołuje go musi mieć takie samo uprawnienia, aby działać. Jeśli kod wywołujący nie ma odpowiednich <xref:System.Security.SecurityException> uprawnień, pojawia się w wyniku dostępu do kodu stosu zabezpieczeń walk.

## <a name="application-code-that-isnt-a-reusable-component"></a>Kod aplikacji, który nie jest składnikiem wielokrotnego użytku

Jeśli kod jest częścią aplikacji, która nie będzie wywoływana przez inny kod, zabezpieczenia jest proste i specjalne kodowanie może nie być wymagane. Należy jednak pamiętać, że złośliwy kod może wywołać kod. Zabezpieczenia dostępu do kodu mogą uniemożliwić złośliwemu kodowi dostęp do zasobów, ale taki kod może nadal odczytywać wartości pól lub właściwości, które mogą zawierać poufne informacje.

Ponadto jeśli kod akceptuje dane wejściowe użytkownika z Internetu lub innych niewiarygodnych źródeł, należy uważać na złośliwe dane wejściowe.

## <a name="managed-wrapper-to-native-code-implementation"></a>Otoka zarządzana do implementacji kodu macierzystego

Zazwyczaj w tym scenariuszu niektóre przydatne funkcje są implementowane w kodzie macierzystym, które chcesz udostępnić do kodu zarządzanego. Otoki zarządzane są łatwe do zapisu przy użyciu platformy wywołać lub COM interop. Jednak jeśli to zrobisz, obiekty wywołujące otoki musi mieć prawa do kodu niezarządzanego, aby odnieść sukces. W ramach zasad domyślnych oznacza to, że kod pobrany z intranetu lub Internetu nie będzie działać z otokami.

Zamiast nadawać niezarządzane prawa do kodu wszystkim aplikacjom, które używają tych otoki, lepiej nadać te prawa tylko kodowi otoki. Jeśli podstawowa funkcjonalność udostępnia żadnych zasobów i implementacji jest podobnie bezpieczne, otoki musi tylko dochodzić swoich praw, co umożliwia dowolnego kodu do wywołania za jego pośrednictwem. Gdy zasoby są zaangażowane, kodowanie zabezpieczeń powinny być takie same jak przypadek kodu biblioteki opisane w następnej sekcji. Ponieważ otoka jest potencjalnie narażając obiekty wywołujące do tych zasobów, staranna weryfikacja bezpieczeństwa kodu macierzystego jest konieczne i jest otoki odpowiedzialność.

## <a name="library-code-that-exposes-protected-resources"></a>Kod biblioteki, który udostępnia chronione zasoby

Następujące podejście jest najbardziej wydajne, a tym samym potencjalnie niebezpieczne (jeśli wykonane niepoprawnie) dla kodowania zabezpieczeń: biblioteka służy jako interfejs dla innego kodu, aby uzyskać dostęp do niektórych zasobów, które nie są dostępne w inny sposób, tak jak klasy .NET wymuszają uprawnień do zasobów, z których korzystają. Wszędzie tam, gdzie uwidaczniasz zasób, kod musi najpierw zażądać uprawnienia odpowiedniego do zasobu (to znaczy musi wykonać sprawdzenie zabezpieczeń), a następnie zazwyczaj dochodzić swoich praw do wykonywania rzeczywistej operacji.

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Zabezpieczanie danych o stanie](securing-state-data.md)|Opisuje sposób ochrony członków prywatnych.|
|[Zabezpieczenia i dane użytkownika](security-and-user-input.md)|W tym artykule opisano problemy z zabezpieczeniami aplikacji, które akceptują dane wejściowe użytkownika.|
|[Zabezpieczenia i sytuacja wyścigu](security-and-race-conditions.md)|Opisuje, jak uniknąć warunków wyścigu w kodzie.|
|[Zabezpieczenia i generowanie kodu na bieżąco](security-and-on-the-fly-code-generation.md)|W tym artykule opisano problemy z zabezpieczeniami aplikacji, które generują kod dynamiczny.|
|[Zabezpieczenia oparte na rolach](role-based-security.md)|W tym artykule oparto na rolie platformy .NET zabezpieczeń w szczegółach i zawiera instrukcje dotyczące używania go w kodzie.|
