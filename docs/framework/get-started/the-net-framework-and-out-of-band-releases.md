---
title: Program .NET Framework i wydania poza harmonogramem (OOB)
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
ms.openlocfilehash: a2dcd011548df857a1399c5bbdfe6ed33927672e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716403"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>Program .NET Framework i wydania poza harmonogramem (OOB)

Program .NET Framework jest rozwijany, tak aby działał na nowych platformach, takich jak aplikacje Windows Phone i aplikacje do Sklepu Windows, a ponadto obsługiwał tradycyjne aplikacje komputerowe i aplikacje internetowe oraz maksymalizował możliwości ponownego wykorzystania kodu. Oprócz regularnych wersji programu .NET Framework nowe funkcje są udostępniane poza harmonogramem (Out of Band, OOB), aby poprawić programowanie wieloplatformowe lub wprowadzić nowe funkcje. W tym temacie omówiono kierunek rozwoju programu .NET Framework i jego wersji OOB.

## <a name="advantages-of-oob-releases"></a>Zalety wersji OOB
 Dostarczanie nowych składników lub aktualizacji składników poza harmonogramem umożliwia firmie Microsoft częstsze dostarczanie aktualizacji programu .NET Framework. Umożliwia to także szybsze zbieranie opinii klientów i reagowanie na nie.

 Gdy w aplikacji jest używana funkcja OOB, użytkownicy nie muszą instalować najnowszej wersji programu systemu .NET Framework, aby uruchomić aplikację, ponieważ zestawy OOB są wdrażane z pakietem aplikacji.

## <a name="how-oob-packages-are-distributed"></a>Dystrybucja pakietów OOB
Wersje OOB dla podstawowych składników środowiska uruchomieniowego języka wspólnego (CLR) są dostarczane za pomocą narzędzia [NuGet](https://www.nuget.org/), który jest menedżerem pakietów dla platformy .NET. Program NuGet umożliwia łatwe przeglądanie i dodawanie bibliotek do projektów programu .NET Framework z poziomu Eksploratora rozwiązań w programie Visual Studio. Program NuGet jest dołączany do wszystkich wersji programu Visual Studio, począwszy od programu Visual Studio 2012. Aby sprawdzić, czy program NuGet jest zainstalowany, poszukaj **Menedżera pakietów NuGet** w menu **Narzędzia** programu Visual Studio. Jeśli nie jest zainstalowany:

1. Na pasku menu programu Visual Studio wybierz kolejno pozycje **Narzędzia**, **rozszerzenia i aktualizacje** (w programie Visual Studio 2010 wybierz pozycję **Menedżer rozszerzeń**).

     Zostanie otwarte okno dialogowe **rozszerzenia i aktualizacje** .

2. Wybierz pozycję **online**, **Menedżer pakietów NuGet**, a następnie wybierz pozycję **Pobierz**.

3. Po zakończeniu pobierania ponownie uruchom program Visual Studio.

 Aby uzyskać szczegółowe instrukcje dotyczące instalacji, zobacz [Instalowanie programu NuGet](/nuget/install-nuget-client-tools) w witrynie sieci Web programu NuGet docs. Więcej informacji o narzędziu NuGet można znaleźć w [dokumentacji programu NuGet](/nuget).

## <a name="using-a-nuget-oob-package"></a>Używanie pakietu NuGet OOB
 Po zainstalowaniu programu NuGet można wyszukiwać i dodawać odwołania do pakietów programu NuGet, używając Eksploratora rozwiązań w programie Visual Studio:

1. Otwórz menu skrótów dla projektu w programie Visual Studio, a następnie wybierz polecenie **Zarządzaj pakietami NuGet**. (Ta opcja jest również dostępna w menu **projekt** ).

2. W lewym okienku wybierz pozycję **online**.

3. Jeśli chcesz używać pakietów wstępnych, w polu listy rozwijanej w środkowym okienku wybierz opcję **Uwzględnij wersje wstępne** zamiast **tylko stabilne**.

4. W okienku po prawej stronie użyj pola **wyszukiwania** , aby zlokalizować pakiet, którego chcesz użyć. Niektóre pakiety firmy Microsoft są oznaczone za pomocą logo programu Microsoft .NET Framework, a wszystkie określają firmę Microsoft jako wydawcę.

 ![Zrzut ekranu przedstawiający Menedżera pakietów NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

 Jak wspomniano wcześniej, podczas wdrażania aplikacji używającej pakietu OOB zestawy OOB będą dostarczane wraz z pakietem aplikacji.

## <a name="types-of-oob-releases"></a>Typy wersji OOB
 Zazwyczaj pakiet OOB ma jedną lub kilka wersji wstępnych i wersję stabilną. Licencja, która towarzyszy wersji wstępnej, zazwyczaj nie zezwala na ponowną dystrybucję, ale umożliwia wypróbowanie pakietu i przesłanie opinii. Opinie są włączane do wszelkich aktualizacji wprowadzanych w pakiecie. Ostateczna wersja jest rozpowszechniana jako stabilny pakiet NuGet i zawiera licencję zezwalającą na dystrybucję pakietu NuGet wraz z aplikacją. Pakiety stabilne są obsługiwane przez firmę Microsoft. Firma Microsoft zapewnia pomoc techniczną IntelliSense, jak również inne typy dokumentacji, takie jak wpisy w blogu i odpowiedzi na forum dla wszystkich pakietów. Ponadto kod źródłowy może być dostępny w przypadku niektórych, ale nie wszystkich pakietów. Anonse dotyczące nowych i zaktualizowanych pakietów można subskrybować [blogu .NET Framework](https://devblogs.microsoft.com/dotnet/).

 Aby znaleźć zarówno wstępne, jak i stabilne pakiety, wybierz pozycję **Uwzględnij wersję wstępną** w Menedżerze pakietów NuGet.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](index.md)
