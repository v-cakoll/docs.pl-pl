---
title: Wytyczne dotyczące bezpiecznego kodowania dla platformy .NET
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
ms.openlocfilehash: 51f835803cc545e2a9982c1c8a90d0c998c2bcb8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705915"
---
# <a name="secure-coding-guidelines"></a>Wytyczne dotyczące bezpiecznego kodowania

Zabezpieczenia oparte na potwierdzaniu i dostęp do kodu zapewniają bardzo zaawansowane, jawne mechanizmy implementowania zabezpieczeń. Większość kodu aplikacji może po prostu użyć infrastruktury zaimplementowanej przez platformę .NET. W niektórych przypadkach wymagane są dodatkowe zabezpieczenia specyficzne dla aplikacji, które zostały utworzone przez rozszerzenie systemu zabezpieczeń lub za pomocą nowych metod ad hoc.

Korzystając z wymuszanych przez platformę .NET uprawnień i innych wymuszania w kodzie, należy wzniesione przeszkody uniemożliwiające złośliwemu kodowi uzyskanie dostępu do informacji, które nie powinny mieć ani wykonywać innych niepożądanych akcji. Ponadto należy uzyskać równowagę między bezpieczeństwem i użytecznością we wszystkich oczekiwanych scenariuszach przy użyciu zaufanego kodu.

W tym omówieniu opisano różne sposoby, w których kod może być przeznaczony do pracy z systemem zabezpieczeń.

## <a name="securing-resource-access"></a>Zabezpieczanie dostępu do zasobów

Podczas projektowania i pisania kodu, należy chronić i ograniczyć dostęp do tego kodu do zasobów, szczególnie w przypadku używania lub wywoływania kodu nieznanego źródła. Należy więc pamiętać o następujących technikach, aby upewnić się, że kod jest bezpieczny:

- Nie używaj zabezpieczeń dostępu kodu (CAS).

- Nie używaj częściowo zaufanego kodu.

- Nie należy używać atrybutu [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) (APTCA).

- Nie używaj komunikacji zdalnej platformy .NET.

- Nie używaj rozproszonej Component Object Model (DCOM).

- Nie używaj binarnych elementów formatujących.

Zabezpieczenia dostępu kodu i kod przezroczysty zabezpieczeń nie są obsługiwane jako granice zabezpieczeń z częściowo zaufanym kodem. Odradzamy ładowanie i wykonywanie kodu z nieznanego źródła bez zapewnienia alternatywnych środków bezpieczeństwa. Alternatywne miary zabezpieczeń są następujące:

- Wirtualizacja

- AppContainers

- Użytkownicy i uprawnienia systemu operacyjnego

- Kontenery funkcji Hyper-V

## <a name="security-neutral-code"></a>Kod neutralny pod względem zabezpieczeń

Kod neutralny pod względem zabezpieczeń nie robi niczego jawnie w systemie zabezpieczeń. Jest ona uruchamiana z dowolnymi uprawnieniami, które odbiera. Chociaż aplikacje, które nie przechwytują wyjątków zabezpieczeń skojarzonych z chronionymi operacjami (na przykład używanie plików, sieci itp.), mogą spowodować nieobsługiwany wyjątek, kod neutralny przez zabezpieczenia nadal wykorzystuje technologie zabezpieczeń w programie .NET .

Biblioteka neutralna pod względem zabezpieczeń ma specjalne cechy, które należy zrozumieć. Załóżmy, że biblioteka zawiera elementy interfejsu API, które używają plików lub wywołują kod niezarządzany. Jeśli kod nie ma odpowiednich uprawnień, nie zostanie uruchomiony zgodnie z opisem. Jednak nawet jeśli kod ma uprawnienie, każdy kod aplikacji, który je wywołuje, musi mieć to samo uprawnienie, aby działał. Jeśli wywoływany kod nie ma odpowiednich uprawnień, <xref:System.Security.SecurityException> pojawia się w wyniku przeszukiwania stosu zabezpieczeń dostępu kodu.

## <a name="application-code-that-isnt-a-reusable-component"></a>Kod aplikacji, który nie jest składnikiem wielokrotnego użytku

Jeśli Twój kod jest częścią aplikacji, która nie zostanie wywołana przez inny kod, zabezpieczenia są proste, a specjalne kodowanie może nie być wymagane. Należy jednak pamiętać, że złośliwy kod może wywoływać swój kod. Chociaż zabezpieczenia dostępu kodu mogą uniemożliwić złośliwemu kodowi uzyskanie dostępu do zasobów, taki kod może nadal odczytywać wartości pól lub właściwości, które mogą zawierać poufne informacje.

Ponadto, jeśli kod akceptuje dane wprowadzane przez użytkownika z Internetu lub innych wiarygodnych źródeł, należy zachować ostrożność w przypadku złośliwych danych wejściowych.

## <a name="managed-wrapper-to-native-code-implementation"></a>Otoka zarządzana do implementacji kodu natywnego

Zwykle w tym scenariuszu niektóre użyteczne funkcje są implementowane w kodzie natywnym, który ma zostać udostępniony w kodzie zarządzanym. Zarządzane otoki można łatwo pisać przy użyciu wywołania platformy lub międzyoperacyjności modelu COM. Jednak w takim przypadku obiekty wywołujące otok muszą mieć niezarządzane prawa do kodu w celu pomyślnego wykonania. W obszarze zasady domyślne oznacza to, że kod pobrany z intranetu lub Internetu nie będzie działał z otokami.

Zamiast udzielać niezarządzanych praw kodu wszystkim aplikacjom, które używają tych otok, lepiej jest nadać te prawa tylko kodowi otoki. Jeśli podstawowe funkcje nie ujawniają żadnych zasobów, a implementacja jest w sposób bezpieczny, otoka musi posłużyć tylko do potwierdzenia jego uprawnień, co umożliwia dowolnemu kodowi wywoływanie. Gdy zasoby są wykorzystywane, kodowanie zabezpieczeń powinno być takie samo jak w przypadku kodu biblioteki opisanego w następnej sekcji. Ponieważ otoka może uwidaczniać wywołujących do tych zasobów, należy uważnie sprawdzić bezpieczeństwo kodu natywnego, a następnie ponosi odpowiedzialność otoki.

## <a name="library-code-that-exposes-protected-resources"></a>Kod biblioteki, który uwidacznia chronione zasoby

Poniższe podejście jest najbardziej wydajne i dlatego potencjalnie niebezpieczne (jeśli zostało nieprawidłowo wykonane) do kodowania zabezpieczeń: Biblioteka służy jako interfejs dla innego kodu, aby uzyskać dostęp do niektórych zasobów, które nie są dostępne w inny sposób, podobnie jak klasy .NET wymuszają uprawnienia do zasobów, których używają. Wszędzie tam, gdzie ujawniasz zasób, kod musi najpierw zażądać uprawnień odpowiednich dla zasobu (to oznacza, że musi wykonać sprawdzanie zabezpieczeń), a następnie zazwyczaj potwierdzać prawa do wykonania rzeczywistej operacji.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Zabezpieczanie danych o stanie](securing-state-data.md)|Opisuje sposób ochrony prywatnych członków.|
|[Zabezpieczenia i dane użytkownika](security-and-user-input.md)|Opisuje zagadnienia dotyczące zabezpieczeń aplikacji, które akceptują dane wejściowe użytkownika.|
|[Zabezpieczenia i sytuacja wyścigu](security-and-race-conditions.md)|Opisuje sposób unikania sytuacji wyścigu w kodzie.|
|[Zabezpieczenia i generowanie kodu na bieżąco](security-and-on-the-fly-code-generation.md)|Opisuje zagadnienia dotyczące zabezpieczeń aplikacji generujących kod dynamiczny.|
|[Zabezpieczenia oparte na rolach](role-based-security.md)|Opisuje szczegóły zabezpieczeń opartych na rolach w programie .NET i zawiera instrukcje dotyczące używania jej w kodzie.|
