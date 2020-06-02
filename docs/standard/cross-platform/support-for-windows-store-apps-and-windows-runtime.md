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
ms.openlocfilehash: 7ca5a1259f970f2db5400837eb7d20998dd824cb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288865"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows

.NET Framework 4,5 obsługuje wiele scenariuszy tworzenia oprogramowania z środowisko wykonawcze systemu Windows. Te scenariusze dzielą się na trzy kategorie:

- Opracowywanie aplikacji ze sklepu Windows 8. x przy użyciu kontrolek XAML, jak opisano w temacie [Przewodnik dla aplikacji do sklepu Windows przy użyciu języka C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))i [.NET dla aplikacji do sklepu Windows — omówienie](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Opracowywanie bibliotek klas do użycia w aplikacjach do sklepu Windows 8. x utworzonych przy użyciu .NET Framework.

- Opracowywanie składników środowisko wykonawcze systemu Windows, spakowane w. Pliki WinMD, które mogą być używane przez dowolny język programowania obsługujący środowisko wykonawcze systemu Windows. Na przykład zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows w językach C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

W tym temacie opisano pomoc .NET Framework techniczną dla wszystkich trzech kategorii oraz scenariusze dotyczące środowisko wykonawcze systemu Windows składników. Pierwsza sekcja zawiera podstawowe informacje o relacji między .NET Framework i środowisko wykonawcze systemu Windows, a także wyjaśnienia niektórych oddities, które mogą wystąpić w systemie pomocy i IDE. W [drugiej sekcji](#WindowsRuntimeComponents) omówiono scenariusze tworzenia środowisko wykonawcze systemu Windows składników programu.

## <a name="the-basics"></a>Podstawowe informacje

.NET Framework obsługuje trzy scenariusze programowania wymienione wcześniej przez udostępnienie platformy .NET dla systemu Windows 8. x aplikacji ze sklepu i przez obsługę środowisko wykonawcze systemu Windows

- [Przestrzenie nazw .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) zapewniają usprawniony widok bibliotek klas .NET Framework i zawierają tylko typy i elementy członkowskie, których można użyć do tworzenia aplikacji do sklepu Windows 8. x i składników Środowisko wykonawcze systemu Windows.

  - Jeśli używasz programu Visual Studio (Visual Studio 2012 lub nowszego) do tworzenia aplikacji ze sklepu Windows 8. x lub składnika środowisko wykonawcze systemu Windows, zestaw zestawów referencyjnych zapewnia, że zobaczysz tylko odpowiednie typy i elementy członkowskie.

  - Ten usprawniony zestaw interfejsów API jest uproszczony przez usunięcie funkcji, które są zduplikowane w ramach .NET Framework lub zduplikowanych funkcji środowisko wykonawcze systemu Windows. Na przykład zawiera tylko ogólne wersje typów kolekcji, a model obiektów dokumentu XML jest eliminowany na korzyść zestawu interfejsów API środowisko wykonawcze systemu Windows XML.

  - Funkcje, które po prostu zawijają interfejs API systemu operacyjnego, są również usuwane, ponieważ środowisko wykonawcze systemu Windows jest łatwe do wywołania z kodu zarządzanego.

  Aby dowiedzieć się więcej na temat aplikacji ze sklepu .NET dla systemu Windows 8. x, zobacz [Omówienie programu .NET dla aplikacji do sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Aby zapoznać się z procesem wyboru interfejsu API, zobacz wpis [.net for Metro style Apps](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) w blogu platformy .NET.

- [Środowisko wykonawcze systemu Windows](/uwp/api/) udostępnia elementy interfejsu użytkownika do kompilowania aplikacji ze sklepu Windows 8. x i zapewnia dostęp do funkcji systemu operacyjnego. Podobnie jak w przypadku .NET Framework, środowisko wykonawcze systemu Windows zawiera metadane, które umożliwiają kompilatorom języka C# i Visual Basic używanie środowisko wykonawcze systemu Windows w sposób, w jaki korzystają z bibliotek klas .NET Framework. .NET Framework ułatwia korzystanie z środowisko wykonawcze systemu Windows, ukrywając pewne różnice:

  - Niektóre różnice w wzorcach programowania między .NET Framework i środowisko wykonawcze systemu Windows, takie jak wzorzec służący do dodawania i usuwania programów obsługi zdarzeń, są ukryte. Wystarczy użyć wzorca .NET Framework.

  - Niektóre różnice w najczęściej używanych typach (na przykład typy pierwotne i kolekcje) są ukryte. Wystarczy użyć typu .NET Framework, jak opisano w [różnicach, które są widoczne w środowisku IDE](#DifferencesVisibleInIDE), w dalszej części tego artykułu.

W większości przypadków .NET Framework wsparcia dla środowisko wykonawcze systemu Windows jest przezroczysty. W następnej sekcji omówiono niektóre widoczne różnice między kodem zarządzanym i środowisko wykonawcze systemu Windows.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework i dokumentacja referencyjna środowisko wykonawcze systemu Windows

Środowisko wykonawcze systemu Windows i zestawy dokumentacji .NET Framework są oddzielone. Jeśli naciśniesz klawisz F1, aby wyświetlić pomoc dla typu lub elementu członkowskiego, zostanie wyświetlona dokumentacja referencyjna z odpowiedniego zestawu. Jednak w przypadku przeglądania [środowisko wykonawcze systemu Windows odwołanie](/uwp/api/) może wystąpić przykład Puzzling:

- Tematy, takie jak <xref:Windows.Foundation.Collections.IIterable%601> interfejs, nie mają składni deklaracji dla Visual Basic lub C#. Zamiast tego, Uwaga pojawia się powyżej sekcji składni (w tym przypadku ".NET: ten interfejs pojawia się jako system. Collections. Generic. IEnumerable \<T> "). Jest to spowodowane tym, że .NET Framework i środowisko wykonawcze systemu Windows zapewniają podobną funkcjonalność z różnymi interfejsami. Ponadto istnieją różnice behawioralne: `IIterable` ma metodę, która `First` nie ma <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody do zwracania modułu wyliczającego. Zamiast wymuszania poznania innego sposobu wykonywania typowego zadania .NET Framework obsługuje środowisko wykonawcze systemu Windows, dzięki czemu kod zarządzany będzie wyglądał do korzystania z znanego typu. Interfejs nie zostanie wyświetlony `IIterable` w środowisku IDE i w związku z tym jedynym sposobem, w jaki zobaczysz, w dokumentacji referencyjnej Środowisko wykonawcze systemu Windows można bezpośrednio przeszukiwać tę dokumentację.

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)>Dokumentacja ilustruje ścisły związek problemu: jego typy parametrów są różne dla różnych języków. Dla języków C# i Visual Basic typy parametrów są <xref:System.String?displayProperty=nameWithType> i <xref:System.Uri?displayProperty=nameWithType> . Jest to spowodowane tym, że .NET Framework ma własne `String` i `Uri` typy, a dla takich często używanych typów nie ma sensu, aby wymusić .NET Framework użytkownikom poznać różne sposoby wykonywania zadań. W środowisku IDE .NET Framework ukrywa odpowiednie typy środowisko wykonawcze systemu Windows.

- W kilku przypadkach, takich jak <xref:Windows.UI.Xaml.GridLength> Struktura, .NET Framework zapewnia typ o tej samej nazwie, ale więcej funkcji. Na przykład zestaw tematów i konstruktorów jest skojarzony z `GridLength` , ale mają bloki składni tylko dla Visual Basic i C#, ponieważ elementy członkowskie są dostępne tylko w kodzie zarządzanym. W środowisko wykonawcze systemu Windows struktury mają tylko pola. Struktura środowisko wykonawcze systemu Windows wymaga klasy pomocnika, <xref:Windows.UI.Xaml.GridLengthHelper> w celu zapewnienia równoważnej funkcjonalności. Ta klasa pomocnika nie zostanie wyświetlona w środowisku IDE podczas pisania kodu zarządzanego.

- W środowisku IDE są wyświetlane środowisko wykonawcze systemu Windows typy, które pochodzą od <xref:System.Object?displayProperty=nameWithType> . Wydaje się, że mają członków dziedziczonych z <xref:System.Object> , takich jak <xref:System.Object.ToString%2A?displayProperty=nameWithType> . Te elementy członkowskie działają tak, jak gdyby typy faktycznie dziedziczone z <xref:System.Object> i typy środowisko wykonawcze systemu Windows mogły być rzutowane na <xref:System.Object> . Ta funkcja jest częścią pomocy technicznej zapewnianej przez .NET Framework środowisko wykonawcze systemu Windows. Jednak w przypadku wyświetlania typów w dokumentacji referencyjnej środowisko wykonawcze systemu Windows nie są wyświetlane takie elementy członkowskie. Dokumentacja tych pozornie dziedziczonych członków jest dostarczana przez <xref:System.Object?displayProperty=nameWithType> dokumentację referencyjną.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Różnice, które są widoczne w środowisku IDE

W bardziej zaawansowanych scenariuszach programistycznych, takich jak używanie środowisko wykonawcze systemu Windows składnika zapisanego w języku C#, aby zapewnić logikę aplikacji dla aplikacji ze sklepu Windows 8. x skompilowaną dla systemu Windows za pomocą języka JavaScript, takie różnice są widoczne w środowisku IDE oraz w dokumentacji. Gdy składnik zwraca `IDictionary<int, string>` kod JavaScript, a zobaczysz go w debugerze JavaScript, zobaczysz metody, `IMap<int, string>` ponieważ język JavaScript używa typu środowisko wykonawcze systemu Windows. W poniższej tabeli przedstawiono niektóre często używane typy kolekcji, które różnią się od siebie w dwóch językach:

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

W środowisko wykonawcze systemu Windows `IMap<K, V>` i `IMapView<K, V>` zostały powtórzone przy użyciu `IKeyValuePair` . Gdy przekazujesz je do kodu zarządzanego, są one wyświetlane jako `IDictionary<TKey, TValue>` i `IReadOnlyDictionary<TKey, TValue>` , więc naturalnie używane `System.Collections.Generic.KeyValuePair<TKey, TValue>` do wyliczania.

Sposób, w jaki interfejsy pojawiają się w kodzie zarządzanym, mają wpływ na sposób, w jaki są wyświetlane te interfejsy. Na przykład `PropertySet` Klasa implementuje `IMap<K, V>` , która pojawia się w kodzie zarządzanym jako `IDictionary<TKey, TValue>` . `PropertySet`pojawia się tak, jakby był zaimplementowany `IDictionary<TKey, TValue>` zamiast `IMap<K, V>` , tak więc w kodzie zarządzanym wydaje się `Add` , że ma metodę, która zachowuje się jak `Add` metoda w słownikach .NET Framework. Wydaje się, że nie ma `Insert` metody.

Aby uzyskać więcej informacji o używaniu .NET Framework do tworzenia składnika środowisko wykonawcze systemu Windows i wskazówki, które pokazują, jak używać takiego składnika z JavaScript, zobacz [Tworzenie składników Środowisko wykonawcze systemu Windows w językach C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Typy pierwotne

Aby umożliwić naturalnym wykorzystywanie środowisko wykonawcze systemu Windows w kodzie zarządzanym, .NET Framework typy pierwotne pojawiają się zamiast środowisko wykonawcze systemu Windows typów pierwotnych w kodzie. W .NET Framework typy pierwotne, takie jak `Int32` Struktura, mają wiele użytecznych właściwości i metod, takich jak `Int32.TryParse` Metoda. Z kolei typy pierwotne i struktury w środowisko wykonawcze systemu Windows mają tylko pola. W przypadku używania prymitywów w kodzie zarządzanym są one wyświetlane jako .NET Framework typy i można użyć właściwości i metod typów .NET Framework, jak zwykle. Poniższa lista zawiera podsumowanie:

- W przypadku środowisko wykonawcze systemu Windows podstawowych,,,,, `Int32` `Int64` `Single` `Double` `Boolean` `String` (niezmienna kolekcja znaków Unicode),,, `Enum` `UInt32` `UInt64` i, należy `Guid` użyć typu o tej samej nazwie w `System` przestrzeni nazw.

- Dla programu `UInt8` , użyj `System.Byte` .

- Dla programu `Char16` , użyj `System.Char` .

- Dla `IInspectable` interfejsu Użyj `System.Object` .

- W przypadku programu `HRESULT` należy użyć struktury z jednym `System.Int32` elementem członkowskim.

Podobnie jak w przypadku typów interfejsów, jedyny czas, w którym można zobaczyć dowód tej reprezentacji, jest to, że projekt .NET Framework jest składnikiem środowisko wykonawcze systemu Windows używanym przez aplikację ze sklepu Windows 8. x utworzoną przy użyciu języka JavaScript.

Inne podstawowe, często używane środowisko wykonawcze systemu Windows typy, które pojawiają się w kodzie zarządzanym jako ich .NET Framework równoważne `Windows.Foundation.DateTime` , obejmują strukturę, która pojawia się w kodzie zarządzanym jako <xref:System.DateTimeOffset?displayProperty=nameWithType> Struktura i `Windows.Foundation.TimeSpan` strukturę, która pojawia się jako <xref:System.TimeSpan?displayProperty=nameWithType> Struktura.

### <a name="other-differences"></a>Inne różnice

W kilku przypadkach fakt, że typy .NET Framework pojawiają się w kodzie, a nie typy środowisko wykonawcze systemu Windows wymaga działania w Twojej części. Na przykład <xref:Windows.Foundation.Uri?displayProperty=nameWithType> Klasa jest wyświetlana <xref:System.Uri?displayProperty=nameWithType> w .NET Framework kodzie. <xref:System.Uri?displayProperty=nameWithType>zezwala na względny identyfikator URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> wymaga bezwzględnego identyfikatora URI. W związku z tym, gdy przekażesz identyfikator URI do metody środowisko wykonawcze systemu Windows, musisz się upewnić, że jest ona bezwzględna. Zobacz [przekazywanie identyfikatora URI do środowisko wykonawcze systemu Windows](passing-a-uri-to-the-windows-runtime.md).

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scenariusze tworzenia środowisko wykonawcze systemu Windows składników

Scenariusze obsługiwane przez składniki zarządzane środowisko wykonawcze systemu Windows są zależne od następujących zasad ogólnych:

- Środowisko wykonawcze systemu Windows składniki utworzone przy użyciu .NET Framework nie mają żadnych wyraźnych różnic z innych Runtimelibraries systemu Windows. Na przykład w przypadku ponownego zaimplementowania natywnego składnika środowisko wykonawcze systemu Windows przy użyciu kodu zarządzanego, te dwa składniki są na tym samym poziomie. Fakt, że składnik jest zapisywana w kodzie zarządzanym, jest niewidoczny dla kodu, który go używa, nawet jeśli ten kod jest samym kodem zarządzanym. Jednak wewnętrznie składnik jest prawdziwy kod zarządzany i jest uruchamiany w środowisku uruchomieniowym języka wspólnego (CLR).

- Składniki mogą zawierać typy implementujące logikę aplikacji, kontrolki interfejsu użytkownika systemu Windows 8. x lub oba te elementy.

  > [!NOTE]
  > Dobrym sposobem jest oddzielenie elementów interfejsu użytkownika od logiki aplikacji. Ponadto nie można używać kontrolek interfejsu użytkownika sklepu Windows 8. x w aplikacji ze sklepu Windows 8. x skompilowanej dla systemu Windows za pomocą języka JavaScript i języka HTML.

- Składnik może być projektem w ramach rozwiązania Visual Studio dla aplikacji ze sklepu Windows 8. x lub składnika wielokrotnego użytku, który można dodać do wielu rozwiązań.

  > [!NOTE]
  > Jeśli składnik będzie używany tylko w języku C# lub Visual Basic, nie ma powodów, aby uczynić go składnikiem środowisko wykonawcze systemu Windows. Jeśli zamiast tego utworzysz jako zwykłą .NET Framework bibliotekę klas, nie musisz ograniczać swojej publicznej powierzchni interfejsu API do typów środowisko wykonawcze systemu Windows.

- Można wydać wersje składników wielokrotnego użytku przy użyciu atrybutu środowisko wykonawcze systemu Windows, <xref:Windows.Foundation.Metadata.VersionAttribute> Aby zidentyfikować typy (i elementy członkowskie w ramach typu), które zostały dodane w różnych wersjach.

- Typy w składniku mogą pochodzić od typów środowisko wykonawcze systemu Windows. Formanty mogą pochodzić od typów kontrolek pierwotnych w <xref:Windows.UI.Xaml.Controls.Primitives> przestrzeni nazw lub od bardziej gotowych kontrolek, takich jak <xref:Windows.UI.Xaml.Controls.Button> .

  > [!IMPORTANT]
  > Począwszy od systemu Windows 8 i .NET Framework 4,5 wszystkie typy publiczne w składniku zarządzanym środowisko wykonawcze systemu Windows muszą być zapieczętowane. Typ w innym składniku środowisko wykonawcze systemu Windows nie może dziedziczyć z nich. Jeśli chcesz zapewnić zachowanie polimorficzne w składniku, możesz utworzyć interfejs i zaimplementować go w typach polimorficznych.

- Wszystkie typy parametrów i zwracanych typów publicznych w składniku muszą być środowisko wykonawcze systemu Windows typy (w tym typy środowisko wykonawcze systemu Windows zdefiniowane przez składnik).

Poniższe sekcje zawierają przykłady typowych scenariuszy.

### <a name="application-logic-for-a-windows-8x-store-app-with-javascript"></a>Logika aplikacji dla aplikacji ze sklepu Windows 8. x z obsługą języka JavaScript

Podczas tworzenia aplikacji ze sklepu Windows 8. x dla systemu Windows za pomocą języka JavaScript może się okazać, że niektóre części logiki aplikacji działają lepiej w kodzie zarządzanym lub są łatwiejsze do opracowania. Język JavaScript nie może używać bibliotek klas .NET Framework bezpośrednio, ale można utworzyć bibliotekę klas a. Plik WinMD. W tym scenariuszu składnik środowisko wykonawcze systemu Windows jest integralną częścią aplikacji, więc nie ma sensu udostępnienia atrybutów wersji.

### <a name="reusable-windows-8x-store-ui-controls"></a>Kontrolki interfejsu użytkownika do sklepu Windows 8. x wielokrotnego użytku

Zestaw powiązanych kontrolek interfejsu użytkownika można spakować w składniku środowisko wykonawcze systemu Windows wielokrotnego użytku. Składnik może być sprzedawany samodzielnie lub używany jako element w tworzonych aplikacjach. W tym scenariuszu warto użyć atrybutu środowisko wykonawcze systemu Windows, <xref:Windows.Foundation.Metadata.VersionAttribute> Aby zwiększyć zgodność.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logika aplikacji wielokrotnego użytku z istniejących aplikacji .NET Framework

Kod zarządzany można spakować z istniejących aplikacji klasycznych jako składnik autonomicznej środowisko wykonawcze systemu Windows. Dzięki temu można używać składnika w aplikacjach systemu Windows 8. x ze sklepu utworzonego przy użyciu języka C++ lub JavaScript, a także do aplikacji ze sklepu Windows 8. x utworzonych przy użyciu języka C# lub Visual Basic. Obsługa wersji jest opcją, jeśli istnieje wiele scenariuszy ponownego użycia kodu.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Omówienie programu .NET dla aplikacji do sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Zawiera opis typów .NET Framework i członków, których można użyć do tworzenia aplikacji do sklepu Windows 8. x i RuntimeComponents systemu Windows. (W centrum deweloperów systemu Windows).|
|[Plan dla aplikacji ze sklepu Windows przy użyciu języka C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Udostępnia kluczowe zasoby ułatwiające rozpoczęcie opracowywania aplikacji ze sklepu Windows 8. x przy użyciu języka C# lub Visual Basic, w tym wiele tematów szybkiego startu, wytycznych i najlepszych rozwiązań. (W centrum deweloperów systemu Windows).|
|[Jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Udostępnia kluczowe zasoby ułatwiające rozpoczęcie opracowywania aplikacji ze sklepu Windows 8. x przy użyciu języka C# lub Visual Basic, w tym wiele tematów szybkiego startu, wytycznych i najlepszych rozwiązań. (W centrum deweloperów systemu Windows).|
|[Tworzenie składników środowisko wykonawcze systemu Windows w językach C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|Opisuje sposób tworzenia składnika środowisko wykonawcze systemu Windows przy użyciu .NET Framework. wyjaśnia, jak używać go jako części aplikacji ze sklepu Windows 8. x skompilowanego dla systemu Windows za pomocą języka JavaScript, i opisuje sposób debugowania kombinacji w programie Visual Studio. (W centrum deweloperów systemu Windows).|
|[Informacje środowisko wykonawcze systemu Windows](/uwp/api/)|Dokumentacja referencyjna środowisko wykonawcze systemu Windows. (W centrum deweloperów systemu Windows).|
|[Przekazywanie identyfikatora URI do środowiska wykonawczego systemu Windows](passing-a-uri-to-the-windows-runtime.md)|W tym artykule opisano problem, który może wystąpić w przypadku przekazania identyfikatora URI z kodu zarządzanego do środowisko wykonawcze systemu Windows i sposobu ich unikania.|
