---
title: Połączone słowniki zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 466a18a58acfebf6d779a1d0eba3d2637743806e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911729"
---
# <a name="merged-resource-dictionaries"></a>Połączone słowniki zasobów
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zasoby obsługują funkcję scalonego słownika zasobów. Ta funkcja udostępnia sposób definiowania części [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zasobów aplikacji poza skompilowaną [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacją. Zasoby mogą być następnie współużytkowane przez aplikacje i bardziej wygodnie odizolowane pod kątem lokalizacji.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Wprowadzenie do scalonego słownika zasobów  
 W znaczniku należy użyć następującej składni, aby wprowadzić scalony słownik zasobów na stronę:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Należy zauważyć, <xref:System.Windows.ResourceDictionary> że element nie ma [dyrektywy x:Key](../../xaml-services/x-key-directive.md), która jest zwykle wymagana dla wszystkich elementów w kolekcji zasobów. Ale inne <xref:System.Windows.ResourceDictionary> odwołanie <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> w kolekcji jest specjalnym przypadkiem zarezerwowanym dla tego scenariusza scalonego słownika zasobów. Wprowadzenie opisu scalonego słownika zasobów nie może mieć [dyrektywy x:Key.](../../xaml-services/x-key-directive.md) <xref:System.Windows.ResourceDictionary> Zazwyczaj każdy <xref:System.Windows.ResourceDictionary> element <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> wkolekcjiokreślaatrybut<xref:System.Windows.ResourceDictionary.Source%2A> . Wartość <xref:System.Windows.ResourceDictionary.Source%2A> powinna[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] być rozpoznawana jako lokalizacja pliku zasobów, który ma zostać scalony. Lokalizacją docelową tego [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] programu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] musi być inny <xref:System.Windows.ResourceDictionary> plik jako element główny.  
  
> [!NOTE]
> Istnieje możliwość zdefiniowania zasobów w ramach <xref:System.Windows.ResourceDictionary> , który jest określony jako scalony słownik, jako alternatywa do określenia <xref:System.Windows.ResourceDictionary.Source%2A>, lub oprócz zasobów uwzględnionych w określonym źródle. Nie jest to jednak typowy scenariusz; głównym scenariuszem dla scalonych słowników jest scalanie zasobów z zewnętrznych lokalizacji plików. Jeśli chcesz określić zasoby wewnątrz znaczników dla strony, zazwyczaj należy je zdefiniować w głównym <xref:System.Windows.ResourceDictionary> , a nie w scalonych słownikach.  
  
## <a name="merged-dictionary-behavior"></a>Zachowanie scalonego słownika  
 Zasoby w scalonym słowniku zajmują lokalizację w zakresie wyszukiwania zasobów, która jest tuż po zakresie głównego słownika zasobów, do którego są scalane. Chociaż klucz zasobu musi być unikatowy w obrębie dowolnego słownika, klucz może istnieć wiele razy w zestawie scalonych słowników. W takim przypadku zwrócony zasób będzie pochodzący z ostatniego słownika znalezionego sekwencyjnie w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcji. Jeśli kolekcja została zdefiniowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], wówczas kolejność scalonych słowników w kolekcji jest kolejnością elementów, jak to podano w znaczniku. <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> Jeśli klucz jest zdefiniowany w słowniku podstawowym, a także w słowniku, który został scalony, zwrócony zasób będzie pochodzić ze słownika podstawowego. Te reguły określania zakresu są stosowane zarówno w przypadku odwołań do zasobów statycznych, jak i dynamicznych odwołań do zasobów.  
  
### <a name="merged-dictionaries-and-code"></a>Scalone słowniki i kod  
 Scalone słowniki można dodawać do `Resources` słownika za pomocą kodu. Wartość domyślna, początkowo pusta <xref:System.Windows.ResourceDictionary> , która istnieje dla `Resources` każdej właściwości, ma również domyślną właściwość kolekcji <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> , która jest początkowo pusta. Aby dodać scalony słownik za pomocą kodu, uzyskuj odwołanie do żądanego elementu podstawowego <xref:System.Windows.ResourceDictionary>, Pobierz jego <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> wartość właściwości i Wywołaj `Add` na ogólny `Collection` , który jest zawarty w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Dodawany obiekt musi być nowym <xref:System.Windows.ResourceDictionary>. W kodzie nie ustawia się <xref:System.Windows.ResourceDictionary.Source%2A> właściwości. Zamiast tego należy uzyskać <xref:System.Windows.ResourceDictionary> obiekt, tworząc jeden lub ładując go. Jednym <xref:System.Windows.ResourceDictionary> ze sposobów ładowania istniejącej do wywołania <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] istniejącego strumienia plików, <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> który ma <xref:System.Windows.ResourceDictionary> element główny, a następnie Rzutowanie wartości zwracanej na <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Scalone identyfikatory URI słownika zasobów  
 Istnieje kilka technik, w których można uwzględnić scalony słownik zasobów, który jest wskazywany przez [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] używany format. Ogólnie mówiąc, te techniki można podzielić na dwie kategorie: zasoby, które są kompilowane jako część projektu, i zasoby, które nie są kompilowane w ramach projektu.  
  
 W przypadku zasobów, które są kompilowane w ramach projektu, można użyć ścieżki względnej odwołującej się do lokalizacji zasobu. Ścieżka względna jest oceniana podczas kompilacji. Zasób musi być zdefiniowany jako część projektu jako akcja kompilacji zasobu. Jeśli plik Resource. XAML zostanie uwzględniony w projekcie jako zasób, nie trzeba kopiować pliku zasobów do katalogu wyjściowego, a zasób jest już uwzględniony w skompilowanej aplikacji. Można również użyć akcji tworzenia zawartości, ale należy skopiować pliki do katalogu wyjściowego, a także wdrożyć pliki zasobów w tej samej relacji ścieżki do pliku wykonywalnego.  
  
> [!NOTE]
> Nie należy używać osadzonej akcji tworzenia zasobów. Sama Akcja kompilacji jest obsługiwana w przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji, ale <xref:System.Windows.ResourceDictionary.Source%2A> rozwiązanie <xref:System.Resources.ResourceManager>nie zawiera i nie może oddzielić poszczególnych zasobów poza strumień. Zasób osadzony nadal może być używany do innych celów, tak długo, jak <xref:System.Resources.ResourceManager> również do uzyskiwania dostępu do zasobów.  
  
 Pokrewna Technika polega na użyciu identyfikatora URI pakietu do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku i odwołując się do niego jako źródło. Pakiet URI pakietu umożliwia odwołania do składników przywoływanych zestawów i innych technik. Aby uzyskać więcej informacji o identyfikatorach URI pakietów, zobacz artykuł [Aplikacja WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 W przypadku zasobów, które nie są kompilowane w ramach projektu, identyfikator URI jest oceniany w czasie wykonywania. Możesz użyć wspólnego transportu URI, takiego jak File: lub http:, aby odwołać się do pliku zasobów. Wadą korzystania z nieskompilowanego podejścia do zasobów jest to, że plik: dostęp wymaga dodatkowych kroków wdrożenia i http: dostęp do strefy zabezpieczeń sieci Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Używanie scalonych słowników  
 Można ponownie użyć i udostępnić scalone słowniki zasobów między aplikacjami, ponieważ słownik zasobów do scalenia może być przywoływany przez dowolny prawidłowy [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Dokładnie tak, jak to zrobisz, będzie zależeć od strategii wdrażania aplikacji i modelu aplikacji, z którego korzystasz. Zgodnie z powyższym strategią dotyczącą identyfikatora URI pakietu zapewnia ona powszechnie Źródło scalonego zasobu w wielu projektach podczas opracowywania przez udostępnienie odwołania do zestawu. W tym scenariuszu zasoby są nadal dystrybuowane przez klienta, a co najmniej jedna z aplikacji musi wdrożyć przywoływany zestaw. Istnieje również możliwość odwoływania się do scalonych zasobów za pośrednictwem rozproszonego identyfikatora URI, który używa protokołu HTTP.  
  
 Pisanie scalonych słowników jako plików lokalnych aplikacji lub do lokalnego magazynu udostępnionego jest innym możliwym scenariuszem wdrożenia słownika/aplikacji.  
  
### <a name="localization"></a>Lokalizacja  
 Jeśli zasoby, które muszą być zlokalizowane, są izolowane do słowników, które są scalane w słowniki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]podstawowe i są przechowywane jako luźne, te pliki można lokalizować osobno. Ta technika jest lekkim alternatywą dla lokalizowania satelitarnych zestawów zasobów. Aby uzyskać szczegółowe informacje, zobacz [Omówienie globalizacji i lokalizacji platformy WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
