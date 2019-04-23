---
title: Połączone słowniki zasobów
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 17dd8e0c02d71fc7e72800fc578866188d03060e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097242"
---
# <a name="merged-resource-dictionaries"></a>Połączone słowniki zasobów
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zasobów obsługują funkcję słownika scalonych zasobów. Ta funkcja udostępnia sposób definiowania zasobów część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji poza skompilowana klasa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji. Następnie mogą udostępniać zasoby w aplikacjach i są również więcej wygodnie izolowane dla lokalizacji.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Wprowadzenie do słownika scalonych zasobów  
 Wprowadzenie słownika scalonych zasobów do strony, w znaczniku, użyj następującej składni:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Należy pamiętać, że <xref:System.Windows.ResourceDictionary> element nie może zostać [x: Key — dyrektywa](../../xaml-services/x-key-directive.md), co jest zazwyczaj wymagane dla wszystkich elementów w kolekcji zasobów. Ale innego <xref:System.Windows.ResourceDictionary> odwoływać się w obrębie <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcja jest to szczególny przypadek, zarezerwowane dla tego scenariusza słownika scalonych zasobów. <xref:System.Windows.ResourceDictionary> Powoduje to wprowadzenie scalone słownik zasobów nie może mieć [x: Key — dyrektywa](../../xaml-services/x-key-directive.md). Zazwyczaj każdy <xref:System.Windows.ResourceDictionary> w ramach <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> Określa, kolekcji <xref:System.Windows.ResourceDictionary.Source%2A> atrybutu. Wartość <xref:System.Windows.ResourceDictionary.Source%2A> powinien być [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] rozwiązań do lokalizacji pliku zasobów do scalenia. Miejsce docelowe, [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] musi być innym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku, za pomocą <xref:System.Windows.ResourceDictionary> jako element główny.  
  
> [!NOTE]
>  Jest legalne, aby zdefiniować zasoby w ramach <xref:System.Windows.ResourceDictionary> jako alternatywa do określania, który jest określony jako scalonych słowników <xref:System.Windows.ResourceDictionary.Source%2A>, lub oprócz dowolne zasoby są uwzględniane pochodzących z określonego źródła. Jednak nie jest to typowy scenariusz; główne scenariusz scalonymi słownikami polega na scaleniu zasoby z lokalizacji pliku zewnętrznego. Jeśli chcesz określić zasoby w ramach kodu znaczników dla strony, należy zwykle zdefiniować w głównym <xref:System.Windows.ResourceDictionary> , a nie w scalonych słowników.  
  
## <a name="merged-dictionary-behavior"></a>Zachowanie scalonych słowników  
 Zasoby w scalonych słowników zajmują miejsce w zakresie wyszukiwania zasobów, który jest zaraz po zakres słownik zasobów główne, które zostaną scalone. Mimo że klucz zasobu musi być unikatowa w obrębie dowolnej słowniku poszczególnych, klucz może istnieć wiele razy z zestawu scalonych słowników. W tym przypadku zasobu, który jest zwracany będą pochodzić z ostatnich słownik znaleźć sekwencyjnie w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcji. Jeśli <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> Kolekcja została zdefiniowana w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kolejność scalonymi słownikami w kolekcji to kolejność elementów zgodnie z postanowieniami w znaczniku. Jeśli klucz jest zdefiniowany w podstawowym słowniku, a także w słowniku, która została scalona, zasób, który jest zwracany będzie pochodził z podstawowego słownika. Te zasady zakresu stosuje się jednakowo zarówno dla odwołania do zasobów statycznych i dynamicznych zasobów odwołania.  
  
### <a name="merged-dictionaries-and-code"></a>Scalonymi słownikami i kod  
 Scalonymi słownikami, mogą być dodawane do `Resources` słownik za pomocą kodu. Wartość domyślna jest początkowo pusta <xref:System.Windows.ResourceDictionary> znajdujące się dla każdego `Resources` właściwość ma również domyślnie początkowo pusta <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> właściwości kolekcji. Aby dodać scalonych słowników za pomocą kodu, Uzyskaj odwołanie do żądanego podstawowej <xref:System.Windows.ResourceDictionary>, Uzyskaj jej <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> wartości właściwości i wywołania `Add` na ogólnej `Collection` zawarta w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>. Obiekt, możesz dodać, musi być nową <xref:System.Windows.ResourceDictionary>. W kodzie, nie należy ustawiać <xref:System.Windows.ResourceDictionary.Source%2A> właściwości. Zamiast tego należy uzyskać <xref:System.Windows.ResourceDictionary> obiektu przez utworzenie jednego lub jeden ładowania. Jednym sposobem, aby załadować istniejący <xref:System.Windows.ResourceDictionary> do wywołania <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na istniejącym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strumienia pliku, który ma <xref:System.Windows.ResourceDictionary> katalogu głównego, następnie rzutowanie <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> wartości zwracanej, aby <xref:System.Windows.ResourceDictionary>.  
  
### <a name="merged-resource-dictionary-uris"></a>Identyfikatory URI słownika scalonych zasobów  
 Istnieje kilka technik, jak dołączyć słownika scalonych zasobów, które są wskazywane przez [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] formatu, który będzie używany. Ogólnie rzecz biorąc, techniki te można podzielić na dwie kategorie: zasoby, które są kompilowane jako część projektu i zasobów, które nie są kompilowane w ramach projektu.  
  
 Dla zasobów, które są kompilowane w ramach projektu można użyć ścieżki względnej, która odwołuje się do lokalizacji zasobów. Ścieżka względna jest oceniany podczas kompilacji. Zasób musi być zdefiniowany jako część projektu jako akcji kompilacji zasobów. Jeśli dodasz plik .xaml zasobów w projekcie jako zasób, nie należy skopiować plik zasobów do katalogu wyjściowego, zasób jest już dołączona w skompilowanej aplikacji. Można również użyć akcji kompilacji zawartości, ale należy następnie skopiuj pliki do katalogu wyjściowego i również wdrożyć pliki zasobów w tej samej relacji ścieżkę do pliku wykonywalnego.  
  
> [!NOTE]
>  Nie należy używać akcji kompilacji osadzonego zasobu. Akcja kompilacji, sama jest obsługiwana w przypadku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, ale rozdzielczość <xref:System.Windows.ResourceDictionary.Source%2A> zawierają <xref:System.Resources.ResourceManager>i w związku z tym nie można oddzielić pojedynczy zasób poza strumienia. Można nadal korzystać z zasobów osadzonych, do innych celów, tak długo, jak również używane <xref:System.Resources.ResourceManager> dostępu do zasobów.  
  
 Pokrewną techniką jest użycie identyfikatora URI pakietu do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku i odwoływać się do niego jako źródła. Identyfikator URI pakietu umożliwia odwołania do składników przywoływanych zestawach i innych technik. Aby uzyskać więcej informacji na temat identyfikatorów URI pakietu, zobacz [zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 Dla zasobów, które nie są kompilowane w ramach projektu identyfikator URI jest oceniane w czasie wykonywania. Można użyć typowych transportu identyfikatora URI, takich jak plik: lub http: do odwoływania się do pliku zasobów. Przy użyciu podejścia Nieskompilowane zasobów wadą jest to ten plik: dostępu wymaga dodatkowe kroki wdrażania i http: dostępu oznacza strefy zabezpieczeń Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Ponowne użycie scalonymi słownikami  
 Można ponownie użyć lub połączone słowniki zasobów między aplikacjami, ponieważ słownika zasobów, aby scalić mogą być przywoływane przez dowolne prawidłowe [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]. Dokładnie tak jak to zrobić zależy od strategii wdrażania aplikacji i modelu danej aplikacji, należy wykonać. Wymienione wyżej strategii identyfikatora URI pakietu zapewnia sposób często źródła scalonych zasobów w wielu projektach podczas programowania, udostępniając odwołania do zestawu. W tym scenariuszu zasoby nadal są dystrybuowane przez klienta, a co najmniej jedną z aplikacji, należy wdrożyć przywoływanego zestawu. Istnieje również możliwość odwołania scalonych zasobów za pomocą rozproszonej identyfikator URI, który korzysta z protokołu http.  
  
 Zapisywanie scalonymi słownikami, lokalnych aplikacji, plików lub w lokalnym magazynie udostępnionym jest inny możliwe scalonych słowników / scenariusz wdrażania aplikacji.  
  
### <a name="localization"></a>Lokalizacja  
 W przypadku zasobów, które mają być lokalizowane izolowane słowników, które została scalona z podstawowego słowników i przechowywane jako luźne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], te pliki, które może być lokalizowana oddzielnie. Ta technika jest uproszczone alternatywą do lokalizowania zestawów zasobów satelickich. Aby uzyskać więcej informacji, zobacz [Przegląd lokalizacja i globalizacja WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.ResourceDictionary>
- [Zasoby XAML](xaml-resources.md)
- [Zasoby i kod](resources-and-code.md)
- [Zasoby aplikacji WPF, zawartość i pliki danych](../app-development/wpf-application-resource-content-and-data-files.md)
