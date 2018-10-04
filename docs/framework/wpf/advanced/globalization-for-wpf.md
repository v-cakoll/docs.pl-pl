---
title: Globalizacja dla WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: d2bb4c9a00f31cb87ad8890591aa190fac6384f9
ms.sourcegitcommit: 700b9003ea6bdd83a53458bbc436c9b5778344f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48261553"
---
# <a name="globalization-for-wpf"></a>Globalizacja dla WPF
W tym temacie przedstawiono problemy, które należy wiedzieć podczas pisania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji na rynek globalny. Globalizacja programistyczny są zdefiniowane w [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] w `System.Globalization`.



<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizacja XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] opiera się na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] i korzysta z pomocy technicznej globalizacji, zdefiniowane w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specyfikacji. W poniższych sekcjach opisano niektóre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funkcje, które trzeba wiedzieć.

<a name="char_reference"></a>
### <a name="character-references"></a>Odwołania do znaków
Odwołanie do znaku zawiera jednostki kodu UTF16 danej [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] znak ją reprezentuje w wartości dziesiętne lub szesnastkowe. Poniższy przykład przedstawia odwołanie do znaku dziesiętnego po litera KOPTYJSKI lub "Ϩ":

```
&#1000;
```

Poniższy przykład pokazuje odwołania znaków szesnastkowych. Należy zauważyć, że ma ona **x** przed liczbę szesnastkową.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Kodowanie
 Kodowanie obsługiwane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 i UTF-8. Instrukcja kodowania jest na początku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Atrybut kodowania, nie istnieje, jeśli nie ma żadnych kolejności bajtów, analizator wartość domyślna to UTF-8. UTF-8 i UTF-16 są preferowane kodowania. UTF-7 nie jest obsługiwane. W poniższym przykładzie pokazano, jak określić kodowanie UTF-8 w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atrybut Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używa [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) do reprezentowania atrybut language elementu.  Aby móc korzystać z <xref:System.Globalization.CultureInfo> klasy, wartość atrybutu language musi mieć jedną z nazw kultur wstępnie zdefiniowane przez <xref:System.Globalization.CultureInfo>. [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) dziedziczona drzewa elementów (według reguł XML nie musi to być z powodu dziedziczenia właściwości zależności) i jego wartość domyślna to ciąg pusty, jeśli nie jest jawnie przypisane.

 Atrybut language jest bardzo przydatne w przypadku określenia dialekty. Na przykład francuski ma inną pisownię, słownictwo i Wymowa we Francji, Quebec, Belgia i Szwajcarii. Także chińskim, japońskiej i koreańskiej udostępnić punkty kodowe w [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ale ideograficznych kształty są różne, i używają czcionki coś zupełnie innego.

 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie użyto `fr-CA` atrybutu języka, aby określić francuski (kanadyjski).

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługuje wszystkie [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funkcji, w tym surogaty. Tak długo, jak zestaw znaków mogą być mapowane na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], jest on obsługiwany. Na przykład GB18030, co oznacza wprowadzenie niektórych znaków, które są mapowane do rozszerzenia chińskim, japońskim i koreańskim (CFK), A i B i par zastępczych, dlatego jest w pełni obsługiwane. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja może użyć <xref:System.Globalization.StringInfo> do manipulowania ciągami bez zrozumienia, czy mają one pary zastępcze i łączenie znaków.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Projektowanie interfejsu użytkownika w wersji międzynarodowej przy użyciu XAML
 W tej sekcji opisano [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkcje, które należy wziąć pod uwagę podczas pisania aplikacji.

<a name="intl_text"></a>
### <a name="international-text"></a>Międzynarodowe tekstu
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera wbudowane przetwarzania dla systemów wszystkich pisania programu Microsoft .NET Framework obsługiwane.

 Obecnie obsługiwane są następujące skrypty:

-   Arabski

-   Bengali

-   Dewanagari

-   Cyrylica

-   grecki

-   Gujarati

-   Gurmukhi

-   Hebrajski

-   Ideograficznych skryptów

-   Kannada

-   Lao

-   Łaciński

-   Malayalam

-   Mongolian

-   Orija

-   Syryjski

-   Tamilski

-   Telugu

-   Thaana

-   Tajski *

-   Tibetan

 * W tej wersji wyświetlanie i edytowanie tajski tekstu jest obsługiwana; nie jest wyrazów.

 Obecnie nie są obsługiwane następujące skrypty:

-   Khmerski

-   Koreański Hangul stare

-   Myanmar

-   Syngaleski

 System pisma aparatów obsługi [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionki mogą obejmować [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabelach układu, które umożliwiają twórcom czcionki projektowania lepiej międzynarodowych wysokiej klasy związane z typografią czcionek i. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Czcionki tabele zawierają informacje dotyczące podstawienia symbol, pozycjonowanie symbol, uzasadnienie i położenie punktu odniesienia, umożliwiając aplikacji przetwarzanie tekstu w celu zwiększenia układu tekstu.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] czcionki, Zezwalaj na obsługę dużych symbol sets przy użyciu [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kodowania. Takie kodowania umożliwia obsługi szerokiej gamy międzynarodowych oraz jak w przypadku odmiany związane z typografią symbol.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Renderowanie tekstu jest obsługiwana przez [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] technologii podrzędnej pikseli, która obsługuje niezależność rozdzielczości. To znacznie zwiększa czytelność i udostępnia możliwość obsługi wysokiej jakości dotyczącym style dokumentów dla wszystkich skryptów.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Układ międzynarodowych
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia bardzo wygodny sposób obsługi poziome, dwukierunkowe i układów w pionie. W ramach prezentacji <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość może służyć do definiowania układu. Dostępne są następujące wzorce kierunek przepływu:

-   *LeftToRight* — układ poziomy łaciński, Azja Wschodnia i tak dalej.

-   *RightToLeft* -dwukierunkowych dla arabskiego, hebrajskiego i tak dalej.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Tworzenie zlokalizowanych aplikacjach
 Podczas pisania aplikacji do użytku globalnego należy zachować należy pamiętać, że aplikacja musi być możliwych do zlokalizowania. Poniższe tematy wspomnieć na uwadze pewne zagadnienia.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Wielojęzyczny interfejs użytkownika
 Wielojęzyczny interfejsy użytkownika (MUI) jest [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] Obsługa przełączanie [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z jednego języka do innego. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja używa modelu zestawu do obsługi MUI. Jedna aplikacja zawiera zestawy niezależny od języka, a także zestawów zasobów satelickich zależne od języka. Punkt wejścia jest zarządzany. EXE w głównym zestawie.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ładowania zasobów wykorzystuje [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]przez Menedżera zasobów do obsługi wyszukiwania zasobów i uwierzytelniania rezerwowego. Wiele zestawów satelickich języka współpracować z tego samego zestawu głównego. Zestaw zasobów, który jest ładowany jest zależna od <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> bieżącego wątku.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Interfejs użytkownika Lokalizowalny
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje używają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do definiowania ich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Umożliwia deweloperom określić hierarchię obiektów z zestawem właściwości i logiki. Podstawowym zastosowaniem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest opracowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, ale może służyć do określania hierarchii dowolnego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów. Większość programistów używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do określania ich stosowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a reagują na interakcję z użytkownikiem za pomocą języka programowania, takiego jak C#.

 Z punktu widzenia zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku przeznaczona do opisania zależne od języka [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest elementem zasobów i w związku z tym formatem końcowej dystrybucji musi być możliwy do zlokalizowania do obsługi języków obcych. Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie może obsłużyć zdarzenia wiele [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacje zawierają bloki kodu, aby to zrobić. Aby uzyskać więcej informacji, zobacz [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Kod jest wycięte i kompilowane do różnych plików binarnych podczas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku jest stokenizowana na formularz BAML XAML. Formularz BAML pliki XAML, obrazy i inne typy obiektów zarządzanych zasobów są osadzone w głównym zestawie satelickim zestawem zasobów, która może być lokalizowana w innych językach, lub w, gdy lokalizacja nie jest wymagane.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje do obsługi wszystkich [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zasobów, w tym tabele ciągów, obrazy i tak dalej.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Tworzenie zlokalizowanych aplikacjach
 Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do różnych kultur. Zapewnienie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji możliwych do zlokalizowania, umożliwiające tworzenie lokalizowalne zasoby w ramach zestawu zasobów. Zestaw zasobów jest zlokalizowany w różnych językach i korzysta z kodem — zarządzanie zasobami [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do załadowania. Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji to plik projektu (plików Proj). Wszystkie zasoby, których używasz w aplikacji powinny być objęte w pliku projektu. Poniższy przykład z pliku .csproj pokazuje, jak to zrobić.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Aby użyć wystąpienia zasób w aplikacji <xref:System.Resources.ResourceManager> i załaduj zasób, którego chcesz użyć. Poniższy przykład demonstruje, jak to zrobić.

 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Przy użyciu aplikacji ClickOnce za pomocą zlokalizowanych aplikacji
 ClickOnce jest nową technologię wdrożenia Windows Forms, która będzie dostarczany z Visual Studio 2005. Umożliwia instalowanie aplikacji i uaktualnianie aplikacji sieci Web. Gdy aplikacja, która została wdrożona za pomocą technologii ClickOnce jest zlokalizowana tylko mogą być wyświetlane na zlokalizowanej kultury. Na przykład, jeśli wdrożonej aplikacji jest zlokalizowane dla języka japońskiego go mogą być przeglądane tylko w języku japońskim [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] nie na Windows w języku angielskim. Stanowi to problem, ponieważ jest to typowy scenariusz dla japońskiego użytkownikom na uruchamianie angielska wersja systemu Windows.

 Rozwiązanie tego problemu jest ustawienie atrybutu rezerwowego neutralnym językiem. Twórca aplikacji może opcjonalnie Usuń zasoby z głównego zestawu i określ, czy zasoby znajdują się w zestawie satelickim odpowiadający określonej kultury. Do kontrolowania użycia tego procesu <xref:System.Resources.NeutralResourcesLanguageAttribute>. Konstruktor obiektu <xref:System.Resources.NeutralResourcesLanguageAttribute> klasa ma dwa podpisów, ta, która przyjmuje <xref:System.Resources.UltimateResourceFallbackLocation> parametru, aby określić lokalizację, gdzie <xref:System.Resources.ResourceManager> należy wyodrębnić zasoby rezerwowe: głównym zestawie lub zestawie satelickim. Poniższy przykład pokazuje, jak używać atrybutu. Ultimate lokalizacji rezerwowej, kod powoduje, że <xref:System.Resources.ResourceManager> wyszukiwać zasoby w podkatalogu "de" katalog zawierający obecnie wykonywany zestaw.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Zobacz też
 [Przeglądanie globalizacji i lokalizacji WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
