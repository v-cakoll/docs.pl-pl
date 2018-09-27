---
title: Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: afaa8e118bb21e5c1e4f1c53b1d0d29ca6bb3bf5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237270"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Programowanie dla wielu platform przy użyciu biblioteki klas przenośnych

Typ projektu biblioteki klas przenośnych w programie Visual Studio pomaga w tworzeniu aplikacji dla wielu platform i bibliotek dla platform firmy Microsoft, szybkie i łatwe.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Biblioteki klas przenośnych mogą pomóc skrócić czas i koszt programowania oraz testowania kodu. Użyj tego typu projektu do zapisywania i tworzenia przenośnych zestawów .NET Framework, a następnie odwołuje się do tych zestawów z aplikacji przeznaczonych dla wielu platform, takich jak .NET Framework, iOS i komputerów Mac.

Nawet po Utwórz projekt biblioteki klas przenośnych w programie Visual Studio i zacznij programować go, możesz zmienić platformy docelowe. Program Visual Studio kompiluje biblioteki za pomocą nowych zestawów, który pomaga zidentyfikować zmiany, które należy wprowadzić w kodzie.

## <a name="create-a-portable-class-library-project"></a>Utwórz projekt biblioteki klas przenośnych

Aby utworzyć Portable Class Library, należy użyć szablonu dostępnego w programie Visual Studio. Utwórz nowy projekt (**pliku** > **nowy projekt**), a następnie w **nowy projekt** okna dialogowego Wybierz język programowania (Visual C# lub Visual Basic). Następnie wybierz **biblioteki klas (starsza wersja przenośny)** szablonu. Wprowadź nazwę dla projektu, a następnie wybierz **OK**.

**Dodaj Portable Class Library** pojawi się okno dialogowe. Wybierz co najmniej dwa elementy docelowe, a następnie wybierz **OK**.

![Dodaj elementy docelowe biblioteki klas przenośnych w programie Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Zmień cele

Możesz zmienić platformy docelowe projektu biblioteki klas przenośnych podczas jej tworzenia lub po rozpoczęciu programowania. Jeśli chcesz zmienić elementy docelowe, po utworzeniu projektu w **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu biblioteki klas przenośnych (nie rozwiązanie), a następnie wybierz **właściwości** . Na stronie właściwości projektu **biblioteki** karta przedstawia platformy projektu obecnie dotyczy.

![Właściwości projektu biblioteki klas przenośnych w programie Visual Studio](media/pcl-project-properties.png)

Aby dodać lub usunąć elementy docelowe, wybierz opcję **zmiany** przycisk, a następnie wybierz i usuń zaznaczenie pola wyboru.

Jeśli zmienisz docelowe, interfejsów API, które są dostępne i umożliwiają tworzenie projektu zmieni się na dopasować wybór. Visual Studio zgłasza błędy i ostrzeżenia, które może wyniknąć z elementów docelowych, zmiana.

Jeśli chcesz przeprowadzić ocenę przenośność zestawy przed wprowadzić zmiany w programie Visual Studio, można użyć [narzędzia .NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).

## <a name="supported-types-and-members"></a>Obsługiwane typy i elementy członkowskie

Typy i elementy członkowskie, które są dostępne w projektach Portable Class Library zależy od kilku czynników zgodności:

-   Muszą one zostać udostępnione w lokalizacjach docelowych, które wybrano.

-   Musi zachowywać się podobnie w tych lokalizacjach docelowych.

-   Nie mogą być kandydatami do wycofania z użycia.

-   Muszą mieć sens w środowisku przenośnym, zwłaszcza gdy pomocnicze elementy członkowskie nie są przenośne.

Jeśli członek jest obsługiwany, in Portable Class Library i wybrane elementy docelowe, pojawi się w projekcie w technologii IntelliSense. Należy jednak pamiętać, że interfejs API może być obsługiwana w Portable Class Library, ale czy można użyć interfejsu API zależy od celów wybierz.

## <a name="api-differences-in-the-portable-class-library"></a>Różnice interfejsu API w bibliotece klas przenośnych

Aby zestawy Portable Class Library zgodne na wszystkich obsługiwanych platformach, niektórzy członkowie nieznacznie zmieniono in Portable Class Library.

## <a name="use-the-portable-class-library"></a>Korzystanie z biblioteki klas przenośnych

Po skompilowaniu projektu Portable Class Library, możesz po prostu odwołanie do niego z innych projektów. Odwołanie może dotyczyć projektu lub określonych zestawów zawierających klasy, do których chce się uzyskać dostęp.

Aby uruchomić aplikację, która odwołuje się do zestawu Portable Class Library, wymagana wersja (lub nowszym) platformy docelowej musi być zainstalowany na tym komputerze. Program Visual Studio zawiera wszystkie wymagane struktury, aby można było uruchomić aplikację bez dalszych modyfikacji na komputerze, który jest używany do tworzenia aplikacji.

### <a name="deploy-a-universal-windows-app"></a>Wdrażanie aplikacji Windows Universal

Podczas tworzenia aplikacji Windows Universal odwołujący się do zestawu Portable Class Library, wszystko, czego potrzebujesz do wdrażania aplikacji znajduje się w pakiecie aplikacji i nie trzeba wykonywać dalszych czynności są wymagane.

### <a name="deploy-a-net-framework-app"></a>Wdrażanie .NET Framework aplikacji

Podczas wdrażania aplikacji .NET Framework, która odwołuje się do zestawu Portable Class Library, należy określić zależność od prawidłowej wersji programu .NET Framework. Określenie tej zależności gwarantuje, że wymagana wersja będzie instalowana wraz z aplikacją.

-   Aby utworzyć zależność z wdrożeniem ClickOnce: W **Eksploratora rozwiązań**, wybierz węzeł projektu dla projektu, który chcesz opublikować. (Jest to projekt, który odwołuje się do projektu Portable Class Library). Na pasku menu wybierz **projektu** > **właściwości**, a następnie wybierz **Publikuj** kartę. Na **Publikuj** wybierz **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.

-   Aby utworzyć zależność z projektem Instalatora: W **Eksploratora rozwiązań**, wybierz projekt Instalatora. Na pasku menu wybierz **projektu** > **właściwości** > **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.

Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Framework, zobacz [przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Zobacz także

- [Korzystanie z biblioteki klas przenośnych z modelem MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [Zasoby aplikacji dla bibliotek przeznaczonych do wielu platform](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [Narzędzia .NET portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Wdrażanie](../../../docs/framework/deployment/net-framework-applications.md)
