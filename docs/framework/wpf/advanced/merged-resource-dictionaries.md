---
title: Połączone słowniki zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 899955a9f3302e67de4efa0ce0cb6baf6bf0ec5d
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559784"
---
# <a name="merged-resource-dictionaries"></a>Połączone słowniki zasobów
zasoby [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] obsługują funkcję scalonego słownika zasobów. Ta funkcja udostępnia sposób definiowania części zasobów aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poza skompilowaną [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji. Zasoby mogą być następnie współużytkowane przez aplikacje i bardziej wygodnie odizolowane pod kątem lokalizacji.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Wprowadzenie do scalonego słownika zasobów  
 W znaczniku należy użyć następującej składni, aby wprowadzić scalony słownik zasobów na stronę:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Należy zauważyć, że element <xref:System.Windows.ResourceDictionary> nie ma [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md), która jest zwykle wymagana dla wszystkich elementów w kolekcji zasobów. Ale inne odwołanie <xref:System.Windows.ResourceDictionary> w ramach kolekcji <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> jest specjalnym przypadkiem zarezerwowanym dla tego scenariusza scalonego słownika zasobów. <xref:System.Windows.ResourceDictionary> wprowadzający scalony słownik zasobów nie może mieć [dyrektywy x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md). Zazwyczaj każda <xref:System.Windows.ResourceDictionary> w kolekcji <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> określa atrybut <xref:System.Windows.ResourceDictionary.Source%2A>. Wartość <xref:System.Windows.ResourceDictionary.Source%2A> powinna być jednolitym identyfikatorem zasobów (URI), który jest rozpoznawany jako lokalizacja pliku zasobów do scalenia. Miejsce docelowe tego identyfikatora URI musi być innym plikiem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], z <xref:System.Windows.ResourceDictionary> jako jego element główny.  
  
> [!NOTE]
> Istnieje możliwość zdefiniowania zasobów w <xref:System.Windows.ResourceDictionary>, który jest określony jako scalony słownik, jako alternatywa dla określenia <xref:System.Windows.ResourceDictionary.Source%2A>lub oprócz zasobów uwzględnionych w określonym źródle. Nie jest to jednak typowy scenariusz; głównym scenariuszem dla scalonych słowników jest scalanie zasobów z zewnętrznych lokalizacji plików. Jeśli chcesz określić zasoby wewnątrz znacznika dla strony, należy zwykle zdefiniować je w głównym <xref:System.Windows.ResourceDictionary>, a nie w scalonych słownikach.  
  
## <a name="merged-dictionary-behavior"></a>Zachowanie scalonego słownika  
 Zasoby w scalonym słowniku zajmują lokalizację w zakresie wyszukiwania zasobów, która jest tuż po zakresie głównego słownika zasobów, do którego są scalane. Chociaż klucz zasobu musi być unikatowy w obrębie dowolnego słownika, klucz może istnieć wiele razy w zestawie scalonych słowników. W takim przypadku zwróconym zasobem będzie wynik ostatniego słownika znaleziony sekwencyjnie w kolekcji <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Jeśli kolekcja <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> została zdefiniowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], to porządek scalonych słowników w kolekcji jest kolejnością elementów, jak to podano w znaczniku. Jeśli klucz jest zdefiniowany w słowniku podstawowym, a także w słowniku, który został scalony, zwrócony zasób będzie pochodzić ze słownika podstawowego. Te reguły określania zakresu są stosowane zarówno w przypadku odwołań do zasobów statycznych, jak i dynamicznych odwołań do zasobów.  
  
### <a name="merged-dictionaries-and-code"></a>Scalone słowniki i kod  
 Scalone słowniki można dodawać do słownika `Resources` za pomocą kodu. Wartość domyślna, początkowo pusta <xref:System.Windows.ResourceDictionary>, która istnieje dla każdej właściwości `Resources` również ma wartość domyślną, początkowo pustą właściwość kolekcji <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Aby dodać scalony słownik za pomocą kodu, uzyskuj odwołanie do żądanej <xref:System.Windows.ResourceDictionary>głównej, Pobierz wartość właściwości <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> i Wywołaj `Add` na ogólnym `Collection`, który jest zawarty w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Dodawany obiekt musi być nowym <xref:System.Windows.ResourceDictionary>. W kodzie nie ustawia się właściwości <xref:System.Windows.ResourceDictionary.Source%2A>. Zamiast tego należy uzyskać <xref:System.Windows.ResourceDictionary> obiektu, tworząc jeden lub ładując go. Jednym ze sposobów ładowania istniejących <xref:System.Windows.ResourceDictionary> do wywoływania <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na istniejącym strumieniu pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] z <xref:System.Windows.ResourceDictionary> głównym, a następnie rzutowania <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> wartości zwracanej na <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Scalone identyfikatory URI słownika zasobów  
 Istnieje kilka technik, w których można uwzględnić scalony słownik zasobów, który jest wskazywany przez format URI (Uniform Resource Identifier), który będzie używany. Ogólnie mówiąc, te techniki można podzielić na dwie kategorie: zasoby, które są kompilowane jako część projektu, i zasoby, które nie są kompilowane w ramach projektu.  
  
 W przypadku zasobów, które są kompilowane w ramach projektu, można użyć ścieżki względnej odwołującej się do lokalizacji zasobu. Ścieżka względna jest oceniana podczas kompilacji. Zasób musi być zdefiniowany jako część projektu jako akcja kompilacji zasobu. Jeśli plik Resource. XAML zostanie uwzględniony w projekcie jako zasób, nie trzeba kopiować pliku zasobów do katalogu wyjściowego, a zasób jest już uwzględniony w skompilowanej aplikacji. Można również użyć akcji tworzenia zawartości, ale należy skopiować pliki do katalogu wyjściowego, a także wdrożyć pliki zasobów w tej samej relacji ścieżki do pliku wykonywalnego.  
  
> [!NOTE]
> Nie należy używać osadzonej akcji tworzenia zasobów. Sama Akcja kompilacji jest obsługiwana w przypadku aplikacji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], ale rozwiązanie <xref:System.Windows.ResourceDictionary.Source%2A> nie zawiera <xref:System.Resources.ResourceManager>i w ten sposób nie może oddzielić poszczególnych zasobów ze strumienia. Zasób osadzony nadal można używać do innych celów, tak długo, jak również <xref:System.Resources.ResourceManager> uzyskać dostęp do zasobów.  
  
 Pokrewna Technika polega na użyciu identyfikatora URI pakietu do pliku [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i zaodwoływania się do niego jako źródło. Pakiet URI pakietu umożliwia odwołania do składników przywoływanych zestawów i innych technik. Aby uzyskać więcej informacji o identyfikatorach URI pakietów, zobacz artykuł [Aplikacja WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 W przypadku zasobów, które nie są kompilowane w ramach projektu, identyfikator URI jest oceniany w czasie wykonywania. Możesz użyć wspólnego transportu URI, takiego jak File: lub http:, aby odwołać się do pliku zasobów. Wadą korzystania z nieskompilowanego podejścia do zasobów jest to, że plik: dostęp wymaga dodatkowych kroków wdrożenia i http: dostęp do strefy zabezpieczeń sieci Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Używanie scalonych słowników  
 Można ponownie użyć lub udostępnić scalone słowniki zasobów między aplikacjami, ponieważ słownik zasobów do scalenia może być przywoływany przez dowolny prawidłowy identyfikator URI (Uniform Resource Identifier). Dokładnie tak, jak to zrobisz, będzie zależeć od strategii wdrażania aplikacji i modelu aplikacji, z którego korzystasz. Zgodnie z powyższym strategią dotyczącą identyfikatora URI pakietu zapewnia ona powszechnie Źródło scalonego zasobu w wielu projektach podczas opracowywania przez udostępnienie odwołania do zestawu. W tym scenariuszu zasoby są nadal dystrybuowane przez klienta, a co najmniej jedna z aplikacji musi wdrożyć przywoływany zestaw. Istnieje również możliwość odwoływania się do scalonych zasobów za pośrednictwem rozproszonego identyfikatora URI, który używa protokołu HTTP.  
  
 Pisanie scalonych słowników jako plików lokalnych aplikacji lub do lokalnego magazynu udostępnionego jest innym możliwym scenariuszem wdrożenia słownika/aplikacji.  
  
### <a name="localization"></a>Lokalizacja  
 Jeśli zasoby, które muszą być zlokalizowane, są izolowane do słowników, które są scalane w słowniki podstawowe i są przechowywane jako luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], te pliki można lokalizować osobno. Ta technika jest lekkim alternatywą dla lokalizowania satelitarnych zestawów zasobów. Aby uzyskać szczegółowe informacje, zobacz [Omówienie globalizacji i lokalizacji platformy WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- [Zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Zasoby i kod](resources-and-code.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
