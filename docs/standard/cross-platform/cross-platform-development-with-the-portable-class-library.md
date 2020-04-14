---
title: Tworzenie aplikacji dla wielu platform przy użyciu przenośnej biblioteki klas
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242806"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Tworzenie między platformami dzięki przenośnej bibliotece klas

Typ projektu biblioteki klas przenośnych w programie Visual Studio ułatwia szybkie i łatwe tworzenie aplikacji i bibliotek między platformami dla platform firmy Microsoft.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Przenośne biblioteki klas mogą pomóc skrócić czas i koszty opracowywania i testowania kodu. Ten typ projektu służy do pisania i tworzenia przenośnych zestawów .NET Framework, a następnie odwoływać się do tych zestawów z aplikacji, które są przeznaczone dla wielu platform, takich jak .NET Framework, iOS lub Mac.

Nawet po utworzeniu projektu biblioteki klas przenośnych w programie Visual Studio i rozpoczęciu jego tworzenia można zmienić platformy docelowe. Visual Studio kompiluje bibliotekę z nowych zestawów, co pomaga zidentyfikować zmiany, które należy wprowadzić w kodzie.

## <a name="create-a-portable-class-library-project"></a>Tworzenie projektu przenośnej biblioteki klas

Aby utworzyć bibliotekę klas przenośnych, użyj szablonu dostarczonego w programie Visual Studio. Utwórz nowy projekt **(Plik** > **nowego projektu),** a w oknie dialogowym **Nowy projekt** wybierz język programowania (Visual C# lub Visual Basic). Następnie wybierz szablon **Biblioteka klas (Legacy Portable).** Wprowadź nazwę projektu i wybierz **przycisk OK**.

Zostanie wyświetlone okno dialogowe **Dodawanie biblioteki klas przenośnych.** Wybierz co najmniej dwa obiekty docelowe, a następnie wybierz przycisk **OK**.

![Dodawanie obiektów docelowych biblioteki klas przenośnych w programie Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Zmienianie celów

Platformy docelowe projektu biblioteki klas przenośnych można zmienić podczas jego tworzenia lub po rozpoczęciu tworzenia. Jeśli chcesz zmienić cele po utworzeniu projektu, w **Eksploratorze rozwiązań**otwórz menu **skrótów**dla projektu przenośnej biblioteki klas (nie rozwiązania), a następnie wybierz polecenie Właściwości . Na stronie właściwości projektu **biblioteka** karta pokazuje platformy, które obecnie są przeznaczone dla projektu.

![Właściwości projektu dla przenośnej biblioteki klas w programie Visual Studio](media/pcl-project-properties.png)

Aby dodać lub usunąć obiekty docelowe, wybierz przycisk **Zmień,** a następnie zaznacz i wyczyść odpowiednie pola wyboru.

Po zmianie obiektów docelowych interfejsów API, które są dostępne do tworzenia projektu zmieni się, aby dopasować swój wybór. Visual Studio zgłasza błędy i ostrzeżenia, które mogą wystąpić w wyniku zmiany obiektów docelowych.

Aby ocenić przenośność zestawów przed wprowadzeniem zmian w programie Visual Studio, można użyć [analizatora przenoszenia .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).

## <a name="supported-types-and-members"></a>Obsługiwane typy i elementy członkowskie

Typy i elementy członkowskie, które są dostępne w projektach biblioteki klas przenośnych są ograniczone przez kilka czynników zgodności:

- Muszą być współużytkowane przez wybrane obiekty docelowe.

- Musi zachowywać się podobnie między tymi celami.

- Nie mogą być kandydatami do wycofania z użycia.

- Muszą mieć sens w środowisku przenośnym, zwłaszcza gdy pomocnicze elementy członkowskie nie są przenośne.

Jeśli element członkowski jest obsługiwany w bibliotece klas przenośnych i dla wybranych obiektów docelowych, pojawi się w projekcie w intellisense. Należy jednak pamiętać, że interfejs API może być obsługiwany w bibliotece klas przenośnych, ale czy można użyć interfejsu API zależy od wybranych obiektów docelowych.

## <a name="api-differences-in-the-portable-class-library"></a>Różnice interfejsu API w bibliotece klas przenośnych

Aby zestawy biblioteki klas przenośnych były zgodne ze wszystkimi obsługiwanymi platformami, niektóre elementy członkowskie zostały nieznacznie zmienione w bibliotece klas przenośnych.

## <a name="use-the-portable-class-library"></a>Korzystanie z biblioteki klas przenośnych

Po utworzeniu projektu biblioteki klas przenośnych, wystarczy odwołać się do niego z innych projektów. Odwołanie może dotyczyć projektu lub określonych zestawów zawierających klasy, do których chce się uzyskać dostęp.

Aby uruchomić aplikację, która odwołuje się do zestawu biblioteki klas przenośnych, na komputerze musi być zainstalowana wymagana wersja (lub nowsza) platform docelowych. Visual Studio zawiera wszystkie wymagane struktury, dzięki czemu można uruchomić aplikację bez dalszej modyfikacji na komputerze, który był używany do tworzenia aplikacji.

### <a name="deploy-a-universal-windows-app"></a>Wdrażanie uniwersalnej aplikacji systemu Windows

Podczas tworzenia uniwersalnej aplikacji systemu Windows, która odwołuje się do zestawu biblioteki klas przenośnych, wszystko, czego potrzebujesz do wdrożenia aplikacji jest zawarte w pakiecie aplikacji i nie są wymagane żadne dalsze kroki.

### <a name="deploy-a-net-framework-app"></a>Wdrażanie aplikacji .NET Framework

Podczas wdrażania aplikacji .NET Framework, która odwołuje się do zestawu biblioteki klas przenośnych, należy określić zależność od poprawnej wersji programu .NET Framework. Określenie tej zależności gwarantuje, że wymagana wersja będzie instalowana wraz z aplikacją.

- Aby utworzyć zależność za pomocą clickonce wdrożenia: W **Eksploratorze rozwiązań**wybierz węzeł projektu dla projektu, który chcesz opublikować. (Jest to projekt, który odwołuje się do projektu biblioteki klas przenośnych.) Na pasku menu wybierz pozycję**Właściwości** **projektu** > , a następnie wybierz kartę **Publikuj.** Na stronie **Publikowanie** wybierz pozycję **Wymagania wstępne**. Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.

- Aby utworzyć zależność z projektem instalacji: W **Eksploratorze rozwiązań**wybierz projekt instalacji. Na pasku menu wybierz pozycję**Wymagania** > **wstępne**właściwości **projektu** > . Jako wymaganie wstępne wybierz wymaganą wersję programu .NET Framework.

Aby uzyskać więcej informacji na temat wdrażania aplikacji programu .NET Framework, zobacz [Przewodnik wdrażania dla deweloperów](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Zobacz też

- [Korzystanie z przenośnej biblioteki klas z modelem MVVM](using-portable-class-library-with-model-view-view-model.md)
- [Zasoby aplikacji dla bibliotek przeznaczonych dla wielu platform](app-resources-for-libraries-that-target-multiple-platforms.md)
- [Analizator przenośności .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Wdrożenie](../../../docs/framework/deployment/net-framework-applications.md)
