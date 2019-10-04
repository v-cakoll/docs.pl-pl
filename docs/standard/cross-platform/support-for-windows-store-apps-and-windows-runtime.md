---
title: Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f46d21123ecfda4bd336edbbd79fabf01e002a4
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835329"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows

.NET Framework 4,5 obsługuje wiele scenariuszy tworzenia oprogramowania z środowisko wykonawcze systemu Windows. Te scenariusze dzielą się na trzy kategorie:

- Opracowywanie aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] z kontrolkami XAML, zgodnie z opisem w [przewodniku dla C# aplikacji do sklepu Windows przy użyciu lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [sposobie korzystania z usługi tos (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))i [platformy .NET dla aplikacji do sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Opracowywanie bibliotek klas do użycia w aplikacjach [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] utworzonych przy użyciu .NET Framework.

- Opracowywanie składników środowisko wykonawcze systemu Windows, spakowane w. Pliki WinMD, które mogą być używane przez dowolny język programowania obsługujący środowisko wykonawcze systemu Windows. Na przykład zapoznaj się [z tematem C# Tworzenie składników środowisko wykonawcze systemu Windows w i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

W tym temacie opisano pomoc .NET Framework techniczną dla wszystkich trzech kategorii oraz scenariusze dotyczące środowisko wykonawcze systemu Windows składników. Pierwsza sekcja zawiera podstawowe informacje o relacji między .NET Framework i środowisko wykonawcze systemu Windows, a także wyjaśnienia niektórych oddities, które mogą wystąpić w systemie pomocy i IDE. W [drugiej sekcji](#WindowsRuntimeComponents) omówiono scenariusze tworzenia środowisko wykonawcze systemu Windows składników programu.

## <a name="the-basics"></a>Podstawowe informacje

.NET Framework obsługuje trzy wymienione wcześniej scenariusze programowania, zapewniając [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] i przez obsługę środowisko wykonawcze systemu Windows.

- [Przestrzenie nazw .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) zapewniają Ulepszony widok bibliotek klas .NET Framework i zawierają tylko typy i elementy członkowskie, których można użyć do tworzenia aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] i środowisko wykonawcze systemu Windows składników.

  - Jeśli używasz programu Visual Studio (Visual Studio 2012 lub nowszego) do tworzenia aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] lub składnika środowisko wykonawcze systemu Windows, zestaw zestawów referencyjnych zapewnia, że zobaczysz tylko odpowiednie typy i elementy członkowskie.

  - Ten usprawniony zestaw interfejsów API jest uproszczony przez usunięcie funkcji, które są zduplikowane w ramach .NET Framework lub zduplikowanych funkcji środowisko wykonawcze systemu Windows. Na przykład zawiera tylko ogólne wersje typów kolekcji, a model obiektów dokumentu XML jest eliminowany na korzyść zestawu interfejsów API środowisko wykonawcze systemu Windows XML.

  - Funkcje, które po prostu zawijają interfejs API systemu operacyjnego, są również usuwane, ponieważ środowisko wykonawcze systemu Windows jest łatwe do wywołania z kodu zarządzanego.

  Aby dowiedzieć się więcej na temat [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], zobacz [Omówienie programu .NET dla aplikacji do sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Aby zapoznać się z procesem wyboru interfejsu API, zobacz wpis [.net for Metro style Apps](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) w blogu platformy .NET.

- [Środowisko wykonawcze systemu Windows](/uwp/api/) udostępnia elementy interfejsu użytkownika do kompilowania aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] i zapewnia dostęp do funkcji systemu operacyjnego. Podobnie jak w przypadku .NET Framework, środowisko wykonawcze systemu Windows zawiera metadane, które C# umożliwiają kompilatorom i Visual Basic używanie środowisko wykonawcze systemu Windows w sposób, w jaki korzystają z bibliotek klas .NET Framework. .NET Framework ułatwia korzystanie z środowisko wykonawcze systemu Windows, ukrywając pewne różnice:

  - Niektóre różnice w wzorcach programowania między .NET Framework i środowisko wykonawcze systemu Windows, takie jak wzorzec służący do dodawania i usuwania programów obsługi zdarzeń, są ukryte. Wystarczy użyć wzorca .NET Framework.

  - Niektóre różnice w najczęściej używanych typach (na przykład typy pierwotne i kolekcje) są ukryte. Wystarczy użyć typu .NET Framework, jak opisano w [różnicach, które są widoczne w środowisku IDE](#DifferencesVisibleInIDE), w dalszej części tego artykułu.

W większości przypadków .NET Framework wsparcia dla środowisko wykonawcze systemu Windows jest przezroczysty. W następnej sekcji omówiono niektóre widoczne różnice między kodem zarządzanym i środowisko wykonawcze systemu Windows.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework i dokumentacja referencyjna środowisko wykonawcze systemu Windows

Środowisko wykonawcze systemu Windows i zestawy dokumentacji .NET Framework są oddzielone. Jeśli naciśniesz klawisz F1, aby wyświetlić pomoc dla typu lub elementu członkowskiego, zostanie wyświetlona dokumentacja referencyjna z odpowiedniego zestawu. Jednak w przypadku przeglądania [środowisko wykonawcze systemu Windows odwołanie](/uwp/api/) może wystąpić przykład Puzzling:

- Tematy, takie jak interfejs <xref:Windows.Foundation.Collections.IIterable%601>, nie mają składni deklaracji Visual Basic lub C#. Zamiast tego, Uwaga pojawia się powyżej sekcji składni (w tym przypadku ".NET: ten interfejs pojawia się jako system. Collections. Generic. IEnumerable @ no__t-0T >"). Jest to spowodowane tym, że .NET Framework i środowisko wykonawcze systemu Windows zapewniają podobną funkcjonalność z różnymi interfejsami. Ponadto istnieją różnice behawioralne: `IIterable` ma metodę `First` zamiast metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>, aby zwrócić moduł wyliczający. Zamiast wymuszania poznania innego sposobu wykonywania typowego zadania .NET Framework obsługuje środowisko wykonawcze systemu Windows, dzięki czemu kod zarządzany będzie wyglądał do korzystania z znanego typu. Nie zobaczysz interfejsu `IIterable` w środowisku IDE i w związku z tym jedynym sposobem, w jaki zostanie on napotkany w dokumentacji referencyjnej środowisko wykonawcze systemu Windows, jest bezpośrednie przeszukiwanie tej dokumentacji.

- Dokumentacja <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> ilustruje ścisły związek problemu: jego typy parametrów są różne dla różnych języków. Dla C# i Visual Basic typy parametrów są <xref:System.String?displayProperty=nameWithType> i <xref:System.Uri?displayProperty=nameWithType>. Jest to spowodowane tym, że .NET Framework ma własne typy `String` i `Uri`, a dla takich często używanych typów nie ma sensu wymuszanie, aby .NET Framework użytkownikom poznać różne sposoby wykonywania zadań. W środowisku IDE .NET Framework ukrywa odpowiednie typy środowisko wykonawcze systemu Windows.

- W kilku przypadkach, takich jak struktura <xref:Windows.UI.Xaml.GridLength>, .NET Framework udostępnia typ o tej samej nazwie, ale większej funkcjonalności. Na przykład zestaw tematów i konstruktorów jest skojarzony z `GridLength`, ale mają bloki składni tylko dla Visual Basic i C# ponieważ elementy członkowskie są dostępne tylko w kodzie zarządzanym. W środowisko wykonawcze systemu Windows struktury mają tylko pola. Struktura środowisko wykonawcze systemu Windows wymaga klasy pomocnika, <xref:Windows.UI.Xaml.GridLengthHelper>, aby zapewnić równoważną funkcjonalność. Ta klasa pomocnika nie zostanie wyświetlona w środowisku IDE podczas pisania kodu zarządzanego.

- W środowisku IDE, środowisko wykonawcze systemu Windows typy pojawiają się od <xref:System.Object?displayProperty=nameWithType>. Wydaje się, że mają członków dziedziczonych z <xref:System.Object>, takich jak <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Te elementy członkowskie działają tak, jak gdyby typy faktycznie dziedziczone z <xref:System.Object> i typy środowisko wykonawcze systemu Windows mogły być rzutowane na <xref:System.Object>. Ta funkcja jest częścią pomocy technicznej zapewnianej przez .NET Framework środowisko wykonawcze systemu Windows. Jednak w przypadku wyświetlania typów w dokumentacji referencyjnej środowisko wykonawcze systemu Windows nie są wyświetlane takie elementy członkowskie. Dokumentacja dla tych pozornie dziedziczonych członków jest dostarczana przez dokumentację referencyjną <xref:System.Object?displayProperty=nameWithType>.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Różnice, które są widoczne w środowisku IDE

W bardziej zaawansowanych scenariuszach programistycznych, takich jak używanie składnika środowisko wykonawcze systemu Windows, który C# jest pisany w celu zapewnienia logiki aplikacji dla aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] skompilowanej dla systemu Windows za pomocą języka JavaScript, takie różnice są widoczne w środowisku IDE, a także w dokumentacji. Gdy składnik zwraca `IDictionary<int, string>` do JavaScript, a zobaczysz go w debugerze JavaScript, zobaczysz metody `IMap<int, string>`, ponieważ język JavaScript używa typu środowisko wykonawcze systemu Windows. W poniższej tabeli przedstawiono niektóre często używane typy kolekcji, które różnią się od siebie w dwóch językach:

|Typ środowisko wykonawcze systemu Windows|Odpowiedni typ .NET Framework|
|--------------------------------------------------------------|---------------------------------------|
|`IIterable<T>`|`IEnumerable<T>`|
|`IIterator<T>`|`IEnumerator<T>`|
|`IVector<T>`|`IList<T>`|
|`IVectorView<T>`|`IReadOnlyList<T>`|
|`IMap<K, V>`|`IDictionary<TKey, TValue>`|
|`IMapView<K, V>`|`IReadOnlyDictionary<TKey, TValue>`|
|`IBindableIterable`|`IEnumerable`|
|`IBindableVector`|`IList`|
|`Windows.UI.Xaml.Data.INotifyPropertyChanged`|`System.ComponentModel.INotifyPropertyChanged`|
|`Windows.UI.Xaml.Data.PropertyChangedEventHandler`|`System.ComponentModel.PropertyChangedEventHandler`|
|`Windows.UI.Xaml.Data.PropertyChangedEventArgs`|`System.ComponentModel.PropertyChangedEventArgs`|

W środowisko wykonawcze systemu Windows `IMap<K, V>` i `IMapView<K, V>` są powtarzane przy użyciu `IKeyValuePair`. Gdy przekazujesz je do kodu zarządzanego, są one wyświetlane jako `IDictionary<TKey, TValue>` i `IReadOnlyDictionary<TKey, TValue>`, więc w naturalny sposób używasz `System.Collections.Generic.KeyValuePair<TKey, TValue>` do wyliczania.

Sposób, w jaki interfejsy pojawiają się w kodzie zarządzanym, mają wpływ na sposób, w jaki są wyświetlane te interfejsy. Na przykład Klasa `PropertySet` implementuje `IMap<K, V>`, który pojawia się w kodzie zarządzanym jako `IDictionary<TKey, TValue>`. `PropertySet` pojawia się tak, jakby był zaimplementowany `IDictionary<TKey, TValue>` zamiast `IMap<K, V>`, więc w kodzie zarządzanym wydaje się, że ma ona metodę `Add`, która zachowuje się jak Metoda `Add` w słownikach .NET Framework. Wydaje się, że nie ma metody `Insert`.

Aby uzyskać więcej informacji o używaniu .NET Framework do tworzenia składnika środowisko wykonawcze systemu Windows i wskazówki, które pokazują, jak używać takiego składnika z JavaScript, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows w C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Typy pierwotne

Aby umożliwić naturalnym wykorzystywanie środowisko wykonawcze systemu Windows w kodzie zarządzanym, .NET Framework typy pierwotne pojawiają się zamiast środowisko wykonawcze systemu Windows typów pierwotnych w kodzie. W .NET Framework typy pierwotne, takie jak struktura `Int32`, mają wiele użytecznych właściwości i metod, takich jak Metoda `Int32.TryParse`. Z kolei typy pierwotne i struktury w środowisko wykonawcze systemu Windows mają tylko pola. W przypadku używania prymitywów w kodzie zarządzanym są one wyświetlane jako .NET Framework typy i można użyć właściwości i metod typów .NET Framework, jak zwykle. Poniższa lista zawiera podsumowanie:

- Dla środowisko wykonawcze systemu Windows podstawowych `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (niezmienna kolekcja znaków Unicode), `Enum`, `UInt32`, `UInt64` i `Guid`, użyj typu o tej samej nazwie w przestrzeni nazw 0.

- W przypadku `UInt8` użyj `System.Byte`.

- W przypadku `Char16` użyj `System.Char`.

- Dla interfejsu `IInspectable` użyj `System.Object`.

- W przypadku `HRESULT` użyj struktury z jednym członkiem `System.Int32`.

Podobnie jak w przypadku typów interfejsów, jedyny czas, w którym można zobaczyć dowód tej reprezentacji, jest to, że projekt .NET Framework jest składnikiem środowisko wykonawcze systemu Windows używanym przez aplikację [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] skompilowaną przy użyciu języka JavaScript.

Inne podstawowe, często używane środowisko wykonawcze systemu Windows typy, które pojawiają się w kodzie zarządzanym jako ich .NET Framework równoważne, zawierają strukturę `Windows.Foundation.DateTime`, która pojawia się w kodzie zarządzanym jako struktura <xref:System.DateTimeOffset?displayProperty=nameWithType> i strukturę @no__t 2, która jest wyświetlana jako <xref:System.TimeSpan?displayProperty=nameWithType> XML.

### <a name="other-differences"></a>Inne różnice

W kilku przypadkach fakt, że typy .NET Framework pojawiają się w kodzie, a nie typy środowisko wykonawcze systemu Windows wymaga działania w Twojej części. Na przykład Klasa <xref:Windows.Foundation.Uri?displayProperty=nameWithType> jest wyświetlana jako <xref:System.Uri?displayProperty=nameWithType> w .NET Framework kodzie. <xref:System.Uri?displayProperty=nameWithType> zezwala na względny identyfikator URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> wymaga bezwzględnego identyfikatora URI. W związku z tym, gdy przekażesz identyfikator URI do metody środowisko wykonawcze systemu Windows, musisz się upewnić, że jest ona bezwzględna. Zobacz [przekazywanie identyfikatora URI do środowisko wykonawcze systemu Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scenariusze tworzenia środowisko wykonawcze systemu Windows składników

Scenariusze obsługiwane przez składniki zarządzane środowisko wykonawcze systemu Windows są zależne od następujących zasad ogólnych:

- Środowisko wykonawcze systemu Windows składniki utworzone przy użyciu .NET Framework nie mają żadnych wyraźnych różnic z innych Runtimelibraries systemu Windows. Na przykład w przypadku ponownego zaimplementowania natywnego składnika środowisko wykonawcze systemu Windows przy użyciu kodu zarządzanego, te dwa składniki są na tym samym poziomie. Fakt, że składnik jest zapisywana w kodzie zarządzanym, jest niewidoczny dla kodu, który go używa, nawet jeśli ten kod jest samym kodem zarządzanym. Jednak wewnętrznie składnik jest prawdziwy kod zarządzany i jest uruchamiany w środowisku uruchomieniowym języka wspólnego (CLR).

- Składniki mogą zawierać typy implementujące logikę aplikacji, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] formantów interfejsu użytkownika lub oba te elementy.

  > [!NOTE]
  > Dobrym sposobem jest oddzielenie elementów interfejsu użytkownika od logiki aplikacji. Ponadto nie można używać formantów interfejsu użytkownika [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] w aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] skompilowanej dla systemu Windows za pomocą języka JavaScript i HTML.

- Składnik może być projektem w ramach rozwiązania Visual Studio dla aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] lub składnika wielokrotnego użytku, który można dodać do wielu rozwiązań.

  > [!NOTE]
  > Jeśli składnik będzie używany tylko z C# lub Visual Basic, nie ma powodów, aby uczynić go składnikiem Środowisko wykonawcze systemu Windows. Jeśli zamiast tego utworzysz jako zwykłą .NET Framework bibliotekę klas, nie musisz ograniczać swojej publicznej powierzchni interfejsu API do typów środowisko wykonawcze systemu Windows.

- Można wydać wersje składników wielokrotnego użytku przy użyciu atrybutu środowisko wykonawcze systemu Windows <xref:Windows.Foundation.Metadata.VersionAttribute>, aby zidentyfikować typy (i elementy członkowskie typu), które zostały dodane w różnych wersjach.

- Typy w składniku mogą pochodzić od typów środowisko wykonawcze systemu Windows. Formanty mogą pochodzić od typów kontrolek pierwotnych w przestrzeni nazw <xref:Windows.UI.Xaml.Controls.Primitives> lub z bardziej gotowymi kontrolkami, takimi jak <xref:Windows.UI.Xaml.Controls.Button>.

  > [!IMPORTANT]
  > Począwszy od [!INCLUDE[win8](../../../includes/win8-md.md)] i .NET Framework 4,5 wszystkie typy publiczne w składniku zarządzanym środowisko wykonawcze systemu Windows muszą być zapieczętowane. Typ w innym składniku środowisko wykonawcze systemu Windows nie może dziedziczyć z nich. Jeśli chcesz zapewnić zachowanie polimorficzne w składniku, możesz utworzyć interfejs i zaimplementować go w typach polimorficznych.

- Wszystkie typy parametrów i zwracanych typów publicznych w składniku muszą być środowisko wykonawcze systemu Windows typy (w tym typy środowisko wykonawcze systemu Windows zdefiniowane przez składnik).

Poniższe sekcje zawierają przykłady typowych scenariuszy.

### <a name="application-logic-for-a-includewin8_appname_longincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logika aplikacji dla aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] z obsługą języka JavaScript

Podczas tworzenia aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] dla systemu Windows za pomocą języka JavaScript może się okazać, że niektóre części logiki aplikacji działają lepiej w kodzie zarządzanym lub są łatwiejsze do opracowania. Język JavaScript nie może używać bibliotek klas .NET Framework bezpośrednio, ale można utworzyć bibliotekę klas a. Plik WinMD. W tym scenariuszu składnik środowisko wykonawcze systemu Windows jest integralną częścią aplikacji, więc nie ma sensu udostępnienia atrybutów wersji.

### <a name="reusable-includewin8_appname_longincludeswin8-appname-long-mdmd-ui-controls"></a>@No__t-0 formantów interfejsu użytkownika wielokrotnego użytku

Zestaw powiązanych kontrolek interfejsu użytkownika można spakować w składniku środowisko wykonawcze systemu Windows wielokrotnego użytku. Składnik może być sprzedawany samodzielnie lub używany jako element w tworzonych aplikacjach. W tym scenariuszu warto użyć atrybutu <xref:Windows.Foundation.Metadata.VersionAttribute> środowisko wykonawcze systemu Windows, aby zwiększyć zgodność.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logika aplikacji wielokrotnego użytku z istniejących aplikacji .NET Framework

Kod zarządzany można spakować z istniejących aplikacji klasycznych jako składnik autonomicznej środowisko wykonawcze systemu Windows. Dzięki temu można używać składnika w aplikacjach [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] utworzonych przy użyciu C++ lub JavaScript, a także w aplikacjach [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] zbudowanych przy użyciu C# lub Visual Basic. Obsługa wersji jest opcją, jeśli istnieje wiele scenariuszy ponownego użycia kodu.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Omówienie programu .NET dla aplikacji do sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Zawiera opis typów .NET Framework i członków, których można użyć do tworzenia aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] i systemu Windows RuntimeComponents. (W centrum deweloperów systemu Windows).|
|[Plan dla aplikacji ze sklepu Windows C# przy użyciu lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Oferuje kluczowe zasoby, które ułatwiają rozpoczęcie opracowywania aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] przy C# użyciu programu lub Visual Basic, w tym wiele tematów szybkiego startu, wytycznych i najlepszych rozwiązań. (W centrum deweloperów systemu Windows).|
|[Jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Oferuje kluczowe zasoby, które ułatwiają rozpoczęcie opracowywania aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] przy C# użyciu programu lub Visual Basic, w tym wiele tematów szybkiego startu, wytycznych i najlepszych rozwiązań. (W centrum deweloperów systemu Windows).|
|[Tworzenie składników środowisko wykonawcze systemu Windows w C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Opisuje sposób tworzenia składnika środowisko wykonawcze systemu Windows przy użyciu .NET Framework. wyjaśnia, jak używać go jako części aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] skompilowanej dla systemu Windows za pomocą języka JavaScript, i opisuje sposób debugowania kombinacji w programie Visual Studio. (W centrum deweloperów systemu Windows).|
|[Informacje środowisko wykonawcze systemu Windows](/uwp/api/)|Dokumentacja referencyjna środowisko wykonawcze systemu Windows. (W centrum deweloperów systemu Windows).|
|[Przekazywanie identyfikatora URI do środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|W tym artykule opisano problem, który może wystąpić w przypadku przekazania identyfikatora URI z kodu zarządzanego do środowisko wykonawcze systemu Windows i sposobu ich unikania.|
