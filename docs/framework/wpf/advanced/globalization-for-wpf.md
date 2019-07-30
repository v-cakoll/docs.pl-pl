---
title: Globalizacja dla WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 099d6b94f9094ac9baed25e5060d8a166e27573b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629926"
---
# <a name="globalization-for-wpf"></a>Globalizacja dla WPF
Ten temat zawiera informacje o problemach, które należy wziąć pod [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uwagę podczas pisania aplikacji dla globalnego rynku. Elementy programowania globalizacji są zdefiniowane w [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] programie w programie. `System.Globalization`

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizacja XAML
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]jest oparta na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] i wykorzystuje obsługę globalizacji zdefiniowaną [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] w specyfikacji. W poniższych sekcjach opisano [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] niektóre funkcje, których należy wiedzieć.

<a name="char_reference"></a>
### <a name="character-references"></a>Odwołania do znaków
Odwołanie znaku daje jednostkę kodu UTF16 dla określonego [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] znaku, który reprezentuje, w postaci dziesiętnej lub szesnastkowej. W poniższym przykładzie pokazano odwołanie do znaku dziesiętnego dla COPTIC wielkiej litery, lub "Ϩ":

```
&#1000;
```

W poniższym przykładzie pokazano szesnastkowe odwołanie do znaku. Zwróć uwagę, że ma **symbol x** przed liczbą szesnastkową.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Kodowanie
 Kodowanie obsługiwane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] są ASCII, [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] UTF-16 i UTF-8. Instrukcja kodowania znajduje się na początku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dokumentu. Jeśli żaden atrybut kodowania nie istnieje i nie ma kolejności bajtów, Analizator domyślnie używa kodowania UTF-8. Kodowanie UTF-8 i UTF-16 są preferowanymi kodowaniami. Kodowanie UTF-7 nie jest obsługiwane. W poniższym przykładzie pokazano, jak określić kodowanie UTF-8 w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku.

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atrybut Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]używa [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) do reprezentowania atrybutu języka elementu.  Aby skorzystać z <xref:System.Globalization.CultureInfo> klasy, wartość atrybutu języka musi być jedną z nazw kultur wstępnie zdefiniowanych przez <xref:System.Globalization.CultureInfo>. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) można dziedziczyć w drzewie elementów (według reguł XML, niekoniecznie ze względu na dziedziczenie właściwości zależności), a jego wartość domyślna to pusty ciąg, jeśli nie jest on jawnie przypisany.

 Atrybut Language jest bardzo przydatny do określania dialektów. Na przykład francuski ma inną pisownię, słownictwo i wymowę w Francji, Quebec, Belgii i Szwajcarii. Ponadto w [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]języku chińskim, japońskim i koreańskim można przydzielić punkty kodu, ale kształty ideograficzne różnią się od siebie i używają całkowicie różnych czcionek.

 W poniższym [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykładzie zastosowano `fr-CA` atrybut Language, aby określić kanadyjski francuski.

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]obsługuje wszystkie [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] funkcje, w tym surogaty. Tak długo, jak zestaw znaków może być zamapowany na [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)], jest obsługiwany. Na przykład GB18030 wprowadza pewne znaki, które są mapowane na rozszerzenia w języku chińskim, japońskim i koreańskim (CFK) a i B i pary dwuskładnikowe, dlatego jest w pełni obsługiwane. Aplikacja może używać <xref:System.Globalization.StringInfo> do manipulowania ciągami bez względu na to, czy mają pary dwuskładnikowe, czy łączące znaki. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Projektowanie międzynarodowego interfejsu użytkownika przy użyciu języka XAML
 W tej sekcji [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] opisano funkcje, które należy wziąć pod uwagę podczas pisania aplikacji.

<a name="intl_text"></a>
### <a name="international-text"></a>Tekst Międzynarodowy
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obejmuje wbudowane przetwarzanie dla wszystkich obsługiwanych systemów Microsoft .NET Framework.

 Obecnie obsługiwane są następujące skrypty:

- Arabski

- Bengalski

- Devanagari

- Pisanych

- grecki

- Gudżarati

- Gurmukhi

- Hebrajski

- Skrypty ideograficzne

- Kannada

- Lao

- Wielka

- Malajalam

- Mongolian

- Odia

- Języka

- Tamilski

- Telugu

- Thaana

- Wersji

- Tybetański

 \* W tej wersji jest obsługiwane wyświetlanie i edytowanie tekstu w języku tajlandzkim; dzielenie wyrazów nie jest dozwolone.

 Następujące skrypty nie są obecnie obsługiwane:

- Khmerski

- Stary Hangul koreański

- Mjanma

- Syngaleski

 Wszystkie zapisywanych aparatów [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] systemu obsługują czcionki. [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]czcionki mogą zawierać [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] tabele układu umożliwiające twórcom czcionek projektowanie lepszych, międzynarodowych i wysokiej klasy czcionek typograficznych. Tabele [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] układu czcionek zawierają informacje dotyczące podstawiania glifów, pozycjonowania glifów, justowania i pozycjonowania linii bazowej, umożliwiając aplikacjom do przetwarzania tekstu ulepszanie układu tekstu.

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]czcionki umożliwiają obsługę dużych zestawów glifów przy użyciu [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] kodowania. Takie kodowanie włącza szeroką pomoc techniczną, a także dla wariantów symboli typograficznych.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]renderowanie tekstu jest obsługiwane przez technologię Microsoft ClearType w pikselach, która obsługuje niezależność rozwiązań. Znacznie poprawia to czytelność i zapewnia możliwość obsługi dokumentów w stylu magazynu o wysokiej jakości dla wszystkich skryptów.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Układ Międzynarodowy
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]zapewnia bardzo wygodny sposób obsługi układów poziomych, dwukierunkowych i pionowych. W strukturze <xref:System.Windows.FrameworkElement.FlowDirection%2A> prezentacji właściwość może służyć do definiowania układu. Wzorce kierunku przepływu są następujące:

- *LeftToRight* — układ poziomy dla języków łacińskich, wschodnioazjatyckich i tak dalej.

- *RightToLeft* — dwukierunkowe dla języka arabskiego, hebrajski i tak dalej.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Opracowywanie aplikacji lokalizowalnych
 Podczas pisania aplikacji do użycia globalnego należy pamiętać, że aplikacja musi być lokalizowalna. W poniższych tematach znajdują się informacje, które należy wziąć pod uwagę.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Wielojęzyczny interfejs użytkownika
 Wielojęzycznego interfejsu użytkownika (MUI) to [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)] obsługa przełączania [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] się z jednego języka do innego. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Aplikacja używa modelu zestawu do obsługi interfejsu MUI. Jedna aplikacja zawiera zestawy, które są niezależne od języka, a także zestawy zasobów satelitarnych zależne od języka. Punkt wejścia jest zarządzany. EXE w zestawie głównym.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]moduł ładujący zasoby korzysta z [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]Menedżera zasobów do obsługi wyszukiwania i powrotu zasobów. Zestawy satelickie dla wielu języków współpracują z tym samym zestawem głównym. Załadowany zestaw zasobów zależy <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> od bieżącego wątku.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Lokalizowalny interfejs użytkownika
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje używają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do definiowania ich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]umożliwia deweloperom określenie hierarchii obiektów z zestawem właściwości i logiki. Głównym zastosowaniem programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest programowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, ale może służyć do określania hierarchii dowolnego obiektu środowiska uruchomieniowego języka wspólnego (CLR). Większość deweloperów używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do określania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji i używania języka programowania, takiego jak C# w celu reagowania na interakcję użytkownika.

 Z punktu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] widzenia zasobów plik zaprojektowany do opisywania zależnego od [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] języka jest elementem zasobów i dlatego jego końcowy format dystrybucji musi być Lokalizowalny do obsługi języków międzynarodowych. Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie obsługuje zdarzeń, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] wiele aplikacji zawiera bloki kodu, aby to zrobić. Aby uzyskać więcej informacji, zobacz [XAML — Omówienie (WPF)](xaml-overview-wpf.md). Kod jest usuwany i kompilowany do różnych plików binarnych, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] gdy plik jest w postaci tokenu do formy BAML języka XAML. Forma BAML plików XAML, obrazów i innych typów obiektów zasobów zarządzanych jest osadzona w zestawie zasobów satelitarnych, który można lokalizować w innych językach lub głównym zestawie, gdy lokalizacja nie jest wymagana.

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]aplikacje obsługują wszystkie [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]zasoby środowiska CLR, w tym tabele ciągów, obrazy i tak dalej.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Kompilowanie aplikacji lokalizowalnych
 Lokalizacja oznacza adaptację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do różnych kultur. Aby nawiązać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikację, deweloperzy muszą kompilować wszystkie zasoby lokalizowalne w zestawie zasobów. Zestaw zasobów jest zlokalizowany w różnych językach, a związany z nim kod używa interfejsu API zarządzania zasobami do załadowania. Jednym z plików wymaganych dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji jest plik projektu (. proj). Wszystkie zasoby, które są używane w aplikacji, powinny być uwzględnione w pliku projektu. Poniższy przykład z pliku. csproj pokazuje, jak to zrobić.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Aby użyć zasobu z wystąpieniami <xref:System.Resources.ResourceManager> aplikacji a i załadować zasobu, którego chcesz użyć. Poniższy przykład demonstruje, jak to zrobić.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Używanie technologii ClickOnce z zlokalizowanymi aplikacjami
 ClickOnce to nowa technologia wdrażania Windows Forms, która będzie dostarczana z programem Visual Studio 2005. Umożliwia instalowanie aplikacji i Uaktualnianie aplikacji sieci Web. Gdy aplikacja, która została wdrożona przy użyciu technologii ClickOnce, jest zlokalizowana, może być wyświetlana tylko w zlokalizowanej kulturze. Na przykład jeśli wdrożona aplikacja jest zlokalizowana w języku japońskim, można ją wyświetlać tylko [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] w języku japońskim, a nie w angielskiej wersji systemu Windows. Jest to problem, ponieważ typowym scenariuszem dla użytkowników japońskich jest uruchomienie angielskiej wersji systemu Windows.

 Rozwiązanie tego problemu powoduje ustawienie atrybutu rezerwy języka neutralnego. Deweloper aplikacji może opcjonalnie usunąć zasoby z głównego zestawu i określić, że zasoby można znaleźć w zestawie satelickim odpowiadającym określonej kulturze. Aby sterować tym procesem, <xref:System.Resources.NeutralResourcesLanguageAttribute>Użyj. Konstruktor <xref:System.Resources.NeutralResourcesLanguageAttribute> klasy ma dwa podpisy, jeden, który <xref:System.Resources.UltimateResourceFallbackLocation> przyjmuje parametr, aby <xref:System.Resources.ResourceManager> określić lokalizację, w której powinny zostać wyodrębnione zasoby rezerwowe: zestaw główny lub zestaw satelicki. Poniższy przykład pokazuje, jak używać atrybutu. W przypadku ostatecznej lokalizacji rezerwowej kod powoduje <xref:System.Resources.ResourceManager> wyszukanie zasobów w podkatalogu "de" katalogu aktualnie wykonywanego zestawu.

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Zobacz także

- [Przeglądanie globalizacji i lokalizacji WPF](wpf-globalization-and-localization-overview.md)
