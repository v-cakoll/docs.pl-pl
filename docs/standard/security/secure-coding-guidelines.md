---
title: Wytyczne dotyczące bezpiecznego programowania dla platformy .NET
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b3a8f0dfc1a2b5e09722876b73281ed1d8b6334e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018648"
---
# <a name="secure-coding-guidelines"></a>Wytyczne dotyczące bezpiecznego programowania

Zabezpieczenia oparte na dowód i zabezpieczenia dostępu kodu zapewniają mechanizmy ogromne możliwości, jawnych, aby zaimplementować zabezpieczenia. Większość kodu aplikacji po prostu użyć infrastruktury implementowany przez platformy .NET. W niektórych przypadkach dodatkowe zabezpieczenia specyficzne dla aplikacji jest wymagany, utworzona przez rozszerzenie systemu zabezpieczeń lub za pomocą nowych metod ad-hoc.

Przy użyciu platformy .NET wymuszane, uprawnienia i innych wymuszania w kodzie, należy ustawienie bariery, aby zapobiec złośliwego kodu na dostęp do informacji, że użytkownik nie chce mieć lub wykonywania innych akcji niepożądane. Ponadto należy zachować równowagę pomiędzy zabezpieczeń i użyteczności, we wszystkich scenariuszach oczekiwanego przy użyciu zaufanego kodu.

W tym omówieniu opisano różne sposoby, w których kod może być przeznaczona do pracy z systemu zabezpieczeń.

## <a name="securing-resource-access"></a>Zabezpieczanie dostępu do zasobów

Podczas projektowania i tworzenia kodu, należy do ochrony i ograniczenie dostępu do zasobów, szczególnie w przypadku, gdy za pomocą lub wywoływania kodem nieznanego pochodzenia kodu. Dlatego należy przestrzegać następujących technik, aby upewnić się, że Twój kod jest bezpieczna:

- Nie należy używać zabezpieczeń dostępu kodu (CAS).

- Nie należy używać częściowej zaufanego kodu.

- Nie używaj [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) atrybutu (APTCA).

- Nie należy używać wywołaniem funkcji zdalnych .NET.

- Nie należy używać Distributed Component Object Model (DCOM).

- Nie należy używać binarne elementy formatujące.

Zabezpieczenia dostępu kodu ani kod o przezroczystym poziomie bezpieczeństwa, nie są obsługiwane jako granice zabezpieczeń z częściowo zaufanego kodu. Odradzamy ładowanie i wykonywanie kodu z nieznanego źródła bez zapewnienia alternatywnych środków bezpieczeństwa. Dostępne są następujące alternatywnych środków bezpieczeństwa:

- Wirtualizacja

- AppContainers

- Użytkownicy systemu operacyjnego (OS) i uprawnienia

- Kontenery funkcji Hyper-V

## <a name="security-neutral-code"></a>Kod o neutralnym poziomie bezpieczeństwa

Kod o neutralnym poziomie bezpieczeństwa nie działają, które są jawnie system zabezpieczeń. Była uruchamiana z uprawnieniami niezależnie od jej odbiera. Mimo że aplikacje, których nie można przechwytywać wyjątki zabezpieczeń skojarzone z operacjami chroniony (na przykład przy użyciu plików, sieci i tak dalej) może spowodować nieobsługiwany wyjątek, kod o neutralnym poziomie bezpieczeństwa nadal korzysta z technologii zabezpieczeń na platformie .NET .

Biblioteka neutralnym poziomie bezpieczeństwa ma specjalne właściwości, które należy zrozumieć. Załóżmy, że biblioteka zawiera elementy interfejsu API, które pliki lub wywoływać kod niezarządzany. Jeśli Twój kod nie ma odpowiednich uprawnień, nie będą uruchamiane, zgodnie z opisem. Jednak nawet wtedy, gdy kod ma uprawnienie, kod źródłowy aplikacji, który ją wywołuje musi mieć tego samego uprawnienia, aby móc pracować. Jeśli kod wywołujący nie ma odpowiednich uprawnień <xref:System.Security.SecurityException> pojawia się w wyniku przeszukiwania stosu zabezpieczeń dostępu kodu.

## <a name="application-code-that-isnt-a-reusable-component"></a>Kod aplikacji, które nie są komponentów wielokrotnego użytku

Jeśli Twój kod jest częścią aplikacji, która nie będzie można wywoływać za pomocą innego kodu, zabezpieczeń jest prosty i specjalnych kodowania, nie mogą być wymagane. Należy jednak pamiętać, że złośliwy kod może wywołać kodu. Gdy zabezpieczenia dostępu kodu może zatrzymać złośliwego kodu, uzyskiwanie dostępu do zasobów, taki kod nadal można odczytać wartości pola lub właściwości, które mogą zawierać poufne informacje.

Ponadto jeśli kod akceptuje dane wejściowe użytkownika z Internetu lub zawodnej źródeł, musi być ostrożność złośliwych danych.

## <a name="managed-wrapper-to-native-code-implementation"></a>Zarządzany otok dla implementacji kodu natywnego

Zwykle w tym scenariuszu niektóre przydatne jest implementowana w kodzie natywnym, który ma być dostępne dla kodu zarządzanego. Zarządzanych otok są łatwe do zapisu przy użyciu jednej z tych platform wywołania lub współdziałania z modelem COM. Jednak jeśli to zrobisz, wywołań usługi otoki musi mieć prawa kodu niezarządzanego, aby można było pomyślnie. W obszarze domyślne zasady oznacza to, że kod pobrany z sieci intranet lub Internetem nie będzie działać z otoki.

Zamiast kodu niezarządzanego prawa do wszystkich aplikacji, które używają tych otoki, lepiej jest udzielić tych uprawnień tylko do kodu otoki. Jeśli podstawową funkcjonalność ujawnia żadnych zasobów i wdrożenia podobnie jest bezpieczne, otoki musi tylko do potwierdzenia swoich praw umożliwiająca jakiegokolwiek kodu do wywołania przez nią. W przypadku zasobów kodowania zabezpieczeń powinna być taka sama w przypadku kodu biblioteki, które są opisane w następnej sekcji. Ponieważ otoki potencjalnie jest ujawniany przez obiekty wywołujące do tych zasobów, dokładnej weryfikacji bezpieczeństwa kodu natywnego jest konieczne i odpowiada za otoki.

## <a name="library-code-that-exposes-protected-resources"></a>Kod biblioteki udostępniający chronione zasoby

Następujące podejście jest najbardziej zaawansowane i dlatego potencjalnie niebezpiecznych (jeśli jest wykonywane niepoprawnie) zabezpieczeń kodowania: biblioteki służy jako interfejs dla innego kodu, dostęp do niektórych zasobów, które w przeciwnym razie są niedostępne, tak samo, jak wymusić klas platformy .NET uprawnienia do zasobów, których używają. Wszędzie tam, gdzie należy udostępnić zasób, kod musi najpierw wymagają uprawnień dla danego zasobu (czyli go wykonać sprawdzanie zabezpieczeń) i zazwyczaj potwierdzenia swoich praw do wykonania bieżącej operacji.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Zabezpieczanie danych o stanie](securing-state-data.md)|Opisuje sposób chronić prywatnych elementów członkowskich.|
|[Zabezpieczenia i dane użytkownika](security-and-user-input.md)|W tym artykule opisano problemy dotyczące zabezpieczeń dla aplikacji, które akceptują dane wejściowe użytkownika.|
|[Zabezpieczenia i sytuacja wyścigu](security-and-race-conditions.md)|Opisuje sposoby unikania wyścigu w kodzie.|
|[Zabezpieczenia i generowanie kodu na bieżąco](security-and-on-the-fly-code-generation.md)|W tym artykule opisano problemy dotyczące zabezpieczeń dla aplikacji, które generują kod dynamicznych.|
|[Zabezpieczenia oparte na rolach](role-based-security.md)|W tym artykule opisano zabezpieczenia oparte na roli platformy .NET szczegółowo i zawiera instrukcje dotyczące korzystania z niego w kodzie.|
