---
title: Przetwarzanie spacji w XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- East Asian characters [XAML Services]
- XAML [XAML Services], whitespace processing
- whitespace processing in XAML [XAML Services]
- characters [XAML Services], East Asian
ms.assetid: cc9cc377-7544-4fd0-b65b-117b90bb0b23
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c382be7dabca90ef201fa24cfb79472955347eef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="whitespace-processing-in-xaml"></a>Przetwarzanie spacji w XAML
Zasady języka XAML stanu, że znaczące światła muszą zostać przetworzone przez [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] implementacji procesora. W tym temacie omówiono te reguły języka XAML. Również dokumentów obsługi dodatkowych spacji jest definiowana za pomocą [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] implementacja procesora XAML i zapisywania XAML do serializacji.  
  
<a name="whitespace_definition"></a>   
## <a name="whitespace-definition"></a>Definicja odstępu  
 Zgodne z [!INCLUDE[TLA2#tla_xml](../../../includes/tla2sharptla-xml-md.md)], znaków odstępu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] to miejsce, wysuwu wiersza i karty. Odpowiadają one [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] wartości 0020, 000A i 0009 odpowiednio.  
  
<a name="whitespace_normalization"></a>   
## <a name="whitespace-normalization"></a>Wartość odstępu  
 Domyślnie następujące normalizacji odstępu występuje podczas [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesów procesora [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] pliku:  
  
1.  Znaki wysuwu wiersza między znaki wschodnioazjatyckie są usuwane. Zobacz sekcję "Znaki wschodnioazjatyckie" w dalszej części tego tematu dla definicji tego terminu.  
  
2.  Wszystkie znaki odstępu (miejsca, wysuwu wiersza, karta) są konwertowane na spacje.  
  
3.  Wszystkie kolejne spacje są usunięty i zastąpiony jednego miejsca.  
  
4.  Odstęp bezpośrednio po tagu początkowego został usunięty.  
  
5.  Odstęp od razu, przed usunięciem tagu końcowego.  
  
 "Domyślny" odnosi się do stanu wskazywane przez wartość domyślną [XML: Space](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md) atrybutu.  
  
<a name="whitespace_in_inner_text_and_string_primitives"></a>   
## <a name="whitespace-in-inner-text-and-string-primitives"></a>Odstęp w tekst wewnętrzny i podstawowych ciągu  
 Poprzednie reguły normalizacji dotyczą wewnętrzny tekst, który znajduje się w obrębie elementów XAML. Po normalizacji procesora XAML konwertuje tekst wewnętrzny do odpowiedniego typu w następujący sposób:  
  
-   Jeśli typ właściwości nie jest kolekcją, ale nie jest bezpośrednio <xref:System.Object> typ procesora XAML próbuje konwertować tego typu za pomocą konwertera jego typu. Konwersja nie powiodło się w tym miejscu powoduje błąd kompilacji.  
  
-   Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny jest ciągły (nie pośredniczące elementu tagów), tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli typ kolekcji nie może zaakceptować <xref:System.String>, powoduje błąd kompilacji.  
  
-   Jeśli typ właściwości jest <xref:System.Object>, tekst wewnętrzny jest analizowany jako pojedynczy <xref:System.String>. Jeśli są aktywne znaczniki elementów, ponieważ powoduje błąd kompilacji <xref:System.Object> typu wymaga pojedynczego obiektu (<xref:System.String> lub w inny sposób).  
  
-   Jeśli typ właściwości jest kolekcją, a tekst wewnętrzny nie jest ciągły, pierwszego podciągu jest konwertowany na <xref:System.String> i dodawane jako elementu kolekcji, pośredniczące element zostanie dodany jako element kolekcji i finally jest końcowe podciąg (jeśli istnieje) dodać do kolekcji w innej <xref:System.String> elementu.  
  
<a name="preserving_whitespace"></a>   
## <a name="preserving-whitespace"></a>Zachowywanie odstępu  
 Istnieje kilka technik zachować odstęp w źródle [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] dla ostatecznego prezentacji, która nie dotyczy [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] normalizacji odstępu procesora.  
  
 **XML: Space = "preserve"**: Określ tego atrybutu na poziomie elementu, w którym wymagane jest zachowanie spacji. Ten zachowuje wszystkie białe miejsca, spacjami dodanych przez edytowanie kodu aplikacji "pretty print" wyrównywanie elementów jako wizualnie intuicyjne zagnieżdżenia. Jednak czy renderowania tych miejscach jest określana przez model zawartości elementu zawierającego. Unikaj określania `xml:space="preserve"` na poziomie głównym ponieważ większość modeli obiektów nie należy traktować odstępu za istotne niezależnie od tego ustawiania atrybutu. Ustawienie `xml:space` globalny może mieć konsekwencje wydajności na przetwarzanie (szczególnie serializacji) w niektórych implementacjach XAML. Jest rozwiązaniem lepsze tylko atrybut w szczególności na poziomie elementów, które renderowania odstępu w ciągach lub są kolekcjami znaczących odstępu.  
  
 **Jednostki i spacje z systemem innym niż podziału**: [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] obsługuje umieszczanie żadnego [!INCLUDE[TLA#tla_unicode](../../../includes/tlasharptla-unicode-md.md)] jednostek w modelu obiektu tekstu. Można użyć dedykowanego jednostek takich jak nierozdzielający miejsca (&\#160; przy użyciu kodowania UTF-8). Można również użyć kontrolek tekstu sformatowanego, które obsługują znaków spacji nierozdzielających. Należy zachować ostrożność Jeśli używasz jednostek do symulowania właściwości układu, takie jak wcięcia, ponieważ dane wyjściowe środowiska wykonawczego jednostek różni się zależnie od większą liczbę czynników nie będzie możliwości do produkcji wyniki wcięcia w typowym układ systemu, na przykład prawidłowego Użyj paneli i marginesów. Na przykład jednostki są mapowane na czcionek i zmieniać rozmiar w odpowiedzi na wybór czcionki użytkownika.  
  
<a name="east_asian_characters"></a>   
## <a name="east-asian-characters"></a>Znaki wschodnioazjatyckie  
 "Znaki wschodnioazjatyckie" jest zdefiniowany jako zestaw [!INCLUDE[TLA2#tla_unicode](../../../includes/tla2sharptla-unicode-md.md)] znak zakresów 20000 U + do U + 2FFFD i U + 30000 do U + 3FFFD. Ten podzestaw jest czasami nazywany "Ideogramy CJK". Aby uzyskać więcej informacji, zobacz [http://www.unicode.org](http://www.unicode.org/).  
  
<a name="whitespace_and_text_content_models"></a>   
## <a name="whitespace-and-text-content-models"></a>Modele zawartości spacja i tekstu  
 W praktyce zachowując spacji jest tylko kwestią w przypadku podzbiór wszystkich możliwych modeli zawartości. Podzbiór ten składa się z zawartości modeli, które można wykonać pojedynczą <xref:System.String> typu w pewnej formy dedykowana <xref:System.String> kolekcji lub kombinację <xref:System.String> i innych typów w <xref:System.Collections.IList> lub <xref:System.Collections.Generic.ICollection%601> kolekcji.  
  
### <a name="whitespace-and-text-content-models-in-wpf"></a>Spacja i tekst modeli zawartości określonych na platformie WPF  
 W celach ilustracyjnych pozostałej części tej sekcji odwołuje się do określonych typach, które są zdefiniowane przez WPF. Funkcje obsługi odstępu, które zostały opisane w tym temacie są zwykle zapewnienie im dostępu do usług .NET Framework XAML i WPF. Aby wyświetlić to zachowanie w akcji, może eksperymentować niektórych znaczników WPF XAML, wyświetlić wyniki na wykresie obiektu i następnie ponownie serializacji do znaczników.  
  
 Nawet w przypadku modeli zawartość, która może zająć ciągów, domyślne zachowanie w tych modelach zawartości jest, że żadnych spacji, który pozostaje nie jest traktowana jako istotne. Na przykład <xref:System.Windows.Controls.ListBox> przyjmuje <xref:System.Collections.IList>, ale whitespace (takie jak znaki wysuwu wiersza między poszczególnymi <xref:System.Windows.Controls.ListBoxItem>) nie są zachowywane i nie są renderowane. Jeśli spróbujesz użyć znaki wysuwu wiersza jako separatora między ciągów dla <xref:System.Windows.Controls.ListBoxItem> elementów, nie działa w ogóle; ciągów, które są rozdzielone przez znaki wysuwu wiersza są traktowane jako jeden ciąg i jeden element.  
  
 Te kolekcje, które Traktuj odstępu za istotne zwykle są częścią modelu przepływu dokumentu. Jest podstawowy kolekcja, która obsługuje zachowanie zachowywania odstępem <xref:System.Windows.Documents.InlineCollection>. Ta klasa kolekcji jest zadeklarowany za pomocą <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>; w przypadku odnalezienia tego atrybutu [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesora za istotne, będą traktować odstępu w kolekcji. Kombinacja `xml:space="preserve"` i odstępów w obrębie <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> wskazywane Kolekcja to czy wszystkie biały znak jest zachowywana i renderowane. Kombinacja `xml:space="default"` i odstępów w obrębie <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> normalizacji spacji początkowej opisanego wcześniej przyczyn, które pozostawia jedno pole w niektórych pozycji, a tych miejscach są zachowywane i renderowane. Jakie zachowanie jest pożądane zależy od użytkownika i należy używać `xml:space` selektywne umożliwienie zachowanie, które mają.  
  
 Ponadto niektórych elementów śródwierszowych, które oznacza rzeczywistej linebreak w modelu dokumentu przepływu celowo nie powinno wprowadzić dodatkowe miejsce nawet w kolekcji znaczących odstępu. Na przykład <xref:System.Windows.Documents.LineBreak> element ma tę samą funkcję co \<BR / > tagów w [!INCLUDE[TLA2#tla_html](../../../includes/tla2sharptla-html-md.md)], a dla czytelności w znaczniku, zwykle <xref:System.Windows.Documents.LineBreak> jest oddzielona od kolejnych tekstu utworzone wysuwu wiersza. Tego wysuwu wiersza nie powinny być znormalizowane do stają się spacje wiodące kolejny wiersz. Aby włączyć to zachowanie definicji klasy dla <xref:System.Windows.Documents.LineBreak> zastosowanie elementu <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>, który następnie jest interpretowany przez [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] procesora oznacza, że otaczającego odstępu <xref:System.Windows.Documents.LineBreak> zawsze jest ograniczona.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Jednostki znaków XML i XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)  
 [xml:space, obsługa w XAML](../../../docs/framework/xaml-services/xml-space-handling-in-xaml.md)
