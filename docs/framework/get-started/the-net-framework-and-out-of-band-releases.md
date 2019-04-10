---
title: Program .NET Framework i wydania poza harmonogramem (OOB)
ms.date: 10/10/2018
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6bf92e118d2ef02c0dc3a550c084e2a0a8e0e3d7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330447"
---
# <a name="the-net-framework-and-out-of-band-releases"></a>Program .NET Framework i wydania poza harmonogramem (OOB)

Program .NET Framework jest rozwijany, tak aby działał na nowych platformach, takich jak aplikacje Windows Phone i aplikacje do Sklepu Windows, a ponadto obsługiwał tradycyjne aplikacje komputerowe i aplikacje internetowe oraz maksymalizował możliwości ponownego wykorzystania kodu. Oprócz regularnych wersji programu .NET Framework nowe funkcje są udostępniane poza harmonogramem (Out of Band, OOB), aby poprawić programowanie wieloplatformowe lub wprowadzić nowe funkcje. W tym temacie omówiono kierunek rozwoju programu .NET Framework i jego wersji OOB.

## <a name="advantages-of-oob-releases"></a>Zalety wersji OOB
 Dostarczanie nowych składników lub aktualizacji składników poza harmonogramem umożliwia firmie Microsoft częstsze dostarczanie aktualizacji programu .NET Framework. Umożliwia to także szybsze zbieranie opinii klientów i reagowanie na nie.

 Gdy w aplikacji jest używana funkcja OOB, użytkownicy nie muszą instalować najnowszej wersji programu systemu .NET Framework, aby uruchomić aplikację, ponieważ zestawy OOB są wdrażane z pakietem aplikacji.

## <a name="how-oob-packages-are-distributed"></a>Dystrybucja pakietów OOB
Wydania OOB dla podstawowych składników środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego są dostarczane za pośrednictwem [NuGet](https://www.nuget.org/), czyli Menedżer pakietów dla platformy .NET. Program NuGet umożliwia łatwe przeglądanie i dodawanie bibliotek do projektów programu .NET Framework z poziomu Eksploratora rozwiązań w programie Visual Studio. Program NuGet jest dołączany do wszystkich wersji programu Visual Studio, począwszy od programu Visual Studio 2012. Aby sprawdzić, czy zainstalowano program NuGet, wyszukaj **Menedżera pakietów NuGet** w programie Visual Studio **narzędzia** menu. Jeśli nie jest zainstalowany:

1. Na pasku menu programu Visual Studio, wybierz **narzędzia**, **rozszerzenia i aktualizacje** (w programie Visual Studio 2010, wybrać **Menedżera rozszerzeń**).

     **Rozszerzenia i aktualizacje** zostanie otwarte okno dialogowe.

2. Wybierz **Online**, **Menedżera pakietów NuGet**, a następnie wybierz **Pobierz**.

3. Po zakończeniu pobierania ponownie uruchom program Visual Studio.

 Aby uzyskać szczegółowe instrukcje dotyczące instalacji, zobacz [Instalowanie systemu NuGet](/nuget/install-nuget-client-tools) w internetowej dokumentacji systemu NuGet. Aby uzyskać więcej informacji na temat programu NuGet, zobacz [dokumentacja programu NuGet](/nuget).

## <a name="using-a-nuget-oob-package"></a>Używanie pakietu NuGet OOB
 Po zainstalowaniu programu NuGet można wyszukiwać i dodawać odwołania do pakietów programu NuGet, używając Eksploratora rozwiązań w programie Visual Studio:

1. Otwórz menu skrótów dla projektu w programie Visual Studio, a następnie wybierz **Zarządzaj pakietami NuGet**. (Ta opcja jest również dostępna z **projektu** menu.)

2. W okienku po lewej stronie wybierz **Online**.

3. Jeśli chcesz używać pakietów wydań wstępnych, w polu listy rozwijanej w środkowym okienku wybierz **Uwzględnij wydania wstępne** zamiast **tylko stabilne**.

4. W okienku po prawej stronie użyj **wyszukiwania** pole, aby zlokalizować pakiet, który chcesz użyć. Niektóre pakiety firmy Microsoft są oznaczone za pomocą logo programu Microsoft .NET Framework, a wszystkie określają firmę Microsoft jako wydawcę.

 ![Zrzut ekranu pokazujący Menedżera pakietów NuGet.](./media/the-net-framework-and-out-of-band-releases/nuget-package-manager-dialog.png)

 Jak wspomniano wcześniej, podczas wdrażania aplikacji używającej pakietu OOB zestawy OOB będą dostarczane wraz z pakietem aplikacji.

## <a name="types-of-oob-releases"></a>Typy wersji OOB
 Zazwyczaj pakiet OOB ma jedną lub kilka wersji wstępnych i wersję stabilną. Licencja, który towarzyszy wersji wstępnej, zazwyczaj nie zezwala na redystrybucję, ale umożliwia wypróbowanie pakietu i wyrazić swoją opinię. Opinie są włączane do wszelkich aktualizacji wprowadzanych w pakiecie. Ostateczna wersja jest rozpowszechniana jako stabilny pakiet NuGet i zawiera licencję zezwalającą na dystrybucję pakietu NuGet wraz z aplikacją. Stabilne pakiety są obsługiwane przez firmę Microsoft. Firma Microsoft zapewnia obsługę technologii IntelliSense, jak również inne typy dokumentacji, takie jak wpisy w blogu i odpowiedzi na forum dla wszystkich pakietów. Ponadto kod źródłowy może być dostępny w niektórych, ale nie wszystkie pakiety. Zapowiedzi dotyczących nowych i zaktualizowanych pakietów, możesz zasubskrybować [Blog programu .NET Framework](https://devblogs.microsoft.com/dotnet/).

 Aby znaleźć stabilne i wstępne pakiety, wybierz **Uwzględnij wydania wstępne** w Menedżerze pakietów NuGet.

 Jeśli chcesz otrzymywać powiadomienia o wydaniach stabilny pakiet, Subskrybuj [źródła danych w programie .NET Framework](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../docs/framework/get-started/index.md)