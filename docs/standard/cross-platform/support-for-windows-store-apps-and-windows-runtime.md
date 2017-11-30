---
title: "Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Store apps, .NET Framework support for
- Windows Runtime, .NET Framework support for
- .NET for Windows Store apps
- .NET Framework, and Windows Store apps
- .NET Framework, and Windows Runtime
ms.assetid: 6fa7d044-ae12-4c54-b8ee-50915607a565
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8ee68c53173f0919a9200ed5ac82fed3e27affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="net-framework-support-for-windows-store-apps-and-windows-runtime"></a>Obsługa .NET Framework dla aplikacji sklepu Windows Store i środowiska wykonawczego systemu Windows
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Jest obsługiwanych kilka scenariuszy rozwoju oprogramowania z [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Te scenariusze dzielą się na trzy kategorie:  
  
-   Tworzenie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji za pomocą kontrolki XAML, zgodnie z opisem w [plan dla Sklepu Windows przy użyciu języka C# lub Visual Basic](http://go.microsoft.com/fwlink/p/?LinkID=242212), [aplikacji ze Sklepu Windows rozwijających się (VB / C# / C++ i XAML)](http://go.microsoft.com/fwlink/p/?LinkId=238311)i [Omówienie aplikacji .NET dla Sklepu Windows](http://go.microsoft.com/fwlink/p/?LinkId=238312) w Centrum deweloperów systemu Windows.  
  
-   Tworzenie bibliotek klas do użycia w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacje utworzone za pomocą programu .NET Framework.  
  
-   Tworzenie [!INCLUDE[wrt](../../../includes/wrt-md.md)] składniki w. Plików WinMD, które mogą być używane przez język programowania, który obsługuje [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Na przykład, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=238313) w Centrum deweloperów systemu Windows.  
  
 W tym temacie przedstawiono pomocy technicznej, .NET Framework zapewnia dla wszystkich trzech kategorii, którą opisano scenariusze dotyczące [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników. Pierwsza sekcja zawiera podstawowe informacje na temat relacji między programu .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)]i opisano niektóre oddities mogą wystąpić w systemie pomocy i IDE. [Drugiej sekcji](#WindowsRuntimeComponents) opisano scenariusze związane z opracowywaniem [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników.  
  
## <a name="the-basics"></a>Podstawy  
 .NET Framework obsługuje scenariusze tworzenia trzech podanych wcześniej, zapewniając [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], a dzięki obsłudze [!INCLUDE[wrt](../../../includes/wrt-md.md)] samej siebie.  
  
-   [.NET dla Sklepu Windows apps](http://go.microsoft.com/fwlink/p/?LinkId=247912) zapewnia uproszczony widok biblioteki klas .NET Framework i zawierają tylko typy i elementy członkowskie, można użyć do utworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i [!INCLUDE[wrt](../../../includes/wrt-md.md)] składników.  
  
    -   Jeśli używasz programu Visual Studio ([!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] lub nowszym) do opracowywania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji lub [!INCLUDE[wrt](../../../includes/wrt-md.md)] zapewnia zbiór zestawów odwołań składnika, zostanie wyświetlony tylko odpowiednie typy i elementy członkowskie.  
  
    -   Upraszcza to prostsze zestawu interfejsów API przez usuwanie funkcji zduplikowanych w programie .NET Framework lub że duplikat [!INCLUDE[wrt](../../../includes/wrt-md.md)] funkcji. Na przykład zawiera tylko wersje ogólnych typów kolekcji i modelu obiektu dokumentu XML wyeliminowania uzyskać [!INCLUDE[wrt](../../../includes/wrt-md.md)] ustawić XML API.  
  
    -   Funkcje, które po prostu zawijać interfejsu API systemu operacyjnego są również usuwane, ponieważ [!INCLUDE[wrt](../../../includes/wrt-md.md)] jest łatwy do wywoływania z kodu zarządzanego.  
  
     Aby dowiedzieć się więcej o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], zobacz [Omówienie aplikacji .NET dla Sklepu Windows](http://go.microsoft.com/fwlink/p/?LinkId=238312) Center.To deweloperów systemu Windows, przeczytaj o procesu wyboru interfejsu API, zobacz [.NET dla Sklepu Windows apps](http://go.microsoft.com/fwlink/p/?LinkId=251061) wpis w ramach platformy .NET blog.  
  
-   [Środowiska wykonawczego systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=238319) zawiera elementy interfejsu użytkownika dla tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji oraz zapewnia dostęp do funkcji systemu operacyjnego. .NET Framework, takich jak [!INCLUDE[wrt](../../../includes/wrt-md.md)] ma metadanych, które umożliwia Kompilatory języka C# i Visual Basic umożliwia [!INCLUDE[wrt](../../../includes/wrt-md.md)] bibliotek klas sposób korzystają z programu .NET Framework. .NET Framework ułatwia użyj [!INCLUDE[wrt](../../../includes/wrt-md.md)] ukrywając pewne różnice:  
  
    -   Pewne różnice w programowaniu wzorce między programu .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)], takich jak wzorzec do dodawania i usuwania programów obsługi zdarzeń, są ukryte. Po prostu użyć wzorzec .NET Framework.  
  
    -   Pewne różnice w często używanych typów (na przykład typy pierwotne i kolekcje) są ukryte. Po prostu można użyć typu .NET Framework, zgodnie z opisem w [różnice czy są widoczne w IDE](#DifferencesVisibleInIDE)w dalszej części tego artykułu.  
  
 Większość czasu, .NET Framework — obsługa dla [!INCLUDE[wrt](../../../includes/wrt-md.md)] jest niewidoczny. W następnej sekcji omówiono niektóre różnice kodu zarządzanego w widocznej i [!INCLUDE[wrt](../../../includes/wrt-md.md)].  
  
<a name="AboutReferenceDocumentation"></a>   
### <a name="the-net-framework-and-the-includewrtincludeswrt-mdmd-reference-documentation"></a>.NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)] odwołania dokumentacji  
 Systemu Windows i zestawy dokumentacji .NET Framework są niezależne. Po naciśnięciu klawisza F1, aby wyświetlić Pomoc dotyczącą typu lub elementu członkowskiego, zostanie wyświetlony dokumentacji z odpowiedniego zestawu. Jednak jeśli przeglądania [odwołania do środowiska wykonawczego systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=238319) napotkać przykłady, które wydają się puzzling:  
  
-   Tematy, takie jak [interfejsu IIterable](http://go.microsoft.com/fwlink/p/?LinkId=238321) nie ma Składnia deklaracji dla języka Visual Basic lub C#. Zamiast tego uwagi pojawi się powyżej w sekcji składni (w tym przypadku ".NET: ten interfejs jest wyświetlany jako System.Collections.Generic.IEnumerable\<T >"). Jest to spowodowane programu .NET Framework i [!INCLUDE[wrt](../../../includes/wrt-md.md)] zapewniają podobne funkcje o różnych interfejsach. Ponadto istnieją różnice funkcjonalne: `IIterable` ma `First` zamiast metody <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda zwraca moduł wyliczający. Wymuszanie, aby dowiedzieć się inny sposób wykonywania typowych zadań, a nie obsługuje programu .NET Framework [!INCLUDE[wrt](../../../includes/wrt-md.md)] dokonując są wyświetlane, aby użyć typu znasz kodu zarządzanego. Nie będą widzieć `IIterable` interfejsu w IDE, a więc jedynym sposobem podłączania w [!INCLUDE[wrt](../../../includes/wrt-md.md)] dokumentacji polega na przeglądaniu tej dokumentacji bezpośrednio.  
  
-   [Konstruktor SyndicationFeed](http://go.microsoft.com/fwlink/p/?LinkId=238322) dokumentacji przedstawiono ściśle powiązane wydania: jego typy parametrów mogą być różne dla różnych języków. C# i Visual Basic, typy parametrów są <xref:System.String?displayProperty=nameWithType> i <xref:System.Uri?displayProperty=nameWithType>. Ponownie, to dlatego, .NET Framework ma własną `String` i `Uri` typów, a dla takich często używanych typów nie ma sensu zmusić użytkowników .NET Framework, aby dowiedzieć się więcej w inny sposób działania. W środowisku IDE programu .NET Framework ukrywa odpowiadającego [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów.  
  
-   W niektórych przypadkach takich jak [Windows.UI.Xaml.GridLength](http://go.microsoft.com/fwlink/p/?LinkId=251059) struktury .NET Framework zapewnia typu o takiej samej nazwie, ale więcej funkcji. Na przykład zbiór tematów Konstruktor i właściwości są skojarzone z `GridLength`, ale mają bloki składni tylko w przypadku języka Visual Basic i C# elementów członkowskich nie są dostępne tylko w kodzie zarządzanym. W [!INCLUDE[wrt](../../../includes/wrt-md.md)], konstrukcji jest tylko pola. [!INCLUDE[wrt](../../../includes/wrt-md.md)] Struktury wymaga klasę pomocy [Windows.UI.Xaml.GridLengthHelper](http://go.microsoft.com/fwlink/p/?LinkId=251060)w celu zapewnienia równoważne funkcje. Nie będzie wyświetlana, klasa pomocy w IDE podczas pisania kodu zarządzanego.  
  
-   W środowisku IDE programu [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy prawdopodobnie pochodzi od <xref:System.Object?displayProperty=nameWithType>. Pojawią się one mieć członków dziedziczonych po elemencie <xref:System.Object>, takich jak <xref:System.Object.ToString%2A?displayProperty=nameWithType>. Elementy te działają tak samo jak, jeśli typy faktycznie dziedziczone z <xref:System.Object>, i [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy mogą być rzutowane na <xref:System.Object>. Ta funkcja jest częścią programu .NET Framework zapewnia obsługę [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Jednak jeśli przeglądasz typów w [!INCLUDE[wrt](../../../includes/wrt-md.md)] odwołania dokumentacji, są wyświetlane nie takich członków. W dokumentacji tych jawnego dziedziczone elementy członkowskie są dostarczane przez <xref:System.Object?displayProperty=nameWithType> odwołania dokumentacji.  
  
<a name="DifferencesVisibleInIDE"></a>   
### <a name="differences-that-are-visible-in-the-ide"></a>Różnice, które są widoczne w środowisku IDE  
 Bardziej zaawansowane scenariusze programowania, takie jak przy użyciu [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika napisane w języku C#, aby zapewnić logikę aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacja dla systemu Windows przy użyciu języka JavaScript, różnice te są widoczne w IDE, a także w dokumentacji. Gdy składnik zwraca `IDictionary<int, string>` JavaScript, i przyjrzyj się on w debugerze JavaScript, zobaczysz metody `IMap<int, string>` ponieważ JavaScript używa [!INCLUDE[wrt](../../../includes/wrt-md.md)] typu. Niektóre często używane w poniższej tabeli przedstawiono typy, które są wyświetlane w różny sposób w dwóch języków kolekcji:  
  
|[!INCLUDE[wrt](../../../includes/wrt-md.md)]Typ|Odpowiedniego typu .NET Framework|  
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
  
 W [!INCLUDE[wrt](../../../includes/wrt-md.md)], `IMap<K, V>` i `IMapView<K, V>` są iterowane przy użyciu `IKeyValuePair`. Jeśli są przekazywane do kodu zarządzanego, są wyświetlane jako `IDictionary<TKey, TValue>` i `IReadOnlyDictionary<TKey, TValue>`, więc naturalnie możesz użyć `System.Collections.Generic.KeyValuePair<TKey, TValue>` do wyliczenia.  
  
 Interfejsy sposób są wyświetlane w kod zarządzany ma wpływ typów sposób, które implementują interfejsy te są wyświetlane. Na przykład `PropertySet` klasa implementuje `IMap<K, V>`, która jest wyświetlana w zarządzanym kodzie jako `IDictionary<TKey, TValue>`. `PropertySet`pojawi się tak, jakby zaimplementowana `IDictionary<TKey, TValue>` zamiast `IMap<K, V>`, więc w kodzie zarządzanym wydaje się być `Add` metody, która zachowuje się jak `Add` metoda słowniki .NET Framework. Nie wydaje się być `Insert` metody.  
  
 Aby uzyskać więcej informacji o korzystaniu z programu .NET Framework do utworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika i wskazówki, który przedstawia sposób użycia tych składników, JavaScript, zobacz [tworzenia składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=238313) w Centrum deweloperów systemu Windows.  
  
### <a name="primitive-types"></a>Typy pierwotne  
 Aby włączyć fizycznych korzystanie z [!INCLUDE[wrt](../../../includes/wrt-md.md)] w kodzie zarządzanym, typy pierwotne .NET Framework są wyświetlane zamiast [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów pierwotnych w kodzie. W programie .NET Framework, typy pierwotne, takich jak `Int32` struktura zawiera wiele przydatnych właściwości i metod, takich jak `Int32.TryParse` metody. Z kolei pierwotne, typy i struktury w [!INCLUDE[wrt](../../../includes/wrt-md.md)] zawierać tylko pola. Gdy używasz podstawowych w kodzie zarządzanym się typy .NET Framework, a w zwykły sposób można użyć właściwości i metody typów .NET Framework. Poniższa lista zawiera podsumowanie:  
  
-   Dla [!INCLUDE[wrt](../../../includes/wrt-md.md)] podstawowych `Int32`, `Int64`, `Single`, `Double`, `Boolean`, `String` (niezmienne zbiór znaków Unicode), `Enum`, `UInt32`, `UInt64`, i `Guid`, używając typu o takiej samej nazwie w `System` przestrzeni nazw.  
  
-   Aby uzyskać `UInt8`, użyj `System.Byte`.  
  
-   Aby uzyskać `Char16`, użyj `System.Char`.  
  
-   Aby uzyskać `IInspectable` interfejsu, użyj `System.Object`.  
  
-   Dla `HRESULT`, struktura jest używana z jednym `System.Int32` elementu członkowskiego.  
  
 Podobnie jak w typów interfejsów tylko wtedy można napotkać dowód taka reprezentacja jest, gdy projekt .NET Framework jest [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika, który jest używany przez [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanej za pomocą języka JavaScript.  
  
 Inne podstawowe najczęściej używanych [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy, które są widoczne w kodzie zarządzanym jako odpowiedniki .NET Framework `Windows.Foundation.DateTime` struktury, która jest wyświetlana w zarządzanym kodzie jako <xref:System.DateTimeOffset?displayProperty=nameWithType> struktury i `Windows.Foundation.TimeSpan` struktury, którego pojawia się jako <xref:System.TimeSpan?displayProperty=nameWithType> struktury.  
  
### <a name="other-differences"></a>Inne różnice między  
 W niektórych przypadkach, fakt, że typy .NET Framework są wyświetlane w kodzie zamiast [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy wymaga działań ze strony użytkownika. Na przykład [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) klasy jest wyświetlany jako <xref:System.Uri?displayProperty=nameWithType> w kodzie .NET Framework. <xref:System.Uri?displayProperty=nameWithType>Umożliwia względnym identyfikatorem URI, ale [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) wymaga bezwzględnego identyfikatora URI. W związku z tym podczas przekazywania identyfikatora URI do [!INCLUDE[wrt](../../../includes/wrt-md.md)] metody, należy upewnić się bezwzględną. (Zobacz [przekazywanie URI do środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md).)  
  
<a name="WindowsRuntimeComponents"></a>   
## <a name="scenarios-for-developing-windows-runtime-components"></a>Scenariusze dotyczące tworzenia składników środowiska wykonawczego systemu Windows  
 Scenariusze, które są obsługiwane dla zarządzanych [!INCLUDE[wrt](../../../includes/wrt-md.md)] składniki są zależne od następujące zasady ogólne:  
  
-   [!INCLUDE[wrt](../../../includes/wrt-md.md)]Składniki, które są tworzone przy użyciu programu .NET Framework ma nie jawnego różnice z innych [!INCLUDE[wrt](../../../includes/wrt-md.md)]biblioteki. Na przykład, jeśli ponowne wdrożenie natywny [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika za pomocą kodu zarządzanego, dwa składniki są nierozróżnialne wypukłymi. Fakt, że składnik jest zapisywane w kodzie zarządzanym jest niewidoczna dla kodu, który korzysta z niego, nawet jeśli kod jest sama kodu zarządzanego. Jednak wewnętrznie składnika jest true kodu zarządzanego i uruchamia na środowisko uruchomieniowe języka wspólnego (CLR).  
  
-   Składniki może zawierać typy, które implementują logikę aplikacji, [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] interfejsu użytkownika formantów lub oba.  
  
    > [!NOTE]
    >  Należy dobrze do oddzielania elementów interfejsu użytkownika z logiki aplikacji. Ponadto nie można użyć [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] formantów interfejsu użytkownika w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla systemu Windows przy użyciu języka JavaScript i HTML.  
  
-   Składnik może być projektu w rozwiązaniu programu Visual Studio dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji lub komponentów wielokrotnego użytku, które można dodać do wielu rozwiązań.  
  
    > [!NOTE]
    >  Jeśli składnika będzie można użyć tylko w języku C# lub Visual Basic, to nie ma powodu, aby była [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Jeśli będzie to zwykłe Biblioteka klas programu .NET Framework zamiast tego, nie trzeba jej publicznej powierzchni interfejsu API, aby ograniczyć [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów.  
  
-   Można zwolnić wersje wielokrotnego użytku składników za pomocą [!INCLUDE[wrt](../../../includes/wrt-md.md)] [VersionAttribute](http://go.microsoft.com/fwlink/p/?LinkId=238563) atrybutu, aby zidentyfikować typy, które (i elementów członkowskich, które w określonym typie) zostały dodane w różnych wersjach.  
  
-   Typy w składniku może pochodzić od [!INCLUDE[wrt](../../../includes/wrt-md.md)] typów. Formanty może pochodzić od typów pierwotnych kontroli w [Windows.UI.Xaml.Controls.Primitives](http://go.microsoft.com/fwlink/p/?LinkId=238564) przestrzeni nazw lub od bardziej Zakończono formantów takich jak [przycisk](http://go.microsoft.com/fwlink/p/?LinkId=238565).  
  
    > [!IMPORTANT]
    >  Począwszy od [!INCLUDE[win8](../../../includes/win8-md.md)] i [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], wszystkie typy publiczne w zarządzanego [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika muszą być zapieczętowane. Typ w innym [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika nie może pochodzić z nich. Jeśli chcesz podać polimorficznych zachowanie w składniku, można utworzyć interfejsu i ją wdrożyć w typach polimorficznych.  
  
-   Wszystkie typy parametrów i wróć na typy publiczne w składniku muszą być [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy (w tym [!INCLUDE[wrt](../../../includes/wrt-md.md)] typy, które definiuje składnika).  
  
 Poniższe sekcje zawierają przykłady typowych scenariuszy.  
  
### <a name="application-logic-for-a-includewin8appnamelongincludeswin8-appname-long-mdmd-app-with-javascript"></a>Logikę aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka JavaScript  
 Podczas opracowywania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla systemu Windows przy użyciu języka JavaScript, może się okazać, że niektórych części logiki aplikacji w kodzie zarządzanym, lub lepiej są łatwiejsze do opracowywania. Język JavaScript nie można użyć bibliotek klas .NET Framework bezpośrednio, ale możesz wprowadzić biblioteki klas. Plik WinMD. W tym scenariuszu [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika jest integralną częścią aplikacji, więc go nie ma sensu zapewnienie atrybuty wersji.  
  
### <a name="reusable-includewin8appnamelongincludeswin8-appname-long-mdmd-ui-controls"></a>Do ponownego użycia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] kontrolek interfejsu użytkownika  
 Można spakować zestaw powiązanych formantów interfejsu użytkownika w wielokrotnego użytku [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Składnik można wprowadzać na rynek samodzielnie lub używane jako element w aplikacjach można utworzyć. W tym scenariuszu, warto użyć [!INCLUDE[wrt](../../../includes/wrt-md.md)] [VersionAttribute](http://go.microsoft.com/fwlink/p/?LinkId=238563) atrybutu, aby zwiększyć zgodność.  
  
### <a name="reusable-application-logic-from-existing-net-framework-apps"></a>Do ponownego użycia aplikacji logiki z istniejącej aplikacji programu .NET Framework  
 Kod zarządzany może pakietu z istniejących aplikacji klasycznych, jako autonomiczny [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika. Dzięki temu można użyć składnika w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanych za pomocą języka C++ lub JavaScript, jak również w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji skompilowanych przy użyciu języka C# lub Visual Basic. Przechowywanie wersji to opcja, jeśli istnieje wiele scenariuszy ponowne użycie kodu.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Omówienie aplikacji .NET dla Sklepu Windows](http://go.microsoft.com/fwlink/p/?LinkId=238312)|W tym artykule opisano typy .NET Framework i elementów członkowskich, które umożliwia tworzenie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji i [!INCLUDE[wrt](../../../includes/wrt-md.md)]składników. (W Centrum deweloperów systemu Windows.)|  
|[Przewodnik po aplikacji do Sklepu Windows przy użyciu języka C# lub Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=242212)|Udostępnia kluczowych zasobów, aby rozpocząć wdrażanie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka C# lub Visual Basic, łącznie z wielu tematów — Szybki Start, wskazówki i najlepsze rozwiązania. (W Centrum deweloperów systemu Windows.)|  
|[Tworzenie aplikacji ze Sklepu Windows (VB / C# / C++ i XAML)](http://go.microsoft.com/fwlink/p/?LinkId=238311)|Udostępnia kluczowych zasobów, aby rozpocząć wdrażanie [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji przy użyciu języka C# lub Visual Basic, łącznie z wielu tematów — Szybki Start, wskazówki i najlepsze rozwiązania. (W Centrum deweloperów systemu Windows.)|  
|[Tworzenie składników środowiska wykonawczego systemu Windows w języku C# i Visual Basic](http://go.microsoft.com/fwlink/p/?LinkId=238313)|Opisuje sposób tworzenia [!INCLUDE[wrt](../../../includes/wrt-md.md)] składnika za pomocą programu .NET Framework, wyjaśniono, jak używać go jako część [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji dla systemu Windows przy użyciu języka JavaScript i opisano, jak można debugować połączenie z programem Visual Studio. (W Centrum deweloperów systemu Windows.)|  
|[Odwołanie do środowiska wykonawczego systemu Windows](http://go.microsoft.com/fwlink/?LinkId=238319)|Dokumentacja referencyjna dla [!INCLUDE[wrt](../../../includes/wrt-md.md)]. (W Centrum deweloperów systemu Windows.)|  
|[Przekazywanie URI do środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/passing-a-uri-to-the-windows-runtime.md)|W tym artykule opisano problem, który może wystąpić podczas przekazywania identyfikatora URI z kodu zarządzanego do [!INCLUDE[wrt](../../../includes/wrt-md.md)]oraz jak uniknąć tego problemu.|
