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
ms.openlocfilehash: 5f587d45f046a3f7b8556052df63220f9f1cac42
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672724"
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Obsługuje wiele scenariuszy programowania oprogramowania za pomocą [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Te scenariusze można podzielić na trzy kategorie:  
  
-   Tworzenie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu XAML kontrolki, zgodnie z opisem w [plan for Windows Store apps przy użyciu języka C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10)), [jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10)), i [Omówienie aplikacji .NET dla Windows Store ](https://msdn.microsoft.com/library/windows/apps/br230302%28v=VS.110%29.aspx).  
  
-   Tworzenie biblioteki klas do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji utworzonych za pomocą programu .NET Framework.  
  
-   Tworzenie [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników, w jednym pakiecie w. Pliki WinMD, które mogą być używane przez każdy język programowania, który obsługuje [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Na przykład zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301(v=VS.110).aspx).  
  
 W tym temacie opisano obsługę programu .NET Framework oferuje dla wszystkich trzech kategorii, która opisuje scenariusze związane z [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników. Pierwsza sekcja obejmuje podstawowe informacje na temat relacji między .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)]i opisano niektóre oddities mogą wystąpić w systemie pomocy i środowiska IDE. [Druga sekcja](#WindowsRuntimeComponents) omawia scenariusze tworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników.  
  
## <a name="the-basics"></a>Podstawowe informacje  
 Program .NET Framework obsługuje trzy rozwoju wymienione wcześniej, zapewniając [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], a dzięki obsłudze [!INCLUDE[wrt](../../../includes/wrt-md.md)] sam.  
  
-   [Aplikacje .NET for Windows Store](https://msdn.microsoft.com/library/windows/apps/br230232(v=vs.110).aspx) zapewnia ujednolicony widok biblioteki klas .NET Framework i zawierają tylko typy i elementy członkowskie, można użyć do utworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników.  
  
    -   Jeśli używasz programu Visual Studio ([!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] lub nowszej) do tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji lub [!INCLUDE[wrt](../../../includes/wrt-md.md)] zapewnia zbiór zestawów odwołań składnika, zostanie wyświetlony tylko odpowiednie typy i elementy członkowskie.  
  
    -   Ten ujednolicony zestaw API jest uproszczone przez usunięcie zduplikowane w ramach programu .NET Framework lub zduplikować, funkcje [!INCLUDE[wrt](../../../includes/wrt-md.md)] funkcji. Na przykład zawiera ogólny wersje typy kolekcji i zastąpiona ceną wyeliminowania XML document object model [!INCLUDE[wrt](../../../includes/wrt-md.md)] zestawu interfejsów API XML.  
  
    -   Funkcje, które po prostu umieszczają w otoce interfejsu API w systemu operacyjnego są również usuwane, ponieważ [!INCLUDE[wrt](../../../includes/wrt-md.md)] jest łatwa do wywoływania z kodu zarządzanego.  
  
     Aby dowiedzieć się więcej o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], zobacz [Omówienie aplikacji .NET dla Windows Store](https://msdn.microsoft.com/library/windows/apps/br230302(v=VS.110).aspx). Aby dowiedzieć się o procesie wybór interfejsu API, zobacz [platformy .NET dla aplikacji w stylu Metro](https://blogs.msdn.microsoft.com/dotnet/2012/04/17/net-for-metro-style-apps/) wpis w blogu .NET.  
  
-   [Windows Runtime](/uwp/api/) zawiera elementy interfejsu użytkownika do kompilowania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i zapewnia dostęp do funkcji systemu operacyjnego. .NET Framework, takich jak [!INCLUDE[wrt](../../../includes/wrt-md.md)] ma metadane, umożliwiająca Kompilatory języka C# i Visual Basic można użyć [!INCLUDE[wrt](../../../includes/wrt-md.md)] sposób korzystają z programu .NET Framework klasy biblioteki. .NET Framework ułatwia użyj [!INCLUDE[wrt](../../../includes/wrt-md.md)] poprzez ukrywanie pewne różnice:  
  
    -   Pewne różnice w programowaniu wzorce między .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)], takich jak wzorzec umożliwiających dodawanie i usuwanie programów obsługi zdarzeń są ukryte. Po prostu użyć wzorca .NET Framework.  
  
    -   Pewne różnice w często używanych typów (na przykład, typy pierwotne i kolekcji) są ukryte. Po prostu używasz typ .NET Framework, zgodnie z opisem w [różnic, są widoczne w środowisku IDE](#DifferencesVisibleInIDE), w dalszej części tego artykułu.  
  
 Większość czasu Obsługa programu .NET Framework dla [!INCLUDE[wrt](../../../includes/wrt-md.md)] jest przezroczysty. W następnej sekcji omówiono niektóre jawnego różnice między kodem zarządzanym i [!INCLUDE[wrt](../../../includes/wrt-md.md)].  
  
<a name="AboutReferenceDocumentation"></a>   
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>.NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)] dokumentacji  
 Środowisko wykonawcze Windows i zestawów dokumentacji .NET Framework są oddzielone. Jeśli użytkownik naciśnie klawisz F1, aby wyświetlić Pomoc dotyczącą typu lub elementu członkowskiego, jest wyświetlany dokumentacji z odpowiedniego zestawu. Jednak podczas przeglądania [dokumentacja środowiska uruchomieniowego Windows](/uwp/api/) mogą wystąpić przykładów, które wydają się puzzling:  
  
-   Tematy, takie jak <xref:Windows.Foundation.Collections.IIterable%601> interfejsu nie mają Składnia deklaracji dla języka Visual Basic lub C#. Zamiast tego notatkę pojawia się powyżej w sekcji składni (w tym przypadku ".NET: ten interfejs jest wyświetlany jako System.Collections.Generic.IEnumerable\<T >"). Jest to spowodowane programu .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)] zapewniają podobne funkcje za pomocą różnych interfejsów. Ponadto istnieją różnice w zachowaniu: `IIterable` ma `First` zamiast metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metodę, aby zwrócić modułu wyliczającego. Zamiast wymuszania wielokrotnego się inny sposób wykonywania typowych zadań, program .NET Framework obsługuje [!INCLUDE[wrt](../../../includes/wrt-md.md)] , wprowadzając zarządzanego kodu są wyświetlane, aby użyć typu, kiedy znasz już. Nie będziesz widzieć `IIterable` interfejsu w IDE, a zatem jedynym sposobem którymi spotkasz się go w [!INCLUDE[wrt](../../../includes/wrt-md.md)] dokumentacja polega na przeglądaniu tą dokumentacją bezpośrednio.  
  
-   <xref:Windows.Web.Syndication.SyndicationFeed.%23ctor(System.String,System.String,Windows.Foundation.Uri)> Dokumentacji ilustruje problem ściśle powiązanych: jego typy parametrów wydaje się być różne dla różnych języków. W języku C# i Visual Basic, są typami parametrów <xref:System.String?displayProperty=nameWithType> i <xref:System.Uri?displayProperty=nameWithType>. To kolejna zmiana, ponieważ programu .NET Framework ma swój własny `String` i `Uri` typów, a dla takich często używanych typów nie ma sensu zmusić użytkowników .NET Framework, aby dowiedzieć się więcej w inny sposób radzenia sobie. W środowisku IDE programu .NET Framework ukrywa odpowiednich [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów.  
  
-   W niektórych przypadkach takich jak <xref:Windows.UI.Xaml.GridLength> struktury, program .NET Framework zawiera typ o tej samej nazwie, ale więcej funkcji. Na przykład zestaw tematów Konstruktor i właściwości są skojarzone z `GridLength`, ale mają tylko w przypadku języka Visual Basic i C# bloki składni elementy członkowskie nie są dostępne tylko w kodzie zarządzanym. W [!INCLUDE[wrt](../../../includes/wrt-md.md)], struktury mają tylko pola. [!INCLUDE[wrt](../../../includes/wrt-md.md)] Struktury wymaga klasę pomocy <xref:Windows.UI.Xaml.GridLengthHelper>w celu zapewnienia równoważne funkcje. Nie będziesz widzieć, klasa pomocy w środowisku IDE podczas pisania kodu zarządzanego.  
  
-   W środowisku IDE programu [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy są wyświetlane do wyprowadzenia z <xref:System.Object?displayProperty=nameWithType>. Wydają się mieć członków dziedziczonych po elemencie <xref:System.Object>, takich jak <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Te elementy członkowskie działają tak samo jak w przypadku typów faktycznie dziedziczonych z <xref:System.Object>, i [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy mogą być rzutowane na <xref:System.Object>. Jest to część obsługi, która oferuje funkcje programu .NET Framework [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Jednak jeśli przeglądasz typów w [!INCLUDE[wrt](../../../includes/wrt-md.md)] dokumentacji, są wyświetlane nie takich elementów członkowskich. W dokumentacji dotyczącej tych jawnego dziedziczone elementy członkowskie są dostarczane przez <xref:System.Object?displayProperty=nameWithType> dokumentację referencyjną.  
  
<a name="DifferencesVisibleInIDE"></a>   
### <a name="differences-that-are-visible-in-the-ide"></a>Różnice, które są widoczne w środowisku IDE  
 Bardziej zaawansowane scenariusze programowania, takich jak przy użyciu [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników napisanych w języku C#, aby zapewnić logikę aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację dla Windows przy użyciu języka JavaScript, takie różnice są widoczne w IDE, jak również tak jak w dokumentacji. Gdy składnik zwraca `IDictionary<int, string>` JavaScript i możesz przyjrzeć się im w debugerze JavaScript, zobaczysz metody `IMap<int, string>` ponieważ JavaScript wykorzystuje [!INCLUDE[wrt](../../../includes/wrt-md.md)] typu. Niektóre powszechnie używane w poniższej tabeli przedstawiono typy, które pojawiają się w różny sposób w dwóch języków kolekcji:  
  
|[!INCLUDE[wrt](../../../includes/wrt-md.md)] Typ|Odpowiedni typ .NET Framework|  
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
  
 W [!INCLUDE[wrt](../../../includes/wrt-md.md)], `IMap<K, V>` i `IMapView<K, V>` są postanowiliśmy przy użyciu `IKeyValuePair`. Podczas przekazywania ich do zarządzanego kodu są wyświetlane jako `IDictionary<TKey, TValue>` i `IReadOnlyDictionary<TKey, TValue>`, więc naturalnie możesz użyć `System.Collections.Generic.KeyValuePair<TKey, TValue>` wyliczyć je.  
  
 Interfejsy sposób pojawiają się w sposób typy, które implementują te interfejsy są wyświetlane ma wpływ kodu zarządzanego. Na przykład `PropertySet` klasy implementuje `IMap<K, V>`, która jest wyświetlana w zarządzanym kodzie jako `IDictionary<TKey, TValue>`. `PropertySet` pojawi się tak, jakby zaimplementowane `IDictionary<TKey, TValue>` zamiast `IMap<K, V>`, więc w kodzie zarządzanym wydaje się być `Add` metody, która zachowuje się jak `Add` metody słowników .NET Framework. Ponieważ prawdopodobnie nie masz `Insert` metody.  
  
 Aby uzyskać więcej informacji o korzystaniu z programu .NET Framework do tworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika i wskazówki, który pokazuje, jak używać tych składników za pomocą języka JavaScript, zobacz [Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301%28v=VS.110%29.aspx).  
  
### <a name="primitive-types"></a>Typy pierwotne  
 Umożliwia użycie fizycznych [!INCLUDE[wrt](../../../includes/wrt-md.md)] pierwotnych typów programu .NET Framework są wyświetlane w kodzie zarządzanym zamiast [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów pierwotnych w kodzie. W .NET Framework, takich jak typy pierwotne `Int32` struktury mają wiele użytecznych właściwości i metod, takich jak `Int32.TryParse` metody. Z kolei podstawowego typy i struktury w [!INCLUDE[wrt](../../../includes/wrt-md.md)] mają tylko pola. Gdy używasz podstawowych w kodzie zarządzanym wydają się być typów programu .NET Framework, a następnie można użyć właściwości i metody typów programu .NET Framework w zwykły sposób. Poniższa lista zawiera podsumowanie:  
  
-   Aby uzyskać [!INCLUDE[wrt](../../../includes/wrt-md.md)] podstawowych `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (kolekcji niezmienialnych znaków Unicode), `Enum`, `UInt32`, `UInt64`, i `Guid`, używając typu o nazwie takiej samej nazwie w `System` przestrzeni nazw.  
  
-   Aby uzyskać `UInt8`, użyj `System.Byte`.  
  
-   Aby uzyskać `Char16`, użyj `System.Char`.  
  
-   Aby uzyskać `IInspectable` interfejsu, należy użyć `System.Object`.  
  
-   Aby uzyskać `HRESULT`, użyj struktury za pomocą jednego `System.Int32` elementu członkowskiego.  
  
 Zgodnie z typów interfejsów, jedyną sytuacją, może zostać wyświetlony jest dowód taka reprezentacja, gdy projekt .NET Framework jest [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnik, który jest używany przez [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanej przy użyciu języka JavaScript.  
  
 Inne podstawowe najczęściej używanych [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy, które pojawiają się w kod zarządzany, ponieważ ich odpowiedników .NET Framework zawiera `Windows.Foundation.DateTime` struktury, która jest wyświetlana w zarządzanym kodzie jako <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i `Windows.Foundation.TimeSpan` strukturę, która pojawia się jako <xref:System.TimeSpan?displayProperty=nameWithType> struktury.  
  
### <a name="other-differences"></a>Inne różnice  
 W niektórych przypadkach fakt, że typów programu .NET Framework są wyświetlane w kodzie zamiast [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy wymaga akcji ze strony użytkownika. Na przykład <xref:Windows.Foundation.Uri?displayProperty=nameWithType> klasa jest wyświetlany jako <xref:System.Uri?displayProperty=nameWithType> w kodzie .NET Framework. <xref:System.Uri?displayProperty=nameWithType> zezwala na względny identyfikator URI, ale <xref:Windows.Foundation.Uri?displayProperty=nameWithType> wymaga bezwzględnego identyfikatora URI. W związku z tym, podczas przekazywania identyfikatora URI do [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody, należy upewnić się, że jest bezwzględna. (Zobacz [przekazywanie adresu URI do środowiska wykonawczego Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)  
  
<a name="WindowsRuntimeComponents"></a>   
## <a name="scenarios-for-developing-windows-runtime-components"></a>Scenariusze dotyczące tworzenia składników środowiska wykonawczego Windows  
 Scenariusze, które są obsługiwane w przypadku zarządzanych [!INCLUDE[wrt](../../../includes/wrt-md.md)] składniki są zależne od następujących zasad ogólnych:  
  
-   [!INCLUDE[wrt](../../../includes/wrt-md.md)] Składniki, które zostały utworzone przy użyciu programu .NET Framework mają nie jawnego różnice z innych [!INCLUDE[wrt](../../../includes/wrt-md.md)]bibliotek. Na przykład w przypadku ponownego zaimplementowania macierzystej [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika przy użyciu kodu zarządzanego, dwa składniki są nierozróżnialne wypukłymi. Fakt, że składnik są zapisywane w kodzie zarządzanym jest niewidoczne dla kodu, który korzysta z niego, nawet jeśli kod jest sam kod zarządzany. Jednak wewnętrznie, składnik jest true kodu zarządzanego i jest uruchamiany w środowisku uruchomieniowym języka wspólnego (CLR).  
  
-   Składników może zawierać typy, które implementują logikę aplikacji, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] interfejsu użytkownika formantów i / lub.  
  
    > [!NOTE]
    >  Jest dobrą praktyką, aby oddzielić elementy interfejsu użytkownika od logiki aplikacji. Ponadto nie można użyć [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] interfejsu użytkownika kontrolki w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanej dla Windows przy użyciu języka JavaScript i HTML.  
  
-   Składnik może być projektu w ramach rozwiązania Visual Studio dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikację lub składnik wielokrotnego użytku, można dodać wiele rozwiązań.  
  
    > [!NOTE]
    >  Jeśli składnik będzie używany tylko w języku C# lub Visual Basic, nie ma powodu do ułatwiają [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Jeśli ustawisz zwykłej biblioteki klas .NET Framework zamiast tego, nie trzeba ograniczyć publicznych powierzchni interfejsu API, tak aby [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów.  
  
-   Można zwolnić wersje składników wielokrotnego użytku, za pomocą [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> atrybut do identyfikowania, jakie typy (i członków, którzy w ramach danego typu) zostały dodane w różnych wersjach.  
  
-   Typy w składniku mogą pochodzić od [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów. Formanty może pochodzić z typu pierwotnego kontrola <xref:Windows.UI.Xaml.Controls.Primitives> przestrzeni nazw lub od bardziej zakończy formantów takich jak <xref:Windows.UI.Xaml.Controls.Button>.  
  
    > [!IMPORTANT]
    >  Począwszy od [!INCLUDE[win8](../../../includes/win8-md.md)] i [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wszystkie typy publiczne w zarządzanej [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika musi być zapieczętowany. Typ w innym [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika nie może pochodzić z nich. Jeśli chcesz zapewnić zachowanie polimorficzne w składniku, można utworzyć interfejsu i wdrożenie go w typach polimorficznych.  
  
-   Wszystkie typy parametrów i zwrotu w publicznych typach w składniku muszą być [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy (włącznie z [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy, które definiuje składnika).  
  
 Poniższe sekcje zawierają przykłady typowych scenariuszy.  
  
### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logika aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji za pomocą języka JavaScript  
 Podczas opracowywania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla Windows przy użyciu języka JavaScript, możesz znaleźć niektórych części logiki aplikacji działać lepiej w kodzie zarządzanym lub są łatwiejsze do opracowywania. Język JavaScript nie można użyć biblioteki klas .NET Framework bezpośrednio, ale istnieje możliwość bibliotekę klas. Plik WinMD. W tym scenariuszu [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnik jest integralną częścią aplikacji, dzięki czemu nie ma sensu potrzeby udostępniania atrybutów wersji.  
  
### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Wielokrotnego użytku, do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] kontrolek interfejsu użytkownika  
 Można spakować zbiór pokrewnych formantów interfejsu użytkownika w wielokrotnego użytku, do [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Ten składnik można wprowadzać na rynek samodzielnie lub jako element w tworzonych przez Ciebie aplikacji. W tym scenariuszu, dobrym pomysłem będzie używać [!INCLUDE[wrt](../../../includes/wrt-md.md)] <xref:Windows.Foundation.Metadata.VersionAttribute> atrybutu, aby zwiększyć zgodność.  
  
### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Logika aplikacji wielokrotnego użytku z istniejących aplikacji programu .NET Framework  
 Można spakować kodu zarządzanego z istniejących aplikacji pulpitu, jako autonomiczny [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Dzięki temu można używać składnika w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje utworzone przy użyciu języka C++ lub JavaScript, jak również w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje utworzone przy użyciu języka C# lub Visual Basic. Przechowywanie wersji jest opcją w przypadku scenariuszy z wieloma ponownego użycia kodu.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Omówienie aplikacji .NET dla Windows Store](https://msdn.microsoft.com/library/windows/apps/br230302(v=VS.110).aspx)|Zawiera opis typów programu .NET Framework i elementów członkowskich, które umożliwia tworzenie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i [!INCLUDE[wrt](../../../includes/wrt-md.md)]składników. (W Centrum deweloperów Windows.)|  
|[Harmonogram działania dla aplikacji Windows Store przy użyciu języka C# lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/br229583(v=win.10))|Zawiera kluczowych zasobów ułatwiających rozpoczęcie pracy tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka C# lub Visual Basic, w tym wiele tematów w przewodniku Szybki Start, wskazówki i najlepsze rozwiązania. (W Centrum deweloperów Windows.)|  
|[Jak OT (XAML)](https://docs.microsoft.com/previous-versions/windows/apps/br229566(v=win.10))|Zawiera kluczowych zasobów ułatwiających rozpoczęcie pracy tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka C# lub Visual Basic, w tym wiele tematów w przewodniku Szybki Start, wskazówki i najlepsze rozwiązania. (W Centrum deweloperów Windows.)|  
|[Tworzenie składników środowiska wykonawczego Windows w języku C# i Visual Basic](https://msdn.microsoft.com/library/windows/apps/br230301%28v=VS.110%29.aspx)|W tym artykule opisano sposób tworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika za pomocą programu .NET Framework, wyjaśnia, jak używać go jako część [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowany dla Windows przy użyciu języka JavaScript, a w tym artykule opisano sposób debugowania w połączeniu z programem Visual Studio. (W Centrum deweloperów Windows.)|  
|[Dokumentacja środowiska uruchomieniowego Windows](/uwp/api/)|Dokumentacja dotycząca [!INCLUDE[wrt](../../../includes/wrt-md.md)]. (W Centrum deweloperów Windows.)|  
|[Przekazywanie identyfikatora URI do środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|W tym artykule opisano problem, który mogą wystąpić, jeśli przekazujesz identyfikatora URI z kodu zarządzanego do [!INCLUDE[wrt](../../../includes/wrt-md.md)]oraz jak uniknąć tego błędu.|
