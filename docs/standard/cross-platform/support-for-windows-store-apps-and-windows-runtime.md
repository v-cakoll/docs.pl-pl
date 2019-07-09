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
ms.openlocfilehash: c49e9a5c4b8785704f8c4cbd1c9b7af10dc0c689
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661784"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows

.NET Framework 4.5 obsługuje wiele scenariuszy programowania oprogramowania za pomocą środowiska wykonawczego Windows. Te scenariusze można podzielić na trzy kategorie:

- Tworzenie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu XAML kontrolki, zgodnie z opisem w [plan for Windows Store apps przy użyciu języka C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), i [Omówienie aplikacji .NET dla Windows Store ](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).

- Tworzenie biblioteki klas do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji utworzonych za pomocą programu .NET Framework.

- Tworzenie składników środowiska wykonawczego Windows, w jednym pakiecie w. Pliki WinMD, które mogą być używane przez każdy język programowania, który obsługuje środowisko wykonawcze Windows. Na przykład zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

W tym temacie opisano obsługę programu .NET Framework oferuje dla wszystkich trzech kategorii i opisano scenariusze dla składników środowiska wykonawczego Windows. Pierwsza sekcja zawiera podstawowe informacje na temat relacji między .NET Framework i środowiska wykonawczego Windows oraz informacje o niektórych oddities, które mogą wystąpić w systemie pomocy i środowiska IDE. [Druga sekcja](#WindowsRuntimeComponents) omawia scenariusze dotyczące tworzenia składników środowiska wykonawczego Windows.

## <a name="the-basics"></a>Podstawowe informacje

Program .NET Framework obsługuje trzy rozwoju wymienione wcześniej, zapewniając [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], a dzięki obsłudze środowisko wykonawcze Windows.

- [Obszary nazw .NET framework i środowiska wykonawczego Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)#net-framework-and-windows-runtime-namespaces) zapewnia ujednolicony widok biblioteki klas .NET Framework i zawierają tylko typy i elementy członkowskie, można użyć do utworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i składników środowiska wykonawczego Windows.

  - Jeśli używasz programu Visual Studio (Visual Studio 2012 lub nowszy) do tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacja lub składnik środowiska wykonawczego Windows, zbiór zestawów odwołań zapewnia, zostanie wyświetlony tylko odpowiednie typy i elementy członkowskie.

  - Ten ujednolicony zestaw API jest uproszczone dalsze poprzez usunięcie funkcji zduplikowane w ramach programu .NET Framework lub zduplikować, środowisko uruchomieniowe Windows funkcji. Na przykład zawiera ogólny wersje typy kolekcji i wyeliminowania model obiektu dokumentu XML na rzecz API XML środowiska wykonawczego Windows ustaw.

  - Funkcje, które po prostu umieszczają w otoce interfejsu API w systemu operacyjnego są również usuwane, ponieważ środowisko wykonawcze Windows jest łatwy do wywoływania z kodu zarządzanego.

  Aby dowiedzieć się więcej o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], zobacz [Omówienie aplikacji .NET dla Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)). Aby dowiedzieć się o procesie wybór interfejsu API, zobacz [platformy .NET dla aplikacji w stylu Metro](https://devblogs.microsoft.com/dotnet/net-for-metro-style-apps/) wpis w blogu .NET.

- [Windows Runtime](/uwp/api/) zawiera elementy interfejsu użytkownika do kompilowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i zapewnia dostęp do funkcji systemu operacyjnego. Podobnie jak .NET Framework, środowisko wykonawcze Windows ma metadanych, który umożliwia C# i Kompilatory języka Visual Basic do korzystania ze środowiska wykonawczego Windows w sposób korzystają z programu .NET Framework class bibliotek. .NET Framework ułatwia korzystania ze środowiska wykonawczego Windows, ukrywając pewne różnice:

  - Pewne różnice w programowaniu wzorce między .NET Framework i środowiska wykonawczego Windows, takich jak wzorzec Dodawanie i usuwanie programów obsługi zdarzeń, są ukryte. Po prostu użyć wzorca .NET Framework.

  - Pewne różnice w często używanych typów (na przykład, typy pierwotne i kolekcji) są ukryte. Po prostu używasz typ .NET Framework, zgodnie z opisem w [różnic, są widoczne w środowisku IDE](#DifferencesVisibleInIDE), w dalszej części tego artykułu.

W większości przypadków, obsługa środowiska uruchomieniowego Windows .NET Framework jest niewidoczne. W następnej sekcji omówiono niektóre jawnego różnice między kodem zarządzanym i środowiska wykonawczego Windows.

<a name="AboutReferenceDocumentation"></a>

### <a name="the-net-framework-and-the-windows-runtime-reference-documentation"></a>.NET Framework i Windows Runtime dokumentacji

Środowisko wykonawcze Windows i zestawów dokumentacji .NET Framework są oddzielone. Jeśli użytkownik naciśnie klawisz F1, aby wyświetlić Pomoc dotyczącą typu lub elementu członkowskiego, jest wyświetlany dokumentacji z odpowiedniego zestawu. Jednak podczas przeglądania [dokumentacja środowiska uruchomieniowego Windows](/uwp/api/) mogą wystąpić przykładów, które wydają się puzzling:

- Tematy, takie jak <xref:Windows.Foundation.Collections.IIterable%601> interfejsu nie mają Składnia deklaracji dla języka Visual Basic lub C#. Zamiast tego notatkę pojawia się powyżej w sekcji składni (w tym przypadku ".NET: Ten interfejs jest wyświetlany jako System.Collections.Generic.IEnumerable\<T > "). Jest to spowodowane programu .NET Framework i środowiska wykonawczego Windows zapewniają podobne funkcje za pomocą różnych interfejsów. Ponadto istnieją różnice w zachowaniu: `IIterable` ma `First` zamiast metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metodę, aby zwrócić modułu wyliczającego. Zamiast wymuszania wielokrotnego się inny sposób wykonywania typowych zadań, program .NET Framework obsługuje środowisko wykonawcze Windows, wprowadzając zarządzanego kodu są wyświetlane, aby użyć typu, który znasz. Nie będziesz widzieć `IIterable` interfejsu w środowisku IDE i dlatego jedynym sposobem, którymi spotkasz w dokumentacji środowiska wykonawczego Windows, przeglądając tą dokumentacją bezpośrednio.

- <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> Dokumentacji przedstawiono ściśle powiązanych problemu: Jego typy parametrów wydają się być różne w różnych językach. W języku C# i Visual Basic, są typami parametrów <xref:System.String?displayProperty=nameWithType> i <xref:System.Uri?displayProperty=nameWithType>. To kolejna zmiana, ponieważ programu .NET Framework ma swój własny `String` i `Uri` typów, a dla takich często używanych typów nie ma sensu zmusić użytkowników .NET Framework, aby dowiedzieć się więcej w inny sposób radzenia sobie. W środowisku IDE programu .NET Framework ukrywa odpowiednich typów środowiska wykonawczego Windows.

- W niektórych przypadkach takich jak <xref:Windows.UI.Xaml.GridLength> struktury, program .NET Framework zawiera typ o tej samej nazwie, ale więcej funkcji. Na przykład zestaw tematów Konstruktor i właściwości są skojarzone z `GridLength`, ale mają tylko w przypadku języka Visual Basic i C# bloki składni elementy członkowskie nie są dostępne tylko w kodzie zarządzanym. W środowisku uruchomieniowym Windows struktury mają tylko pola. Struktura środowiska uruchomieniowego Windows wymaga klasę pomocy <xref:Windows.UI.Xaml.GridLengthHelper>w celu zapewnienia równoważne funkcje. Nie będziesz widzieć, klasa pomocy w środowisku IDE podczas pisania kodu zarządzanego.

- W IDE, typów środowiska wykonawczego Windows wydają się pochodzić od <xref:System.Object?displayProperty=nameWithType>. Wydają się mieć członków dziedziczonych po elemencie <xref:System.Object>, takich jak <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Te elementy członkowskie działają tak samo jak w przypadku typów faktycznie dziedziczonych z <xref:System.Object>, oraz typów środowiska wykonawczego Windows mogą być rzutowane na <xref:System.Object>. Ta funkcja jest częścią wsparcia dla środowiska uruchomieniowego Windows .NET Framework. Jednak jeśli przeglądasz typów w dokumentacji środowiska wykonawczego Windows, są wyświetlane żadnych takich elementów członkowskich. W dokumentacji dotyczącej tych jawnego dziedziczone elementy członkowskie są dostarczane przez <xref:System.Object?displayProperty=nameWithType> dokumentację referencyjną.

<a name="DifferencesVisibleInIDE"></a>

### <a name="differences-that-are-visible-in-the-ide"></a>Różnice, które są widoczne w środowisku IDE

Bardziej zaawansowane scenariusze programowania, na przykład za pomocą składnika wykonawczego Windows napisanych w C# zapewnienie logikę aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację dla Windows przy użyciu języka JavaScript, takie różnice są widoczne w IDE, a także jak w dokumentacja. Gdy składnik zwraca `IDictionary<int, string>` JavaScript i możesz przyjrzeć się im w debugerze JavaScript, zobaczysz metody `IMap<int, string>` ponieważ JavaScript wykorzystuje typ środowiska uruchomieniowego Windows. Niektóre powszechnie używane w poniższej tabeli przedstawiono typy, które pojawiają się w różny sposób w dwóch języków kolekcji:

|Typ środowiska uruchomieniowego Windows|Odpowiedni typ .NET Framework|
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

W środowisku uruchomieniowym Windows `IMap<K, V>` i `IMapView<K, V>` są postanowiliśmy przy użyciu `IKeyValuePair`. Podczas przekazywania ich do zarządzanego kodu są wyświetlane jako `IDictionary<TKey, TValue>` i `IReadOnlyDictionary<TKey, TValue>`, więc naturalnie możesz użyć `System.Collections.Generic.KeyValuePair<TKey, TValue>` wyliczyć je.

Interfejsy sposób pojawiają się w sposób typy, które implementują te interfejsy są wyświetlane ma wpływ kodu zarządzanego. Na przykład `PropertySet` klasy implementuje `IMap<K, V>`, która jest wyświetlana w zarządzanym kodzie jako `IDictionary<TKey, TValue>`. `PropertySet` pojawi się tak, jakby zaimplementowane `IDictionary<TKey, TValue>` zamiast `IMap<K, V>`, więc w kodzie zarządzanym wydaje się być `Add` metody, która zachowuje się jak `Add` metody słowników .NET Framework. Ponieważ prawdopodobnie nie masz `Insert` metody.

Aby uzyskać więcej informacji na temat tworzenia składnika wykonawczego Windows i wskazówki, który pokazuje, jak używać tych składników za pomocą języka JavaScript przy użyciu programu .NET Framework, zobacz [Tworzenie składników środowiska wykonawczego Windows w C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic).

### <a name="primitive-types"></a>Typy pierwotne

Aby włączyć fizyczne użycie środowiska wykonawczego Windows w kodzie zarządzanym, pierwotnych typów programu .NET Framework są wyświetlane zamiast typów pierwotnych środowiska wykonawczego Windows w kodzie. W .NET Framework, takich jak typy pierwotne `Int32` struktury mają wiele użytecznych właściwości i metod, takich jak `Int32.TryParse` metody. Z drugiej strony typy pierwotne i struktur w środowisku uruchomieniowym Windows mają tylko pola. Gdy używasz podstawowych w kodzie zarządzanym wydają się być typów programu .NET Framework, a następnie można użyć właściwości i metody typów programu .NET Framework w zwykły sposób. Poniższa lista zawiera podsumowanie:

- Dla elementów podstawowych Windows Runtime `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (kolekcji niezmienialnych znaków Unicode), `Enum`, `UInt32`, `UInt64`, i `Guid`, używając typu o nazwie takiej samej nazwie w `System` przestrzeni nazw.

- Aby uzyskać `UInt8`, użyj `System.Byte`.

- Aby uzyskać `Char16`, użyj `System.Char`.

- Aby uzyskać `IInspectable` interfejsu, należy użyć `System.Object`.

- Aby uzyskać `HRESULT`, użyj struktury za pomocą jednego `System.Int32` elementu członkowskiego.

W przypadku typów interfejsu, jedyną sytuacją, może zostać wyświetlony jest dowód taka reprezentacja, gdy projekt .NET Framework jest składnik środowiska wykonawczego Windows, który jest używany przez [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanej przy użyciu języka JavaScript.

Inne podstawowe, powszechnie używanym typów środowiska wykonawczego Windows, które pojawiają się w kod zarządzany, ponieważ ich odpowiedników .NET Framework zawiera `Windows.Foundation.DateTime` struktury, która jest wyświetlana w zarządzanym kodzie jako <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i `Windows.Foundation.TimeSpan` strukturę, która pojawia się jako <xref:System.TimeSpan?displayProperty=nameWithType> struktury.

### <a name="other-differences"></a>Inne różnice

W niektórych przypadkach fakt, że typów programu .NET Framework są wyświetlane w kodzie zamiast typów środowiska wykonawczego Windows wymaga akcji ze strony użytkownika. Na przykład <xref:Windows.Foundation.Uri?displayProperty=nameWithType> klasa jest wyświetlany jako <xref:System.Uri?displayProperty=nameWithType> w kodzie .NET Framework. <xref:System.Uri?displayProperty=nameWithType> zezwala na względny identyfikator URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> wymaga bezwzględnego identyfikatora URI. W związku z tym przy identyfikatora URI jest przekazywane do metody środowiska wykonawczego Windows, należy się upewnić, że jest bezwzględna. (Zobacz [przekazywanie adresu URI do środowiska wykonawczego Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)

<a name="WindowsRuntimeComponents"></a>

## <a name="scenarios-for-developing-windows-runtime-components"></a>Scenariusze dotyczące tworzenia składników środowiska wykonawczego Windows

Scenariusze, które są obsługiwane w przypadku zarządzanych składników środowiska wykonawczego Windows zależą od następujących zasad ogólnych:

- Składników środowiska wykonawczego Windows, które zostały utworzone przy użyciu programu .NET Framework mają nie jawnego różnice z innych Runtimelibraries Windows. Na przykład w przypadku ponownego zastosowania natywnych składnika wykonawczego Windows przy użyciu kodu zarządzanego, dwa składniki są nierozróżnialne wypukłymi. Fakt, że składnik są zapisywane w kodzie zarządzanym jest niewidoczne dla kodu, który korzysta z niego, nawet jeśli kod jest sam kod zarządzany. Jednak wewnętrznie, składnik jest true kodu zarządzanego i jest uruchamiany w środowisku uruchomieniowym języka wspólnego (CLR).

- Składników może zawierać typy, które implementują logikę aplikacji, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] interfejsu użytkownika formantów i / lub.

  > [!NOTE]
  > Jest dobrą praktyką, aby oddzielić elementy interfejsu użytkownika od logiki aplikacji. Ponadto nie można użyć [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] interfejsu użytkownika kontrolki w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanej dla Windows przy użyciu języka JavaScript i HTML.

- Składnik może być projektu w ramach rozwiązania Visual Studio dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację lub składnik wielokrotnego użytku, można dodać wiele rozwiązań.

  > [!NOTE]
  > Jeśli składnik będzie używana tylko w przypadku C# lub Visual Basic, nie ma powodu się składnika wykonawczego Windows. Jeśli ustawisz zwykłej biblioteki klas .NET Framework zamiast tego, nie trzeba ograniczyć jej publicznych powierzchni interfejsu API do typów środowiska wykonawczego Windows.

- Za pomocą środowiska uruchomieniowego Windows mogą wersje składników wielokrotnego użytku <xref:Windows.Foundation.Metadata.VersionAttribute> atrybut do identyfikowania, jakie typy (i członków, którzy w ramach danego typu) zostały dodane w różnych wersjach.

- Typy w składniku może pochodzić z typami środowiska wykonawczego Windows. Formanty może pochodzić z typu pierwotnego kontrola <xref:Windows.UI.Xaml.Controls.Primitives> przestrzeni nazw lub od bardziej zakończy formantów takich jak <xref:Windows.UI.Xaml.Controls.Button>.

  > [!IMPORTANT]
  > Począwszy od [!INCLUDE[win8](../../../includes/win8-md.md)] i .NET Framework 4.5, wszystkie typy publiczne w zarządzanego składnika środowiska wykonawczego Windows musi być zapieczętowany. Typ w innym składniku Windows Runtime nie może pochodzić z nich. Jeśli chcesz zapewnić zachowanie polimorficzne w składniku, można utworzyć interfejsu i wdrożenie go w typach polimorficznych.

- Wszystkie typy parametrów i zwrotu w publicznych typach w składniku należy typów środowiska wykonawczego Windows (w tym typów środowiska wykonawczego Windows, które definiuje składnika).

Poniższe sekcje zawierają przykłady typowych scenariuszy.

### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logika aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji za pomocą języka JavaScript

Podczas opracowywania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla Windows przy użyciu języka JavaScript, możesz znaleźć niektórych części logiki aplikacji działać lepiej w kodzie zarządzanym lub są łatwiejsze do opracowywania. Język JavaScript nie można użyć biblioteki klas .NET Framework bezpośrednio, ale istnieje możliwość bibliotekę klas. Plik WinMD. W tym scenariuszu składnik środowiska wykonawczego Windows jest integralną częścią aplikacji, więc nie ma sensu potrzeby udostępniania atrybutów wersji.

### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Wielokrotnego użytku, do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] kontrolek interfejsu użytkownika

Można spakować zbiór pokrewnych formantów interfejsu użytkownika w wielokrotnego użytku składnika wykonawczego Windows. Ten składnik można wprowadzać na rynek samodzielnie lub jako element w tworzonych przez Ciebie aplikacji. W tym scenariuszu, dobrym pomysłem będzie korzystania ze środowiska wykonawczego Windows <xref:Windows.Foundation.Metadata.VersionAttribute> atrybutu, aby zwiększyć zgodność.

### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logika aplikacji wielokrotnego użytku z istniejących aplikacji programu .NET Framework

Można spakować kodu zarządzanego z istniejących aplikacji pulpitu, jako autonomiczny składnik środowiska wykonawczego Windows. Dzięki temu można używać składnika w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje utworzone przy użyciu języka C++ lub JavaScript, jak również w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje utworzone przy użyciu języka C# lub Visual Basic. Przechowywanie wersji jest opcją w przypadku scenariuszy z wieloma ponownego użycia kodu.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Omówienie aplikacji .NET dla Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))|Zawiera opis typów programu .NET Framework i elementów członkowskich, które umożliwia tworzenie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Windows RuntimeComponents i aplikacji. (W Centrum deweloperów Windows.)|
|[Harmonogram działania dla aplikacji Windows Store przy użyciu języka C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Zawiera kluczowych zasobów ułatwiających rozpoczęcie pracy tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka C# lub Visual Basic, w tym wiele tematów w przewodniku Szybki Start, wskazówki i najlepsze rozwiązania. (W Centrum deweloperów Windows.)|
|[Jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Zawiera kluczowych zasobów ułatwiających rozpoczęcie pracy tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka C# lub Visual Basic, w tym wiele tematów w przewodniku Szybki Start, wskazówki i najlepsze rozwiązania. (W Centrum deweloperów Windows.)|
|[Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](/windows/uwp/winrt-components/creating-windows-runtime-components-in-csharp-and-visual-basic)|W tym artykule opisano sposób tworzenia składnika wykonawczego Windows przy użyciu programu .NET Framework, wyjaśnia, jak używać go jako część [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowany dla Windows przy użyciu języka JavaScript, a w tym artykule opisano sposób debugowania w połączeniu z programem Visual Studio. (W Centrum deweloperów Windows.)|
|[Dokumentacja środowiska uruchomieniowego Windows](/uwp/api/)|Dokumentacja referencyjna środowiska wykonawczego Windows. (W Centrum deweloperów Windows.)|
|[Przekazywanie identyfikatora URI do środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|W tym artykule opisano problem, który może wystąpić, jeśli identyfikator URI z kodu zarządzanego do środowiska wykonawczego Windows oraz jak uniknąć tego błędu.|
