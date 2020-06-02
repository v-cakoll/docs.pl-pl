---
title: Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 033c9bc6e506d0ae2b9f20fedb72d1b7f29e434b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288917"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Tworzenie aplikacji dla wielu platform za pomocą przenośnej biblioteki klas

Typ projektu Biblioteka klas przenośnych w programie Visual Studio ułatwia szybkie i łatwe tworzenie międzyplatformowych aplikacji i bibliotek dla platform firmy Microsoft.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Przenośne biblioteki klas mogą pomóc w skróceniu czasu i kosztów tworzenia i testowania kodu. Ten typ projektu służy do zapisywania i kompilowania przenośnych zestawów .NET Framework, a następnie odwoływania się do tych zestawów z aplikacji przeznaczonych dla wielu platform, takich jak .NET Framework, iOS lub Mac.

Nawet po utworzeniu projektu przenośnej biblioteki klas w programie Visual Studio i rozpoczęciu opracowywania go można zmienić platformę docelową. Program Visual Studio kompiluje bibliotekę z nowymi zestawami, co pomaga identyfikować zmiany, które należy wprowadzić w kodzie.

## <a name="create-a-portable-class-library-project"></a>Tworzenie projektu biblioteki klas przenośnych

Aby utworzyć przenośną bibliotekę klas, użyj szablonu podanego w programie Visual Studio. Utwórz nowy projekt (**plik**  >  **Nowy projekt**), a następnie w oknie dialogowym **Nowy projekt** wybierz język programowania (Visual C# lub Visual Basic). Następnie wybierz szablon **Biblioteka klas (starsza wersja przenośna)** . Wprowadź nazwę projektu i wybierz **przycisk OK**.

Zostanie wyświetlone okno dialogowe **Dodawanie biblioteki klas przenośnych** . Wybierz co najmniej dwa elementy docelowe, a następnie wybierz przycisk **OK**.

![Dodawanie obiektów docelowych biblioteki klas przenośnych w programie Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Zmień elementy docelowe

Można zmienić platformę docelową projektu przenośnej biblioteki klas podczas jego tworzenia lub po rozpoczęciu opracowywania. Jeśli chcesz zmienić obiekty docelowe po utworzeniu projektu, w **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu biblioteki klas przenośnych (nie rozwiązanie), a następnie wybierz polecenie **Właściwości**. Na stronie właściwości projektu na karcie **Biblioteka** są wyświetlane platformy, dla których projekt jest obecnie docelowy.

![Właściwości projektu dla przenośnej biblioteki klas w programie Visual Studio](media/pcl-project-properties.png)

Aby dodać lub usunąć obiekty docelowe, wybierz przycisk **Zmień** , a następnie zaznacz i wyczyść odpowiednie pola wyboru.

Po zmianie obiektów docelowych interfejsy API, które są dostępne dla opracowywania projektu, zmienią się tak, aby pasowały do wybranego elementu. Program Visual Studio zgłasza błędy i ostrzeżenia, które mogą wystąpić w wyniku zmiany elementów docelowych.

Jeśli chcesz oszacować przenośność zestawów przed wprowadzeniem zmian w programie Visual Studio, możesz użyć [analizatora przenośności platformy .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).

## <a name="supported-types-and-members"></a>Obsługiwane typy i elementy członkowskie

Typy i elementy członkowskie, które są dostępne w przenośnych projektach bibliotek klas, są ograniczone przez kilka czynników zgodności:

- Muszą być współużytkowane przez wybrane obiekty docelowe.

- Musi zachowywać się podobnie dla tych obiektów docelowych.

- Nie mogą być kandydatami do wycofania z użycia.

- Muszą mieć sens w środowisku przenośnym, zwłaszcza gdy pomocnicze elementy członkowskie nie są przenośne.

Jeśli element członkowski jest obsługiwany w bibliotece klas przenośnych i dla wybranych obiektów docelowych, pojawi się w projekcie w technologii IntelliSense. Należy jednak pamiętać, że interfejs API może być obsługiwany w bibliotece klas przenośnych, ale bez względu na to, czy można użyć interfejsu API, zależy od wybranych obiektów docelowych.

## <a name="api-differences-in-the-portable-class-library"></a>Różnice interfejsu API w przenośnej bibliotece klas

Aby zestawy bibliotek klas przenośnych były zgodne ze wszystkimi obsługiwanymi platformami, niektóre elementy członkowskie zostały nieco zmienione w bibliotece klas przenośnych.

## <a name="use-the-portable-class-library"></a>Korzystanie z przenośnej biblioteki klas

Po skompilowaniu projektu biblioteki klas przenośnych należy tylko odwołać się do niego z innych projektów. Odwołanie może dotyczyć projektu lub określonych zestawów zawierających klasy, do których chce się uzyskać dostęp.

Aby uruchomić aplikację, która odwołuje się do zestawu biblioteki klas przenośnych, na komputerze musi być zainstalowana wymagana wersja (lub nowsza) platform. Program Visual Studio zawiera wszystkie wymagane platformy, dzięki czemu można uruchomić aplikację bez dalszych modyfikacji na komputerze, który został użyty do opracowania aplikacji.

### <a name="deploy-a-universal-windows-app"></a>Wdrażanie aplikacji uniwersalnej systemu Windows

Podczas tworzenia aplikacji uniwersalnej systemu Windows, która odwołuje się do zestawu biblioteki klas przenośnych, wszystko, czego potrzebujesz do wdrożenia aplikacji, jest zawarte w pakiecie aplikacji i nie są wymagane żadne dalsze kroki.

### <a name="deploy-a-net-framework-app"></a>Wdrażanie aplikacji .NET Framework

Podczas wdrażania aplikacji .NET Framework, która odwołuje się do zestawu biblioteki klas przenośnych, należy określić zależność od prawidłowej wersji .NET Framework. Określenie tej zależności gwarantuje, że wymagana wersja będzie instalowana wraz z aplikacją.

- Aby utworzyć zależność z wdrożeniem ClickOnce: w **Eksplorator rozwiązań**wybierz węzeł projektu dla projektu, który chcesz opublikować. (Jest to projekt, który odwołuje się do projektu biblioteki klas przenośnych). Na pasku menu wybierz **Project**  >  **Właściwości**projektu, a następnie wybierz kartę **Publikowanie** . Na stronie **Publikowanie** wybierz opcję **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.

- Aby utworzyć zależność z projektem Instalatora: w **Eksplorator rozwiązań**wybierz projekt Instalatora. Na pasku menu wybierz kolejno **Project**pozycje  >  **Właściwości**projektu  >  **wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.

Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Framework, zobacz [Przewodnik wdrażania dla deweloperów](../../framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Zobacz także

- [Korzystanie z przenośnej biblioteki klas z modelem MVVM](using-portable-class-library-with-model-view-view-model.md)
- [Zasoby aplikacji dla bibliotek przeznaczonych dla wielu platform](app-resources-for-libraries-that-target-multiple-platforms.md)
- [Analizator przenośności platformy .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](support-for-windows-store-apps-and-windows-runtime.md)
- [Wdrożenie](../../framework/deployment/net-framework-applications.md)
