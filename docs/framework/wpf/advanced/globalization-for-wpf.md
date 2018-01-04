---
title: Globalizacja dla WPF
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-wpf
ms.topic: article
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6f39d40284e6212715d85fece545e653ff2e60a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="globalization-for-wpf"></a>Globalizacja dla WPF
W tym temacie przedstawiono problemy, które należy zwrócić uwagę podczas zapisywania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji na rynek globalnego. Globalizacja programistyczny są zdefiniowane w [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] w `System.Globalization`.  
  

  
<a name="xaml_globalization"></a>   
## <a name="xaml-globalization"></a>Globalizacja XAML  
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]jest oparta na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] i wykorzystuje wsparcia globalizacja zdefiniowane w [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] specyfikacji. W poniższych sekcjach opisano niektóre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funkcje, które należy zwrócić uwagę.  
  
<a name="char_reference"></a>   
### <a name="character-references"></a>Odwołania do znaków  
Odwołanie do znaku daje jednostki kodu UTF16 danej [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] znak go reprezentuje w wartości dziesiętne lub szesnastkowe. W poniższym przykładzie przedstawiono jako odwołanie do znaku dziesiętnego KOPTYJSKI ODSTĘP litera lub "Ϩ":

```
&#1000;
```

W poniższym przykładzie przedstawiono odwołanie znaków szesnastkowych. Należy zauważyć, że ma ona **x** przed liczbę szesnastkową.

```
&#x3E8;
```

<a name="encoding"></a>   
### <a name="encoding"></a>Kodowanie  
 Kodowanie obsługiwane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są [!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)], [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 i UTF-8. Instrukcja kodowania jest na początku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Brak atrybutu kodowania istnieje, jeśli nie ma żadnych kolejności bajtów, analizator domyślnie UTF-8. UTF-8 i UTF-16 są preferowane kodowania. UTF-7 nie jest obsługiwane. W poniższym przykładzie pokazano sposób określenia kodowania UTF-8 w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.  
  
```  
?xml encoding="UTF-8"?  
```  
  
<a name="lang_attrib"></a>   
### <a name="language-attribute"></a>Atrybut języka  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]używa [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) do reprezentowania atrybucie language elementu.  Aby móc korzystać z <xref:System.Globalization.CultureInfo> klasy, wartość atrybutu language musi być jedną z nazw kultury wstępnie zdefiniowane przez <xref:System.Globalization.CultureInfo>. [XML: lang](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) jest dziedziczona w drzewie elementu (regułami XML, niekoniecznie z powodu zależności dziedziczenia) i jego wartość domyślna to ciąg pusty, jeśli nie jest jawnie przypisane.  
  
 Atrybut języka jest przydatne do określenia dialekty języka. Na przykład francuski ma inną pisownię, słownictwa i wymowy Francja, Quebec, Belgia i Szwajcarii. Również udostępniać punktów kodowych w chińskich, japońskich i koreańskich [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], ale ideograficznych kształtów są różne, a ich używać całkiem czcionek.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie użyto `fr-CA` atrybut języka Aby określić kanadyjskich francuski.  
  
```xml  
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>  
```  
  
<a name="unicode"></a>   
### <a name="unicode"></a>Unicode  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]obsługuje wszystkie [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funkcji, łącznie z elementami zastępczymi została. Tak długo, jak zestaw znaków mogą być mapowane na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], jest obsługiwane. Na przykład GB18030 wprowadza pewne znaki, które są mapowane do rozszerzenia chińskim, japońskim i koreańskim (CFK), A i B i dwuskładnikowy pary, dlatego całkowicie jest obsługiwane. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacja może używać <xref:System.Globalization.StringInfo> do manipulowania ciągami bez opis, czy mają one Znaki dwuskładnikowe lub łączenie znaków.  
  
<a name="design_intl_ui_with_xaml"></a>   
## <a name="designing-an-international-user-interface-with-xaml"></a>Projektowanie interfejsu użytkownika w wersji międzynarodowej o XAML  
 W tej sekcji opisano [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkcje, które należy wziąć pod uwagę podczas pisania aplikacji.  
  
<a name="intl_text"></a>   
### <a name="international-text"></a>Międzynarodowe tekstu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zawiera wbudowane przetwarzania dla wszystkich [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] obsługiwanych systemach zapisu.  
  
 Obecnie obsługiwane są następujące skrypty:  
  
-   Arabski  
  
-   Bengalski  
  
-   Dewanagari  
  
-   Cyrylica  
  
-   grecki  
  
-   Gudżarati  
  
-   Gurmukhi  
  
-   Hebrajski  
  
-   Ideograficznych skryptów  
  
-   Kannada  
  
-   Laotańska  
  
-   Łacińska  
  
-   Malayalam  
  
-   Mongolski  
  
-   Orija  
  
-   Syryjski  
  
-   Tamilski  
  
-   Telugu  
  
-   Thaana  
  
-   Tajski *  
  
-   Tibetan  
  
 * W tej wersji wyświetlania i edytowania tekstu tajski jest obsługiwany; nie jest dzielenia wyrazów.  
  
 Obecnie nie są obsługiwane następujące skrypty:  
  
-   Kmerski  
  
-   Koreański Hangul starego  
  
-   Myanmaru  
  
-   Sinhala  
  
 System pisma silników obsługi [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] czcionek. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]czcionki mogą obejmować [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabele, umożliwiających twórców czcionki do projektowania lepiej międzynarodowe wysokiej klasy związane z typografią czcionki i. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] Czcionki tabele zawierają informacje o symbolu podstawień, pozycjonowanie symbolu uzasadnienie i położenie linii bazowej, włączanie aplikacji przetwarzanie tekstu w celu zwiększenia układu tekstu.  
  
 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]czcionki Zezwalaj na obsługę dużych symbolu ustawia przy użyciu [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kodowania. Takie kodowanie umożliwia szeroki zakres międzynarodowych obsługi oraz jak w przypadku wariantów związane z typografią symbolu.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Renderowanie tekstu jest obsługiwany przez [!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)] podrzędne pikseli technologia, która obsługuje niezależność rozpoznawania. To znacznie poprawia czytelność i umożliwia obsługę wysokiej jakości magazine styl dokumentów wszystkie skrypty.  
  
<a name="intl_layout"></a>   
### <a name="international-layout"></a>Układ międzynarodowych  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]oferuje bardzo wygodny sposób obsługiwać poziomej, dwukierunkowego i układy pionowy. W ramach prezentacji <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwości może służyć do definiowania układu. Wzorce kierunek przepływu to:  
  
-   *LeftToRight* — układ poziomy Latin, wschodnioazjatyckich i tak dalej.  
  
-   *RightToLeft* — dwukierunkowy dla arabskiego, hebrajskiego i tak dalej.  
  
<a name="developing_localizable_apps"></a>   
## <a name="developing-localizable-applications"></a>Tworzenie aplikacji możliwych do zlokalizowania  
 Podczas pisania aplikacji dla globalnego zużycia należy mieć na uwadze, że aplikacja musi być lokalizowalny. Poniższe tematy wskazywanie rzeczy, które należy wziąć pod uwagę.  
  
<a name="mui"></a>   
### <a name="multilingual-user-interface"></a>Wielojęzyczny interfejs użytkownika  
 Obsługa wielu języków interfejsy użytkownika (MUI) jest [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] obsługuje przełączenie [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] z jednego języka do innego. A [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikację do obsługi MUI modelu zestawu. Jedna aplikacja zawiera zestawy niezależny od języka, a także zestawy zasobów zależnych od języka. Punkt wejścia jest zarządzanego. EXE w zestawie głównym.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Moduł ładujący zasoby korzysta z [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]przez Menedżera zasobów do obsługi wyszukiwania zasobów i powrotu. Zestawy satelickie języka wielu współpracować z tego samego zestawu głównego. Zależy od zestawu zasobów, który jest ładowany <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> bieżącego wątku.  
  
<a name="localizable_ui"></a>   
### <a name="localizable-user-interface"></a>Interfejs użytkownika Lokalizowalny  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje używają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do definiowania ich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Umożliwia deweloperom określić hierarchię obiektów z zestawem właściwości i logika. Podstawowym zastosowaniem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest rozwój [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, ale można określić hierarchię dowolnego [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] obiektów. Użyj większość deweloperów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] określić ich stosowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i użyj języka programowania, takiego jak [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] reagowanie na interakcji z użytkownikiem.  
  
 Z punktu widzenia zasobów [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku przeznaczony do opisywania zależne od języka [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] jest elementem zasobów i jego format końcowej dystrybucji musi mieć zatem Lokalizowalny do obsługi językach. Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie może obsłużyć zdarzenia wiele [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacje zawierają bloki kodu, w tym celu. Aby uzyskać więcej informacji, zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Kod jest wycięte i kompilowane do plików binarnych różnych podczas [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku stokenizowanego jest w formie BAML XAML. Formularz BAML plików XAML, obrazy i inne typy zasobów zarządzanych obiektów wbudowanych w zestawu satelickiego zasobów, które można lokalizować na inne języki, lub główny zestaw gdy lokalizacja nie jest wymagana.  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje obsługują wszystkie [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zasobów w tym tabele ciągów, obrazy i tak dalej.  
  
<a name="building_localizable_apps"></a>   
### <a name="building-localizable-applications"></a>Tworzenie aplikacji Lokalizowalny  
 Lokalizowanie oznacza dostosowanie [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do innych kultur. Aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji Lokalizowalny deweloperzy potrzebne do tworzenia zlokalizowania zasobów w ramach zestawu zasobów. Zestaw zasobów jest zlokalizowane w różnych językach, a kodem używa zarządzanie zasobami [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] do załadowania. Jeden z plików wymaganych do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji jest plikiem projektu (.proj). W pliku projektu powinien znajdować się wszystkie zasoby, które są używane w aplikacji. Poniższy przykład z pliku .csproj pokazuje, jak to zrobić.  
  
```xml  
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>  
```  
  
 Aby użyć wystąpienia zasób w aplikacji <xref:System.Resources.ResourceManager> i załadować zasobu, którego chcesz użyć. Poniższy przykład demonstruje, jak to zrobić.  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]  
  
<a name="using_clickonce"></a>   
## <a name="using-clickonce-with-localized-applications"></a>Za pomocą aplikacji ClickOnce z aplikacjami zlokalizowanych  
 ClickOnce jest nową technologią wdrożenia formularzy systemu Windows będzie dostarczanych z programem [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)]. Umożliwia instalowanie aplikacji i uaktualniania aplikacji sieci Web. Gdy aplikacja, która została wdrożona za pomocą technologii ClickOnce jest zlokalizowana mogą być przeglądane tylko w zlokalizowanych kultury. Na przykład, jeśli wdrażana aplikacja jest zlokalizowana na japoński go mogą być przeglądane tylko w języku japońskim [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] nie znajduje się w języku angielskim [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)]. Stanowi to problem, ponieważ jest typowym scenariuszem dla japońskiego użytkownikom na uruchamianie angielską wersję językową [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)].  
  
 Rozwiązanie tego problemu jest ustawienie atrybutu rezerwowy niezależnym od języka. Deweloper aplikacji Opcjonalnie można usunąć zasoby z głównego zestawu i określ, że zasoby można znaleźć w zestawie satelickim odpowiadający określonej kultury. Do kontrolowania użycia tego procesu <xref:System.Resources.NeutralResourcesLanguageAttribute>. Konstruktor obiektu <xref:System.Resources.NeutralResourcesLanguageAttribute> klasa ma dwa podpisów, który przyjmuje <xref:System.Resources.UltimateResourceFallbackLocation> parametr, aby określić lokalizację, gdzie <xref:System.Resources.ResourceManager> należy wyodrębnić zasoby rezerwowe: główny zestaw lub zestawu satelickiego. Poniższy przykład przedstawia użycie atrybutu. Ultimate lokalizacji rezerwowej, kod powoduje, że <xref:System.Resources.ResourceManager> ma zostać wyszukane zasoby w podkatalogu "de" katalog zawierający obecnie wykonywany zestaw.  
  
```  
[assembly: NeutralResourcesLanguageAttribute(  
    "de" , UltimateResourceFallbackLocation.Satellite)]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przeglądanie globalizacji i lokalizacji WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)
