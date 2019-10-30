---
title: Globalizacja dla WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: df9c66d47d1f5e345858ae08b3d926d0e938a255
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038322"
---
# <a name="globalization-for-wpf"></a>Globalizacja dla WPF
Ten temat zawiera informacje o problemach, które należy wziąć pod uwagę podczas pisania [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacji dla globalnego rynku. Elementy programistyczne globalizacji są zdefiniowane w .NET w przestrzeni nazw <xref:System.Globalization>.

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>Globalizacja XAML
 Extensible Application Markup Language (XAML) bazuje na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] i wykorzystuje obsługę globalizacji zdefiniowaną w specyfikacji [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. W poniższych sekcjach opisano niektóre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] funkcje, których należy wiedzieć.

<a name="char_reference"></a>
### <a name="character-references"></a>Odwołania do znaków
Odwołanie do znaku daje jednostkę kodu UTF16 określonego znaku Unicode, który reprezentuje, w postaci dziesiętnej lub szesnastkowej. W poniższym przykładzie pokazano odwołanie do znaku dziesiętnego dla COPTIC wielkiej litery, lub "Ϩ":

```
&#1000;
```

W poniższym przykładzie pokazano szesnastkowe odwołanie do znaku. Zwróć uwagę, że ma **symbol x** przed liczbą szesnastkową.

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>Kody
 Kodowanie obsługiwane przez [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to ASCII, Unicode UTF-16 i UTF-8. Instrukcja kodowania znajduje się na początku dokumentu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Jeśli żaden atrybut kodowania nie istnieje i nie ma kolejności bajtów, Analizator domyślnie używa kodowania UTF-8. Kodowanie UTF-8 i UTF-16 są preferowanymi kodowaniami. Kodowanie UTF-7 nie jest obsługiwane. Poniższy przykład ilustruje sposób określania kodowania UTF-8 w pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

```xaml
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>Atrybut Language
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] używa [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) do reprezentowania atrybutu języka elementu.  Aby skorzystać z klasy <xref:System.Globalization.CultureInfo>, wartość atrybutu języka musi być jedną z nazw kultur wstępnie zdefiniowanych przez <xref:System.Globalization.CultureInfo>. [XML: lang](../../xaml-services/xml-lang-handling-in-xaml.md) można dziedziczyć w drzewie elementów (według reguł XML, niekoniecznie ze względu na dziedziczenie właściwości zależności), a jego wartość domyślna to pusty ciąg, jeśli nie jest on jawnie przypisany.

 Atrybut Language jest bardzo przydatny do określania dialektów. Na przykład francuski ma inną pisownię, słownictwo i wymowę w Francji, Quebec, Belgii i Szwajcarii. W standardzie Unicode, a także w językach chińskim, japońskim i koreańskim, ale kształty ideograficzne różnią się od siebie i używają całkowicie różnych czcionek.

 Poniższy przykład [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] używa atrybutu języka `fr-CA`, aby określić kanadyjski francuski.

```xaml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługuje wszystkie funkcje Unicode, w tym surogaty. Tak długo, jak zestaw znaków można zamapować na Unicode, jest obsługiwany. Na przykład GB18030 wprowadza pewne znaki, które są mapowane na rozszerzenia w języku chińskim, japońskim i koreańskim (CFK) a i B i pary dwuskładnikowe, dlatego jest w pełni obsługiwane. Aplikacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] może używać <xref:System.Globalization.StringInfo> do manipulowania ciągami bez względu na to, czy mają one pary zastępcze czy łączenia znaków.

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>Projektowanie międzynarodowego interfejsu użytkownika przy użyciu języka XAML
 W tej sekcji opisano [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] funkcje, które należy wziąć pod uwagę podczas pisania aplikacji.

<a name="intl_text"></a>
### <a name="international-text"></a>Tekst Międzynarodowy
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obejmuje wbudowane przetwarzanie dla wszystkich systemów Microsoft .NET obsługiwanych przez platformę.

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

- -

- Wielka

- Malayalam

- Mongolski

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

 Wszystkie aparaty systemu pisania obsługują czcionki OpenType. Czcionki OpenType mogą zawierać tabele układu OpenType, które umożliwiają twórcom czcionek projektowanie lepszych, międzynarodowych i wysokiej klasy czcionek typograficznych. Tabele układu czcionek OpenType zawierają informacje dotyczące podstawiania glifów, pozycjonowania glifów, justowania i pozycjonowania linii bazowej, umożliwiając aplikacjom do przetwarzania tekstu ulepszanie układu tekstu.

 Czcionki OpenType umożliwiają obsługę dużych zestawów glifów przy użyciu kodowania Unicode. Takie kodowanie włącza szeroką pomoc techniczną, a także dla wariantów symboli typograficznych.

 renderowanie tekstu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest obsługiwane przez technologię Microsoft ClearType w pikselach, która obsługuje niezależność rozwiązań. Znacznie poprawia to czytelność i zapewnia możliwość obsługi dokumentów w stylu magazynu o wysokiej jakości dla wszystkich skryptów.

<a name="intl_layout"></a>
### <a name="international-layout"></a>Układ Międzynarodowy
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zapewnia bardzo wygodny sposób obsługi układów poziomych, dwukierunkowych i pionowych. W środowisku prezentacji Właściwość <xref:System.Windows.FrameworkElement.FlowDirection%2A> może służyć do definiowania układu. Wzorce kierunku przepływu są następujące:

- *LeftToRight* — układ poziomy dla języków łacińskich, wschodnioazjatyckich i tak dalej.

- *RightToLeft* — dwukierunkowe dla języka arabskiego, hebrajski i tak dalej.

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>Opracowywanie aplikacji lokalizowalnych
 Podczas pisania aplikacji do użycia globalnego należy pamiętać, że aplikacja musi być lokalizowalna. W poniższych tematach znajdują się informacje, które należy wziąć pod uwagę.

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>Wielojęzyczny interfejs użytkownika
 Wielojęzycznego interfejsu użytkownika (MUI) to pomoc techniczna firmy Microsoft dla przełączania interfejsów użytkownika z jednego języka do innego. Aplikacja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] używa modelu zestawu do obsługi interfejsu MUI. Jedna aplikacja zawiera zestawy, które są niezależne od języka, a także zestawy zasobów satelitarnych zależne od języka. Punkt wejścia jest zarządzany. EXE w zestawie głównym.  moduł ładujący zasobów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] korzysta z Menedżera zasobów [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]do obsługi wyszukiwania i powrotu zasobów. Zestawy satelickie dla wielu języków współpracują z tym samym zestawem głównym. Załadowany zestaw zasobów zależy od <xref:System.Globalization.CultureInfo.CurrentUICulture%2A> bieżącego wątku.

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>Lokalizowalny interfejs użytkownika
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje używają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do definiowania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pozwala deweloperom na określenie hierarchii obiektów z zestawem właściwości i logiki. Podstawowym zastosowaniem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest opracowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, ale może służyć do określania hierarchii dowolnego obiektu środowiska uruchomieniowego języka wspólnego (CLR). Większość deweloperów używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do określania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikacji i używania języka programowania, takiego jak C# w celu reagowania na interakcję użytkownika.

 Z punktu widzenia zasobów, plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zaprojektowany do opisywania [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zależnych od języka to element zasobów, dlatego jego końcowy format dystrybucji musi być Lokalizowalny do obsługi języków międzynarodowych. Ponieważ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nie może obsługiwać zdarzeń wielu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacje zawierają bloki kodu, aby to zrobić. Aby uzyskać więcej informacji, zobacz [XAML — Omówienie (WPF)](xaml-overview-wpf.md). Kod jest usuwany i kompilowany do różnych plików binarnych, gdy plik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jest zadany przy użyciu tokenu w formie BAML języka XAML. Forma BAML plików XAML, obrazów i innych typów obiektów zasobów zarządzanych jest osadzona w zestawie zasobów satelitarnych, który można lokalizować w innych językach lub głównym zestawie, gdy lokalizacja nie jest wymagana.

> [!NOTE]
> aplikacje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsługują wszystkie [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]zasoby środowiska CLR, w tym tabele ciągów, obrazy i tak dalej.

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>Kompilowanie aplikacji lokalizowalnych
 Lokalizacja oznacza adaptację [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do różnych kultur. Aby nawiązać [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, deweloperzy muszą kompilować wszystkie zasoby lokalizowalne w zestawie zasobów. Zestaw zasobów jest zlokalizowany w różnych językach, a związany z nim kod używa interfejsu API zarządzania zasobami do załadowania. Jednym z plików wymaganych dla aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest plik projektu (. proj). Wszystkie zasoby, które są używane w aplikacji, powinny być uwzględnione w pliku projektu. Poniższy przykład z pliku. csproj pokazuje, jak to zrobić.

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 Aby użyć zasobu w aplikacji, Utwórz wystąpienie <xref:System.Resources.ResourceManager> i Załaduj zasób, którego chcesz użyć. Poniższy przykład demonstruje, jak to zrobić.

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>Używanie technologii ClickOnce z zlokalizowanymi aplikacjami
 ClickOnce to nowa technologia wdrażania Windows Forms, która będzie dostarczana z programem Visual Studio 2005. Umożliwia instalowanie aplikacji i Uaktualnianie aplikacji sieci Web. Gdy aplikacja, która została wdrożona przy użyciu technologii ClickOnce, jest zlokalizowana, może być wyświetlana tylko w zlokalizowanej kulturze. Na przykład jeśli wdrożona aplikacja jest zlokalizowana w języku japońskim, można ją wyświetlać tylko w japońskim systemie Microsoft Windows, a nie w angielskiej wersji systemu Windows. Jest to problem, ponieważ typowym scenariuszem dla użytkowników japońskich jest uruchomienie angielskiej wersji systemu Windows.

 Rozwiązanie tego problemu powoduje ustawienie atrybutu rezerwy języka neutralnego. Deweloper aplikacji może opcjonalnie usunąć zasoby z głównego zestawu i określić, że zasoby można znaleźć w zestawie satelickim odpowiadającym określonej kulturze. Aby kontrolować ten proces, użyj <xref:System.Resources.NeutralResourcesLanguageAttribute>. Konstruktor klasy <xref:System.Resources.NeutralResourcesLanguageAttribute> ma dwa podpisy, jeden, który przyjmuje parametr <xref:System.Resources.UltimateResourceFallbackLocation>, aby określić lokalizację, w której <xref:System.Resources.ResourceManager> powinien wyodrębnić zasoby rezerwowe: zestaw główny lub zestaw satelicki. Poniższy przykład pokazuje, jak używać atrybutu. W przypadku ostatecznej lokalizacji rezerwowej kod powoduje, że <xref:System.Resources.ResourceManager> szuka zasobów w podkatalogu "de" katalogu aktualnie wykonywanego zestawu.

```csharp
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>Zobacz także

- [Przeglądanie globalizacji i lokalizacji WPF](wpf-globalization-and-localization-overview.md)
