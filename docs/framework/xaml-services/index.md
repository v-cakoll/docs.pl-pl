---
title: Usługi XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: fbe67e81bdc461e290b5cdbb9e1050aec32ce8fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566837"
---
# <a name="xaml-services"></a>Usługi XAML
W tym temacie opisano funkcje zestawu technologii, znany jako .NET Framework XAML usług. Większość usług i interfejsów API opisanego znajdują się w zestawie System.Xaml, która jest zestawem wprowadzone w systemie [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zbiór zestawów platformy .NET core. Usługi obejmują fabryki czytelników i moduły zapisujące klasy schematu i obsługi schematu, przypisywanie klas, wewnętrzne obsługę języka XAML i inne funkcje języka XAML.  
  
## <a name="about-this-documentation"></a>Informacje o tej dokumentacji  
 Dokumentacja koncepcyjna dla usług .NET Framework XAML założono, że doświadczenia z języka XAML i sposobu jego mogą być stosowane do określonej platformy, na przykład [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] lub programu Windows Workflow Foundation lub funkcji określonych technologii obszar, na przykład dostosowania kompilacji funkcje w <xref:Microsoft.Build.Framework.XamlTypes>. Ta dokumentacja nie jest podejmowana próba opisano podstawy XAML jako język, terminologii składni języka XAML lub innych materiałów wstępne. Zamiast tego w tej dokumentacji koncentruje się na specjalnie przy użyciu usług .NET Framework XAML, które są włączone w bibliotece System.Xaml zestawu. Większość tych interfejsów API ma dla scenariuszy integracji języka XAML i rozszerzeń. Może to być jedną z następujących czynności:  
  
-   Rozszerzanie możliwości podstawowej czytników XAML lub autorów XAML (bezpośrednio przetwarzania strumień węzłów XAML; wyprowadzanie własne czytnika XAML lub zapis XAML).  
  
-   Definiowanie typów niestandardowych można używać języka XAML, które nie mają określonej platformy zależności i przypisywanie typów w celu przedstawienia ich XAML typu właściwości do usług .NET Framework XAML.  
  
-   Hosting czytniki XAML lub autorów XAML jako część aplikacji, takich jak wizualnego projektanta lub interakcyjne edytora XAML znaczników źródeł.  
  
-   Zapisywanie konwertery wartości XAML (rozszerzenia znaczników; typy konwerterów dla niestandardowych typów).  
  
-   Definiowanie niestandardowego kontekst schematu XAML (przy użyciu alternatywnych metod ładowania zestawu źródeł typ zapasowy; przy użyciu technik wyszukiwania znane typy zamiast zawsze odzwierciedlające zestawy; przy użyciu załadowanego zestawu pojęcia, które nie korzystają z środowiska CLR `AppDomain` i jego model skojarzony zabezpieczeń).  
  
-   Rozszerzanie podstawowego systemu typu XAML.  
  
-   Przy użyciu `Lookup` lub `Invoker` technik w celu wywierania wpływu XAML wpisz systemu i jak są analizowane podłoża typu.  
  
 Jeśli szukasz wprowadzające informacje na języku XAML jako język, możesz spróbować [omówienie XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Ten temat omówiono XAML na odbiorców, którzy nowego zarówno do [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] i również przy użyciu znaczników XAML i funkcje języka XAML. Innym dokumencie przydatne jest wprowadzające informacje w [specyfikacja języka XAML](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>Usługi XAML .NET framework i System.Xaml architektury .NET  
 W poprzednich wersjach programu Microsoft .NET Framework, obsługuje dla XAML — funkcje językowe została zaimplementowana przez platformy, które oparty na programie Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], programu Windows Workflow Foundation i Windows Communication Foundation (WCF)), a więc zróżnicowana w jego zachowanie i interfejsu API używany w zależności od tego, które określonej platformy były używane. Obejmuje XAML analizatora i jego obiektu wykresu mechanizm tworzenia, funkcje wewnętrzne języka XAML, obsługi serializacji i tak dalej.  
  
 W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], usługi XAML .NET Framework i zestawu System.Xaml zdefiniować wiele co jest potrzebne do obsługi funkcji języka XAML. Dotyczy to również klas podstawowych dla czytników XAML i zapisywania XAML. Najważniejsze funkcja dodana do usług XAML .NET Framework, która nie była obecna w innych implementacjach XAML określonej struktury jest reprezentacja system typu dla XAML. Reprezentacja typu systemu przedstawia XAML w sposób zorientowane obiektowo koncentruje się na funkcjach XAML bez konieczności przełączania zależności na określone możliwości platform.  
  
 System typów języka XAML nie jest ograniczona przez formularz znaczników lub charakterystykę środowiska wykonawczego pochodzenia XAML; nie jest ograniczona przez żadnych szczególnych bazowego typu systemu. System typów języka XAML zawiera reprezentacje obiektów dla typów, elementy członkowskie, kontekst schematu XAML, koncepcje poziomie XML i innych pojęcia dotyczące języka XAML lub funkcje wewnętrzne XAML. Za pomocą lub rozszerzanie system typów języka XAML umożliwia pochodzi od klasy, takich jak czytniki XAML i zapisywania XAML i rozszerzyć funkcjonalność reprezentacje XAML do określonych funkcji włączane przez strukturę, technologia lub aplikacji, która wykorzystuje lub emituje XAML. Pojęcie kontekst schematu XAML umożliwia operacje zapisu dla obiekt praktyczne wykres z kombinacji XAML obiektu składnika zapisywania implementacji programu to technologia bazowego typu systemu jako przekazywane za pośrednictwem informacji o zestawie w kontekście i węzłów XAML źródło. Aby uzyskać więcej informacji na temat koncepcji schematu XAML. zobacz [domyślny kontekst schematu XAML i kontekst schematu WPF XAML](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Strumienie węzłów XAML, czytników XAML i zapisywania XAML  
 Aby zrozumieć rolę, jaką odgrywa usług .NET Framework XAML w relacji między języka XAML i określonych technologii, które używają jako języka XAML, warto zrozumienie pojęcia strumień węzłów XAML i jak tą koncepcją shapes interfejsu API i terminologia z zakresu. Strumień węzłów XAML jest koncepcyjny pośredni między reprezentację języka XAML i XAML reprezentujący lub definiuje wykres obiektu.  
  
-   Czytnik XAML jest jednostka, która przetwarza XAML w jakiejś formie i tworzy strumień węzłów XAML. W interfejsie API czytnik XAML jest reprezentowany przez klasę podstawową <xref:System.Xaml.XamlReader>.  
  
-   Edytor XAML jest jednostka, która przetwarza strumień węzłów XAML i tworzy coś innego. W interfejsie API, Edytor XAML jest reprezentowany przez klasę podstawową <xref:System.Xaml.XamlWriter>.  
  
 Dwa najbardziej typowych scenariuszy obejmujących XAML są ładowania kodu XAML do utworzenia wystąpienia wykres obiektu i zapisywania wykresu obiektów z aplikacji lub narzędzia i produkcji reprezentację XAML (zazwyczaj postać znaczników zapisany jako plik tekstowy). Ładowanie XAML i tworzenie wykresu obiektów jest często określonych w tej dokumentacji jako ścieżka obciążenia. Zapisywanie lub istniejący wykres serializacji obiektu w języku XAML jest często określany w tej dokumentacji jako Zapisz ścieżkę.  
  
 Najczęściej spotykanym typem ścieżki obciążenia można przedstawić w następujący sposób:  
  
-   Rozpoczynać reprezentację XAML w formacie XML kodowany w formacie UTF i zapisany jako plik tekstowy.  
  
-   Ładowanie tego XAML do <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> jest <xref:System.Xaml.XamlReader> podklasy.  
  
-   Wynik jest strumień węzłów XAML. Są dostępne poszczególne węzły użycia strumienia węzłów XAML <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> interfejsu API. Najbardziej typową operację w tym miejscu jest odszukaj strumień węzłów XAML przetwarzania każdego węzła za pomocą "bieżącego rekordu" metaphor.  
  
-   Przekazywania wynikowy węzłów z strumień węzłów XAML do <xref:System.Xaml.XamlObjectWriter> interfejsu API. <xref:System.Xaml.XamlObjectWriter> jest <xref:System.Xaml.XamlWriter> podklasy.  
  
-   <xref:System.Xaml.XamlObjectWriter> Zapisuje wykres obiektu, jeden obiekt w czasie, zgodnie z postępu za pośrednictwem strumień węzłów XAML źródła. Jest to realizowane przy pomocy kontekst schematu XAML i implementację, która ma dostęp do zestawów i typy bazowego typu systemu i framework.  
  
-   Wywołanie <xref:System.Xaml.XamlObjectWriter.Result%2A> końcem strumienia węzłów XAML, aby uzyskać obiekt główny wykresu obiektu.  
  
 Najczęściej spotykanym typem z ścieżkę zapisu można przedstawić w następujący sposób:  
  
-   Rozpocznij od wykres obiektu czasu uruchomienia aplikacji, zawartości interfejsu użytkownika i stan czasu wykonywania, lub mniejsze segment reprezentację obiektu ogólną aplikacji w czasie wykonywania.  
  
-   Z obiektu start logicznych, takich jak katalog główny aplikacji lub głównego dokumentu załadować obiektów w <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> jest <xref:System.Xaml.XamlReader> podklasy.  
  
-   Wynik jest strumień węzłów XAML. Są dostępne poszczególne węzły użycia strumienia węzłów XAML <xref:System.Xaml.XamlObjectReader> i <xref:System.Xaml.XamlReader> interfejsu API. Najbardziej typową operację w tym miejscu jest odszukaj strumień węzłów XAML przetwarzania każdego węzła za pomocą "bieżącego rekordu" metaphor.  
  
-   Przekazywania wynikowy węzłów z strumień węzłów XAML do <xref:System.Xaml.XamlXmlWriter> interfejsu API. <xref:System.Xaml.XamlXmlWriter> jest <xref:System.Xaml.XamlWriter> podklasy.  
  
-   <xref:System.Xaml.XamlXmlWriter> Zapisuje XAML w formacie XML UTF kodowania. To można zapisać jako plik tekstowy, jako strumień lub w innych formularzy.  
  
-   Wywołanie <xref:System.Xaml.XamlXmlWriter.Flush%2A> uzyskanie do pliku wyjściowego.  
  
 Aby uzyskać więcej informacji o pojęciach strumień węzłów XAML, zobacz [opis XAML węzła strukturami i koncepcjami strumienia](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>Klasa XamlServices  
 Nie zawsze jest konieczne w celu zaradzenia strumień węzłów XAML. Chcąc ścieżka podstawowa obciążenia lub basic ścieżkę zapisu, można użyć interfejsów API w <xref:System.Xaml.XamlServices> klasy.  
  
-   Podpisy różnych <xref:System.Xaml.XamlServices.Load%2A> zaimplementować ścieżki obciążenia. Albo można załadować pliku lub strumienia lub załadować <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> lub <xref:System.Xaml.XamlReader> który zawijać dane wejściowe XAML przez ładowanie z interfejsami API tego czytnika.  
  
-   Różnych podpisów <xref:System.Xaml.XamlServices.Save%2A> zapisać wykres obiektu i generowania danych wyjściowych jako strumienia pliku, lub <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> wystąpienia.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> Konwertuje XAML łącząc ścieżki obciążenia i Zapisz ścieżkę jako jedna operacja. Kontekst inny schemat lub różnych bazowego typu systemu może służyć do <xref:System.Xaml.XamlReader> i <xref:System.Xaml.XamlWriter>, która jest, co wpływa na sposób jest przekształcana wynikowy XAML.  
  
 Aby uzyskać więcej informacji o sposobie używania <xref:System.Xaml.XamlServices>, zobacz [klasa XAMLServices i podstawowy odczyt XAML lub zapisywania](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>System typów języka XAML  
 System typów języka XAML udostępnia interfejsy API, które są wymagane do pracy z danego węzła poszczególnych strumienia węzłów XAML.  
  
 <xref:System.Xaml.XamlType> jest reprezentacja dla obiekt — co to są przetwarzania między węzła obiektu początkowego i końcowego obiektu węzła.  
  
 <xref:System.Xaml.XamlMember> jest reprezentacja elementu członkowskiego obiektu — co to są przetwarzania między węzeł elementu członkowskiego początkowy i końcowy węzeł elementu członkowskiego.  
  
 Interfejsy API, takich jak <xref:System.Xaml.XamlType.GetAllMembers%2A> i <xref:System.Xaml.XamlType.GetMember%2A> i <xref:System.Xaml.XamlMember.DeclaringType%2A> raport relacje między <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>.  
  
 Domyślne zachowanie system typów języka XAML zaimplementowanego usług .NET Framework XAML opiera się na środowisko uruchomieniowe języka wspólnego (CLR) i analizy statycznej typów CLR w zestawach za pomocą odbicia. Dla określonego typu CLR, domyślna implementacja system typów języka XAML może w związku z tym ujawnia schematu XAML typu i jej elementów członkowskich i zgłoś go pod względem system typów języka XAML. W domyślny system typu XAML pojęcie assignability typów jest mapowany na dziedziczenia CLR i pojęcia wystąpień, typy wartości i tak dalej również są mapowane do obsługi zachowania i funkcji środowiska CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Odwołania dla języka XAML — funkcje  
 Do obsługi języka XAML, .NET Framework XAML Services zapewnia konkretnej implementacji pojęcia dotyczące języka XAML zgodnie z definicją przestrzeni nazw XAML języka XAML. Te są udokumentowane jako odwołanie do określonej strony. Funkcje języka zostały opisane z punktu widzenia zachowania te funkcje języka zostały one przetworzone przez czytnik XAML lub Edytor XAML, który jest definiowana za pomocą usług .NET Framework XAML. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).
