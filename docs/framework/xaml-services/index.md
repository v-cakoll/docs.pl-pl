---
title: Usługi XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 373478e8c21fca66cbfbf7a58fc7d53f65ce5d0b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141090"
---
# <a name="xaml-services"></a>Usługi XAML
W tym temacie opisano funkcje, nazywane .NET Framework XAML usługi zestawu technologii. Większość usług i interfejsów API, opisane znajdują się w zestawie System.Xaml, która jest zestawem wprowadzone w programie [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zbiór zestawów programu .NET core. Usługi obejmują czytników i składników zapisywania klasy schematu i obsługa schematu, fabryk, przypisywanie klas, języka XAML, wsparcie wewnętrznej i inne funkcje języka XAML.  
  
## <a name="about-this-documentation"></a>Informacje o tej dokumentacji  
 Dokumentacji koncepcyjnego dla usług programu .NET Framework XAML przyjęto założenie, iż poprzednie środowisko przy użyciu języka XAML i jak ją mogą być stosowane do określonych framework, na przykład [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] lub programu Windows Workflow Foundation lub funkcji określonej technologii obszar, na przykład dostosowania kompilacji funkcje w <xref:Microsoft.Build.Framework.XamlTypes>. Ta dokumentacja nie podjęto próby opisano podstawy XAML jako język znaczników, terminologia składni XAML lub inne materiały wprowadzających. Zamiast tego tej dokumentacji koncentruje się na specjalnie przy użyciu usług .NET Framework XAML, które są włączone w bibliotece System.Xaml zestawu. Większość z tych interfejsów API jest dla scenariuszy integracji języka XAML oraz rozszerzalność. Może zawierać żadnego z następujących czynności:  
  
-   Rozszerzanie możliwości podstawowego czytelnicy XAML lub autorzy XAML (bezpośrednio przetwarzania strumienia węzłów XAML; wyprowadzanie własne czytnika XAML lub zapis XAML).  
  
-   Definiowanie typów niestandardowych można używać XAML, które nie mają zależności określonej struktury i przypisywanie typów w celu przekazania ich XAML typ właściwości do usług programu .NET Framework XAML.  
  
-   Hosting czytniki XAML lub moduły zapisujące XAML jako część aplikacji, takich jak projektant wizualny lub interaktywny Edytor źródeł znaczników XAML.  
  
-   Zapisywanie konwertery wartości XAML (rozszerzenia znaczników; typy konwerterów dla niestandardowych typów).  
  
-   Definiowanie niestandardowego kontekst schematu XAML (przy użyciu alternatywnych metod ładowania zestawu źródeł typ zapasowy; przy użyciu technik wyszukiwania znane typy, a nie zawsze odzwierciedlający zestawy; zostanie użyta załadowany zestaw pojęcia, które nie korzystają z środowiska CLR `AppDomain` i swój model zabezpieczeń skojarzone).  
  
-   Rozszerzanie podstawowego systemu typu XAML.  
  
-   Za pomocą `Lookup` lub `Invoker` technik do wywierania wpływu na XAML typ systemu i jak są obliczane podłoża typu.  
  
 Jeśli chcesz uzyskać wprowadzające informacje na XAML jako język, możesz spróbować [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md). Ten temat omawia XAML dla odbiorców, co nowego zarówno do [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] a także przy użyciu znaczników XAML i funkcji języka XAML. Innym dokumencie przydatne jest wprowadzające informacje w [specyfikacji języka XAML](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET framework XAML usług i System.Xaml w architekturze .NET  
 W poprzednich wersjach programu Microsoft .NET Framework, obsługa funkcji języka XAML został wdrożony, struktur, które oparty na programie Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation i Windows Communication Foundation (WCF)), a więc zróżnicowane w jego zachowanie i interfejsu API użyta, w zależności od tego, które z określonym środowiskiem były używane. Dotyczyło to też XAML analizator i jego obiekt wykresu mechanizm tworzenia, funkcje wewnętrzne języka XAML, obsługi serializacji i tak dalej.  
  
 W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework XAML Services i zestawu System.Xaml zdefiniowanie ilości co jest potrzebne do obsługi funkcji języka XAML. Obejmuje to klas bazowych dla XAML czytników i składników zapisywania XAML. Najważniejsze funkcja, dodany do usług XAML programu .NET Framework, który nie był obecny we wszystkich wdrożeniach XAML właściwa dla struktury jest reprezentację systemie typu XAML. Typ reprezentujący system przedstawia XAML zorientowane obiektowo jak centra możliwości w XAML bez przełączania zależności na konkretne funkcje platformy.  
  
 System typów XAML nie jest ograniczone przez formularz znaczników lub szczegóły środowiska wykonawczego pochodzenia XAML; nie jest ograniczona przez dowolnego zapasowy określonego typu systemu. System typów XAML zawiera reprezentacji obiektów dla typów, elementów członkowskich, kontekst schematu XAML, koncepcje poziomie XML i innych pojęcia języka XAML lub funkcje wewnętrzne XAML. Za pomocą lub rozszerzanie systemie typu XAML umożliwia pochodzi od klasy takie jak XAML czytników i składników zapisywania XAML i rozszerzyć funkcjonalność reprezentacje XAML do określonych funkcji włączane przez strukturę, technologia lub aplikacji, która zużywa lub emituje XAML. Pojęcie kontekst schematu XAML umożliwia operacje zapisu wykresu obiektu praktyczne z kombinacji XAML obiekt składnika zapisywania implementacji programu to technologia zapasowy typ systemu jako przekazywane za pomocą informacji o zestawie w kontekście i węzłów XAML źródło. Aby uzyskać więcej informacji na temat koncepcji schematu XAML. zobacz [domyślny kontekst schematu XAML i kontekst schematu XAML w WPF](../../../docs/framework/xaml-services/default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Strumienie węzłów XAML, XAML czytniki i moduły zapisujące XAML  
 Aby zrozumieć, ról, usług programu .NET Framework XAML odtwarzany w relacji między języka XAML i określonych technologii, które używają XAML jako język, jest pomocne w zrozumieniu koncepcji strumienia węzłów XAML i jak związany z tą koncepcją kształty interfejsu API i terminologia. Strumień węzłów XAML jest koncepcyjny pośredni między reprezentacja języka XAML i wykres obiektu, który reprezentuje XAML, lub definiuje.  
  
-   Czytnik XAML jest jednostką, która przetwarza XAML w pewnej postaci i generuje strumień węzłów XAML. W interfejsie API czytnik XAML jest reprezentowany przez klasę bazową <xref:System.Xaml.XamlReader>.  
  
-   Edytor XAML jest jednostką, która przetwarza strumień węzłów XAML i generuje coś innego. W interfejsie API Edytor XAML jest reprezentowane przez klasę bazową <xref:System.Xaml.XamlWriter>.  
  
 Dwie najbardziej typowych scenariuszy obejmujących XAML są podczas ładowania XAML do tworzenia wystąpienia grafu obiektów i zapisywania wykresu obiektu z aplikacji lub narzędzia i produkujących reprezentację XAML (zwykle w formie znaczników zapisany jako plik tekstowy). Ładowanie XAML i tworzenie wykresu obiektu jest często określonych w tej dokumentacji, jako ścieżkę obciążenia. Zapisywanie lub istniejący wykres serializacji obiektu do XAML jest często określana w tej dokumentacji jako Zapisz ścieżkę.  
  
 Najczęściej spotykanym typem ścieżki obciążenia można przedstawić w następujący sposób:  
  
-   Rozpoczynać reprezentację XAML w formacie XML kodowany w formacie UTF i zapisany jako plik tekstowy.  
  
-   Ładowanie tego XAML do <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> jest <xref:System.Xaml.XamlReader> podklasę.  
  
-   Wynik jest strumień węzłów XAML. Dostęp poszczególnych węzłów użycia strumienia węzłów XAML <xref:System.Xaml.XamlXmlReader>  /  <xref:System.Xaml.XamlReader> interfejsu API. W tym miejscu najbardziej typowych operacji jest przechodzić przez strumień węzłów XAML, przetwarzanie w każdym węźle, używając "bieżącego rekordu" metaphor.  
  
-   Przekaż wynikowy węzłów ze strumienia węzłów XAML w celu <xref:System.Xaml.XamlObjectWriter> interfejsu API. <xref:System.Xaml.XamlObjectWriter> jest <xref:System.Xaml.XamlWriter> podklasę.  
  
-   <xref:System.Xaml.XamlObjectWriter> Zapisuje wykres obiektu jednego obiektu w czasie, zgodnie z postęp strumień węzłów XAML źródła. Można to zrobić z pomocą kontekst schematu XAML i implementację, które mają dostęp do zestawów i typów zapasowy typ systemu i framework.  
  
-   Wywołaj <xref:System.Xaml.XamlObjectWriter.Result%2A> na końcu strumienia węzłów XAML do uzyskiwania obiektu głównego wykresu obiektu.  
  
 Najczęściej spotykanym typem ścieżka zapisu, można przedstawić w następujący sposób:  
  
-   Zacznij od wykresu obiektu czasu całej aplikacji, uruchamianie, zawartości interfejsu użytkownika i stan czasu wykonywania lub mniejszych segment cała aplikacja reprezentację obiektu w czasie wykonywania.  
  
-   Z obiektu start logiczne, takie jak katalog główny aplikacji lub katalog główny dokumentów, ładowanie obiektów do <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> jest <xref:System.Xaml.XamlReader> podklasę.  
  
-   Wynik jest strumień węzłów XAML. Dostęp poszczególnych węzłów użycia strumienia węzłów XAML <xref:System.Xaml.XamlObjectReader> i <xref:System.Xaml.XamlReader> interfejsu API. W tym miejscu najbardziej typowych operacji jest przechodzić przez strumień węzłów XAML, przetwarzanie w każdym węźle, używając "bieżącego rekordu" metaphor.  
  
-   Przekaż wynikowy węzłów ze strumienia węzłów XAML w celu <xref:System.Xaml.XamlXmlWriter> interfejsu API. <xref:System.Xaml.XamlXmlWriter> jest <xref:System.Xaml.XamlWriter> podklasę.  
  
-   <xref:System.Xaml.XamlXmlWriter> Zapisuje XAML w UTF XML, kodowania. To można zapisać jako plik tekstowy, jako strumień lub w innych form.  
  
-   Wywołaj <xref:System.Xaml.XamlXmlWriter.Flush%2A> uzyskanie do pliku wyjściowego.  
  
 Aby uzyskać więcej informacji na temat koncepcji strumienia węzłów XAML, zobacz [opis XAML węzła Stream strukturami i koncepcjami](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>Klasa XamlServices  
 Nie zawsze jest konieczne poradzić sobie z strumień węzłów XAML. Jeśli chcesz ścieżka podstawowa obciążenia lub podstawowa ścieżka zapisu, możesz użyć interfejsów API w <xref:System.Xaml.XamlServices> klasy.  
  
-   Różne sygnatur <xref:System.Xaml.XamlServices.Load%2A> zaimplementować ścieżki obciążenia. Możesz załadować pliku lub strumienia lub załadować <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> lub <xref:System.Xaml.XamlReader> , zawijanie dane wejściowe XAML, ładując za pomocą interfejsów API ten czytnik.  
  
-   Różne sygnatur <xref:System.Xaml.XamlServices.Save%2A> zapisywania wykresu obiektu i generować dane wyjściowe w postaci strumienia pliku lub <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> wystąpienia.  
  
-   <xref:System.Xaml.XamlServices.Transform%2A> Konwertuje XAML, łącząc ścieżki obciążenia i Zapisz ścieżkę jako pojedyncza operacja. Kontekst innego schematu lub tworzenie innej kopii typu systemu może służyć do <xref:System.Xaml.XamlReader> i <xref:System.Xaml.XamlWriter>, czyli, co ma wpływ na sposób wynikowy XAML jest przekształcane.  
  
 Aby uzyskać więcej informacji o sposobie używania <xref:System.Xaml.XamlServices>, zobacz [klasa XAMLServices i podstawowy odczyt XAML lub zapisywanie](../../../docs/framework/xaml-services/xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>System typów XAML  
 System typów XAML udostępnia interfejsy API, które są wymagane do pracy z danego węzła poszczególnych strumienia węzłów XAML.  
  
 <xref:System.Xaml.XamlType> to reprezentacja obiektu — co to są przetwarzania między węzła obiektu początkowego i końcowego obiektu węzła.  
  
 <xref:System.Xaml.XamlMember> jest reprezentację należącą do obiektu — co to są przetwarzania między węzeł składowej, od rozpoczęcia i zakończenia elementu członkowskiego węzła.  
  
 Interfejsy API, takie jak <xref:System.Xaml.XamlType.GetAllMembers%2A> i <xref:System.Xaml.XamlType.GetMember%2A> i <xref:System.Xaml.XamlMember.DeclaringType%2A> raportu relacje między <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>.  
  
 Domyślne zachowanie systemu typu XAML jako implementowany przez .NET Framework XAML Services opiera się na środowisko uruchomieniowe języka wspólnego (CLR) i analizę statyczną typów CLR w zestawach przy użyciu odbicia. Dla określonego typu CLR, domyślna implementacja systemie typu XAML można w związku z tym, udostępnianie schematu XAML tego typu i jego elementów członkowskich i go zgłosić pod względem systemie typu XAML. W systemie typu XAML domyślne koncepcji zbywalności typów jest mapowana na dziedziczenie CLR i koncepcji wystąpień typów wartości i również są mapowane do obsługi zachowań i funkcji środowiska CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Dokumentacja dotycząca funkcji języka XAML  
 Na potrzeby obsługi XAML, .NET Framework XAML Services udostępnia określoną implementację pojęcia języka XAML, zgodnie z definicją w przestrzeni nazw XAML dla języka XAML. Te są opisane jako odwołanie do określonej strony. Funkcje języka są udokumentowane z punktu widzenia zachowaniem te funkcje językowe są przetwarzane przez czytnik XAML lub Edytor XAML, który jest definiowany przez .NET Framework XAML Services. Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).
