---
title: .NET Framework i wersje poza pasmem
description: Dowiedz się więcej o wersjach platformy .NET i oprogramowania poza pasmem. Nowe funkcje są wydane poza pasmem (OOB), aby ulepszyć Programowanie dla wielu platform lub wprowadzić nowe funkcje.
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 9653696f46279e0c23418f92030d64839cc20518
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618769"
---
# <a name="net-framework-and-out-of-band-releases"></a>Program .NET Framework i wydania poza harmonogramem (OOB)

.NET Framework został rozwijający się w celu uwzględnienia różnych platform, takich jak aplikacje platformy UWP oraz tradycyjne aplikacje klasyczne i sieci Web, a także do zmaksymalizowania ponownego użycia kodu. Oprócz zwykłych wersji .NET Framework nowe funkcje są zwalniane poza pasmem (OOB), co pozwala ulepszyć Programowanie na wielu platformach lub wprowadzać nowe funkcje.

## <a name="advantages-of-oob-releases"></a>Zalety wersji OOB

Wysyłka nowych składników lub aktualizacji składników poza pasmem umożliwia firmie Microsoft dostarczanie bardziej częstych aktualizacji do .NET Framework. Umożliwia to także szybsze zbieranie opinii klientów i reagowanie na nie.

Jeśli używasz funkcji OOB w aplikacji, użytkownicy nie muszą instalować najnowszej wersji .NET Framework, aby uruchomić aplikację, ponieważ zestawy OOB są wdrażane z pakietem aplikacji.

## <a name="how-oob-packages-are-distributed"></a>Dystrybucja pakietów OOB

Wersje OOB dla podstawowych składników środowiska uruchomieniowego języka wspólnego (CLR) są dostarczane za pomocą programu [NuGet](https://www.nuget.org/), który jest menedżerem pakietów dla platformy .NET. Pakiet NuGet umożliwia łatwe przeglądanie i Dodawanie bibliotek do .NET Frameworkych projektów z poziomu programu Visual Studio. Menedżer pakietów NuGet jest dostępny we wszystkich wersjach programu Visual Studio, począwszy od programu Visual Studio 2012. Poszukaj **Menedżera pakietów NuGet** w menu **Narzędzia** w programie Visual Studio. Jeśli nie jest zainstalowana, postępuj zgodnie z instrukcjami dotyczącymi [instalowania programu NuGet](/nuget/install-nuget-client-tools). Aby uzyskać więcej informacji na temat narzędzia NuGet, zobacz [dokumenty NuGet](/nuget).

## <a name="use-a-nuget-oob-package"></a>Używanie pakietu NuGet OOB

Jeśli zainstalowano Menedżera pakietów NuGet, można przeglądać i dodawać odwołania do pakietów NuGet przy użyciu Eksplorator rozwiązań w programie Visual Studio:

1. Otwórz menu skrótów dla projektu w programie Visual Studio, a następnie wybierz polecenie **Zarządzaj pakietami NuGet**. (Ta opcja jest również dostępna w menu **projekt** ).

2. W lewym okienku wybierz pozycję **online**.

3. Jeśli chcesz używać pakietów wstępnych, w polu listy rozwijanej w środkowym okienku wybierz opcję **Uwzględnij wersje wstępne** zamiast **tylko stabilne**.

4. W okienku po prawej stronie użyj pola **wyszukiwania** , aby zlokalizować pakiet, którego chcesz użyć. Niektóre pakiety firmy Microsoft są oznaczone za pomocą logo programu Microsoft .NET Framework, a wszystkie określają firmę Microsoft jako wydawcę.

![Menedżer pakietów NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Jak wspomniano wcześniej, podczas wdrażania aplikacji używającej pakietu OOB zestawy OOB będą dostarczane wraz z pakietem aplikacji.

## <a name="types-of-oob-releases"></a>Typy wersji OOB

Zazwyczaj pakiet OOB ma jedną lub kilka wersji wstępnych i wersję stabilną. Licencja, która towarzyszy wersji wstępnej, zazwyczaj nie zezwala na ponowną dystrybucję, ale umożliwia wypróbowanie pakietu i przesłanie opinii. Opinie są włączane do wszelkich aktualizacji wprowadzanych w pakiecie. Ostateczna wersja jest rozpowszechniana jako stabilny pakiet NuGet i zawiera licencję zezwalającą na dystrybucję pakietu NuGet wraz z aplikacją. Pakiety stabilne są obsługiwane przez firmę Microsoft. Firma Microsoft zapewnia pomoc techniczną IntelliSense, jak również inne typy dokumentacji, takie jak wpisy w blogu i odpowiedzi na forum dla wszystkich pakietów. Ponadto kod źródłowy może być dostępny w przypadku niektórych, ale nie wszystkich pakietów. Anonse dotyczące nowych i zaktualizowanych pakietów można subskrybować [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).

Aby znaleźć zarówno wstępne, jak i stabilne pakiety, wybierz opcję **Uwzględnij wersję wstępną** w Menedżerze pakietów NuGet.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](index.md)
