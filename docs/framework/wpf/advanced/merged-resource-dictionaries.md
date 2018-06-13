---
title: Połączone słowniki zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: f2dc5bbb96d74533e8e77251185a0b105fc55746
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548057"
---
# <a name="merged-resource-dictionaries"></a>Połączone słowniki zasobów
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zasoby obsługuje funkcji słownika zasobów scalone. Ta funkcja udostępnia sposób definiowania zasobów część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji poza skompilowanych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji. Następnie można udostępniać zasoby w aplikacjach i są również więcej wygodny sposób izolowany lokalizacji.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Wprowadzenie do słownika zasobów scalony  
 W znaczniku można użyć następującej składni wprowadzenie słownik zasobów scalone do strony:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Należy pamiętać, że <xref:System.Windows.ResourceDictionary> element nie ma [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md), które są zazwyczaj wymagane dla wszystkich elementów w kolekcji zasobów. Ale innego <xref:System.Windows.ResourceDictionary> odwołanie w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcja jest szczególnych przypadkach, zarezerwowane dla tego scenariusza słownika zasobów scalone. <xref:System.Windows.ResourceDictionary> Powoduje to wprowadzenie scalone słownik zasobów nie może mieć [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md). Zazwyczaj każdego <xref:System.Windows.ResourceDictionary> w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> określa kolekcji <xref:System.Windows.ResourceDictionary.Source%2A> atrybutu. Wartość <xref:System.Windows.ResourceDictionary.Source%2A> powinien być [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] rozwiązań do lokalizacji pliku zasobów do scalenia. Miejsce docelowe tego [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] musi być inny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku z <xref:System.Windows.ResourceDictionary> jako jego elementu głównego.  
  
> [!NOTE]
>  Aby zdefiniować zasoby w ramach dozwolone <xref:System.Windows.ResourceDictionary> jako alternatywę do określania, który jest określony jako słownika scalone <xref:System.Windows.ResourceDictionary.Source%2A>, lub oprócz uwzględniono niezależnie od zasobów z określonego źródła. Jednak to nie jest typowym scenariuszem; główne scenariusz scalonych słownikach polega na scaleniu zasobów z lokalizacji zewnętrznych plików. Jeśli chcesz określić zasobów w ramach znaczników strony, należy zwykle zdefiniować w głównym <xref:System.Windows.ResourceDictionary> , a nie w scalonych słownikach.  
  
## <a name="merged-dictionary-behavior"></a>Zachowanie połączony słownik  
 Zasoby w scalonych słownikach zajmują miejsce w zakres wyszukiwania zasobów, który jest zaraz po zakres słownik zasobów główne, które zostaną scalone. Mimo że klucza zasobów muszą być unikatowe w dowolnej poszczególnych słownika, klucz może istnieć wiele razy w zestawie scalonych słownikach. W takim przypadku zasobów, która jest zwracana będzie pochodził z ostatnich słownik znaleziono sekwencyjnie w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcji. Jeśli <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcji został zdefiniowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kolejność scalonych słownikach w kolekcji to kolejność elementów, zgodnie z znaczników. Jeśli klucz jest zdefiniowany w podstawowym słowniku, a także w słowniku, który został scalony, zasobów, która jest zwracana będzie pochodził z podstawowego słownika. Tych reguł ustawiania zakresu stosowane jednakowo dla odwołania do zasobu statycznych i dynamicznych zasobów odwołań.  
  
### <a name="merged-dictionaries-and-code"></a>Scalonych słownikach i kod  
 Scalonych słownikach mogą być dodawane do `Resources` słownika przy użyciu kodu. Wartość domyślna jest początkowo pusta <xref:System.Windows.ResourceDictionary> znajdujące się w każdej `Resources` właściwość również ma wartość domyślną, początkowo pusta <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> właściwości kolekcji. Aby dodać scalonych słownika przy użyciu kodu, należy uzyskać odwołanie do podstawowej żądany <xref:System.Windows.ResourceDictionary>, pobrać jego <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> wartość właściwości i wywołanie `Add` na ogólnej `Collection` zawarte w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Możesz dodać obiekt musi być nowy <xref:System.Windows.ResourceDictionary>. W kodzie, nie należy ustawiać <xref:System.Windows.ResourceDictionary.Source%2A> właściwości. Zamiast tego należy uzyskać <xref:System.Windows.ResourceDictionary> obiektu przez utworzenie jednego lub jeden ładowania. Aby załadować istniejący <xref:System.Windows.ResourceDictionary> do wywołania <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na istniejącym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strumień plików, który ma <xref:System.Windows.ResourceDictionary> katalogu głównego, następnie rzutowanie <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> zwrócić wartość do <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Identyfikatory URI słownika zasobów scalony  
 Istnieje kilka technik sposobu obejmują słownik scalonych zasobów, które są oznaczone [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] formatu, który będzie używany. Ogólnie rzecz biorąc, te techniki można podzielić na dwie kategorie: zasoby, które są kompilowane jako część projektu i zasobów, które nie są kompilowane w ramach projektu.  
  
 Dla zasobów, które są kompilowane w ramach projektu można użyć ścieżki względnej, która odwołuje się do lokalizacji zasobów. Ścieżka względna jest oceniane podczas kompilacji. Zasób musi być zdefiniowany jako część projektu jako akcja kompilacji zasobu. Jeśli plik .xaml zasobów w projekcie jako zasób, nie trzeba kopiować pliku zasobu do katalogu wyjściowego, zasób jest już uwzględniona w obrębie skompilowanej aplikacji. Można również użyć akcji kompilacji zawartości, ale należy następnie skopiuj pliki do katalogu wyjściowego oraz wdrożyć pliki zasobów w tej samej relacji ścieżka do pliku wykonywalnego.  
  
> [!NOTE]
>  Nie należy używać akcji kompilacji osadzony zasób. Akcja kompilacji, sama jest obsługiwana dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, ale rozpoznanie <xref:System.Windows.ResourceDictionary.Source%2A> nie obejmuje <xref:System.Resources.ResourceManager>i dlatego nie można oddzielić pojedynczego zasobu spoza strumienia. Można nadal używać osadzonego zasobu do innych celów, tak długo, jak również używane <xref:System.Resources.ResourceManager> dostęp do zasobów.  
  
 Powiązane technika jest użycie identyfikatora URI Pack do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików i odwołuje się do niego jako źródło. Adres URI pakietu umożliwia odwołania do składników zestawów występujących w odwołaniach i innych technik. Aby uzyskać więcej informacji na identyfikatory URI pakietu, zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).  
  
 Dla zasobów, które nie są kompilowane w ramach projektu identyfikator URI jest oceniane w czasie wykonywania. Np. w pliku można użyć typowych transportu identyfikatora URI: lub http: Aby odwołać się do pliku zasobów. Wadą podejście Nieskompilowane zasobów jest ten plik: dostępu wymaga dodatkowe kroki wdrażania i http: dostępu oznacza strefy zabezpieczeń Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Ponowne wykorzystywanie scalonych słownikach  
 Można użyć ponownie lub udostępnić scalonych słownikach zasobów między aplikacjami, ponieważ można scalić słownika zasobów może być przywoływany przez dowolne prawidłowe [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Dokładnie tak jak to będzie zależeć od strategii wdrażania aplikacji i która aplikacja modelu należy wykonać. Wyżej wymienione strategii identyfikatora URI elementu Pack umożliwia często źródła scalonych zasobów w wielu projektach podczas tworzenia za pomocą udostępniania odwołania do zestawu. W tym scenariuszu zasoby nadal są dystrybuowane przez klienta, a co najmniej jedną z aplikacji, należy wdrożyć przywoływanego zestawu. Istnieje również możliwość odwołania scalonych zasobów za pomocą rozproszonego identyfikator URI, który korzysta z protokołu http.  
  
 Zapisywanie scalonych słownikach miejscowego plików lub do lokalnego magazynu udostępnionego jest inny możliwe słownik scalonych / scenariusz wdrażania aplikacji.  
  
### <a name="localization"></a>Lokalizacja  
 Jeśli zasoby, które muszą być lokalizowany są izolowane do słowników, które scalone z podstawowego słownika i przechowywane jako utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], te pliki, które może być lokalizowany oddzielnie. Ta technika jest lekki alternatywą do lokalizowania zestawów satelickich zasobów. Aby uzyskać więcej informacji, zobacz [omówienie lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.ResourceDictionary>  
 [Zasoby XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Zasoby i kod](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [Zasoby aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
