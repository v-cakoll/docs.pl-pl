---
title: Wersje .NET Framework i Out-of-Band
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: 058bc1a5180060d3c3c6ba4ead1f074a14336b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181564"
---
# <a name="net-framework-and-out-of-band-releases"></a>.NET Framework i wydania poza pasmem

Program .NET Framework ewoluował, aby pomieścić różne platformy, takie jak aplikacje platformy uniwersalnej systemu Windows i tradycyjne aplikacje klasyczne i internetowe, a także zmaksymalizować ponowne użycie kodu. Oprócz regularnych wydań .NET Framework, nowe funkcje są wydawane poza pasmem (OOB), aby poprawić tworzenie między platformami lub wprowadzić nowe funkcje.

## <a name="advantages-of-oob-releases"></a>Zalety wersji OOB

Wysyłanie nowych składników lub aktualizacji do składników poza pasmem umożliwia firmie Microsoft częstsze aktualizowanie programu .NET Framework. Umożliwia to także szybsze zbieranie opinii klientów i reagowanie na nie.

Korzystając z funkcji OOB w aplikacji, użytkownicy nie trzeba instalować najnowszą wersję programu .NET Framework do uruchamiania aplikacji, ponieważ zestawy OOB wdrożyć z pakietem aplikacji.

## <a name="how-oob-packages-are-distributed"></a>Dystrybucja pakietów OOB

Wersje OOB dla podstawowych składników środowiska wykonawczego języka wspólnego (CLR) są dostarczane za pośrednictwem [NuGet](https://www.nuget.org/), który jest menedżerem pakietów dla .NET. NuGet umożliwia przeglądanie i dodawanie bibliotek do projektów platformy .NET Framework łatwo z poziomu programu Visual Studio. Menedżer pakietów NuGet jest dołączony do wszystkich wersji programu Visual Studio, począwszy od programu Visual Studio 2012. Szukaj **Menedżera pakietów NuGet** w menu **Narzędzia** w programie Visual Studio. Jeśli nie jest zainstalowany, postępuj zgodnie z instrukcjami [dotyczącymi instalowania programu NuGet](/nuget/install-nuget-client-tools). Aby uzyskać więcej informacji na temat NuGet, zobacz [dokumenty NuGet](/nuget).

## <a name="use-a-nuget-oob-package"></a>Używanie pakietu NuGet OOB

Jeśli nuget Package Manager jest zainstalowany, można przeglądać i dodawać odwołania do pakietów NuGet przy użyciu Eksploratora rozwiązań w programie Visual Studio:

1. Otwórz menu skrótów dla projektu w programie Visual Studio, a następnie wybierz pozycję **Zarządzaj pakietami NuGet**. (Ta opcja jest również dostępna w menu **Projekt).**

2. W lewym okienku wybierz pozycję **Online**.

3. Jeśli chcesz używać pakietów wersji wstępnej, w polu listy rozwijanej w środkowym okienku wybierz pozycję **Uwzględnij wydanie wstępne** zamiast **stabilnej tylko**.

4. W prawym okienku użyj pola **Wyszukiwania,** aby zlokalizować pakiet, którego chcesz użyć. Niektóre pakiety firmy Microsoft są oznaczone za pomocą logo programu Microsoft .NET Framework, a wszystkie określają firmę Microsoft jako wydawcę.

![Menedżer pakietów NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

Jak wspomniano wcześniej, podczas wdrażania aplikacji używającej pakietu OOB zestawy OOB będą dostarczane wraz z pakietem aplikacji.

## <a name="types-of-oob-releases"></a>Typy wersji OOB

Zazwyczaj pakiet OOB ma jedną lub kilka wersji wstępnych i wersję stabilną. Licencja, która towarzyszy wersji wstępnej zazwyczaj nie zezwala na redystrybucję, ale umożliwia wypróbowanie pakietu i przekazanie opinii. Opinie są włączane do wszelkich aktualizacji wprowadzanych w pakiecie. Ostateczna wersja jest rozpowszechniana jako stabilny pakiet NuGet i zawiera licencję zezwalającą na dystrybucję pakietu NuGet wraz z aplikacją. Stabilne pakiety są obsługiwane przez firmę Microsoft. Firma Microsoft zapewnia pomoc techniczną intellisense, a także inne typy dokumentacji, takie jak wpisy na blogu i odpowiedzi na forum dla wszystkich pakietów. Ponadto kod źródłowy może być dostępny z niektórymi, ale nie wszystkimi pakietami. W przypadku ogłoszeń dotyczących nowych i zaktualizowanych pakietów można subskrybować [blog programu .NET Framework .](https://devblogs.microsoft.com/dotnet/)

Aby znaleźć zarówno pakiety wstępne, jak i **stabilne,** wybierz pozycję Uwzględnij wstępne wydanie w Menedżerze pakietów NuGet.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie](index.md)
