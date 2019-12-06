---
title: Usługi XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], System.Xaml concepts
- XAML Services in WPF [XAML Services]
- System.Xaml [XAML Services], conceptual documentation
ms.assetid: 0e11f386-808c-4eae-9ba6-029ad7ba2211
ms.openlocfilehash: 8e1e8dc9a1410d05c19e4dd1bccb30c65d7c5e66
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837288"
---
# <a name="xaml-services"></a>Usługi XAML
W tym temacie opisano możliwości zestawu technologii znanego jako .NET Framework usług XAML. Większość opisanych usług i interfejsów API znajduje się w zestawie System. XAML, który jest zestawem wprowadzonym z zestawem .NET Framework 4 zestawów .NET Core. Usługi obejmują czytelnicy i moduły zapisujące, klasy schematów i obsługę schematów, fabryki, Przypisywanie klas, obsługa wewnętrzna języka XAML i inne funkcje języka XAML.  
  
## <a name="about-this-documentation"></a>Informacje o tej dokumentacji  
 Dokumentacja dotycząca pojęć dla .NET Framework usług XAML zakłada, że masz poprzednie środowisko pracy z językiem XAML i jak mogą one być stosowane do określonej struktury, na przykład [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] lub Windows Workflow Foundation lub określonego obszaru funkcji, na przykład funkcji dostosowywania kompilacji w <xref:Microsoft.Build.Framework.XamlTypes>. W tej dokumentacji nie jest podejmowana próba wyjaśnienia podstaw języka XAML w języku znaczników, terminologii składni języka XAML ani innych materiałów wprowadzających. Zamiast tego Ta dokumentacja koncentruje się na korzystaniu z usług .NET Framework XAML, które są włączone w bibliotece zestawów System. XAML. Większość z tych interfejsów API jest dla scenariuszy integracji i rozszerzalności języka XAML. Mogą to być następujące elementy:  
  
- Rozszerzanie możliwości podstawowych czytników XAML lub autorów XAML (przetwarzanie strumienia węzła XAML bezpośrednio; wyprowadzanie własnego czytnika XAML lub składnika zapisywania XAML).  
  
- Definiowanie typów niestandardowych użytecznych do języka XAML, które nie mają określonych zależności struktury, i przypisywania typów do przekazywania charakterystyk systemu typu XAML do .NET Framework usług XAML.  
  
- Hosting czytelników XAML lub autorów XAML jako składnika aplikacji, takiej jak projektant wizualny lub interaktywny Edytor dla źródeł znaczników XAML.  
  
- Pisanie konwerterów wartości języka XAML (rozszerzeń znaczników; konwertery typów dla typów niestandardowych).  
  
- Definiowanie niestandardowego kontekstu schematu XAML (przy użyciu alternatywnych technik ładowania zestawów dla źródeł typu zapasowego; użycie technik wyszukiwania znanych typów zamiast zawsze odzwierciedlania zestawów; przy użyciu załadowanych koncepcji zestawu, które nie używają `AppDomain` CLR i skojarzonego z nim modelu zabezpieczeń).  
  
- Rozszerzanie podstawowego systemu typów XAML.  
  
- Użycie technik `Lookup` lub `Invoker`, które mają wpływ na system typów XAML i sposób oceniania typu.  
  
 Jeśli szukasz materiału wprowadzającego w języku XAML w postaci języka, możesz spróbować wykonać [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md). W tym temacie omówiono w języku XAML dla odbiorców, którzy są nowymi do [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], a także do korzystania z funkcji znaczników XAML i języka XAML. Innym przydatnym dokumentem jest materiał wprowadzający w [specyfikacji języka XAML](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="net-framework-xaml-services-and-systemxaml-in-the-net-architecture"></a>.NET Framework usług XAML i system. XAML w architekturze .NET  
 W poprzednich wersjach Microsoft .NET Framework Obsługa funkcji języka XAML została wdrożona przez platformy, które zostały utworzone na podstawie Microsoft .NET Framework ([!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Windows Workflow Foundation i Windows Communication Foundation (WCF)), a tym samym w zależności od tego, jak działa interfejs API, a następnie używany w programie, zależnie od używanej platformy. Obejmuje to Analizator XAML i mechanizm tworzenia grafów obiektów, funkcje wewnętrzne języka XAML, Obsługa serializacji i tak dalej.  
  
 W .NET Framework 4 .NET Framework usługi XAML i zestaw system. xaml definiują większość potrzebnych do obsługi funkcji języka XAML. Obejmuje to klasy bazowe dla czytników XAML i autorów XAML. Najważniejsze funkcje dodane do .NET Framework usług XAML, które nie były obecne w żadnej z implementacji języka XAML specyficznych dla platformy, są reprezentacją systemu typów dla języka XAML. Reprezentacja systemu typów przedstawia kod XAML w zorientowany obiektowo sposób, który koncentruje się na możliwościach języka XAML, bez konieczności wykonywania zależności od określonych możliwości platformy.  
  
 System typu XAML nie jest ograniczony przez formularz oznakowania ani charakterystykę czasu wykonywania pochodzenia XAML; nie jest ograniczony przez żaden określony system typu zapasowego. System typu XAML zawiera reprezentacje obiektów dla typów, elementów członkowskich, kontekstów schematu XAML, pojęć na poziomie XML i innych pojęć języka XAML lub funkcji w języku XAML. Używanie lub Rozszerzanie systemu typu XAML umożliwia tworzenie danych z klas takich jak czytelnicy XAML i autorzy języka XAML, a także rozszerzanie funkcji reprezentacji XAML do określonych funkcji włączonych przez platformę, technologię lub aplikację, która wykorzystuje lub emituje kod XAML. Koncepcja kontekstu schematu XAML umożliwia praktyczne operacje zapisu grafu obiektów z kombinacji implementacji składnika zapisywania obiektów XAML, systemowego typu technologii jako przekazanego przez informacje o zestawie w kontekście i węzła XAML zewnętrz. Aby uzyskać więcej informacji na temat koncepcji schematu XAML. Zobacz [domyślny kontekst schematu XAML i kontekst schematu WPF XAML](default-xaml-schema-context-and-wpf-xaml-schema-context.md).  
  
## <a name="xaml-node-streams-xaml-readers-and-xaml-writers"></a>Strumienie węzłów XAML, czytniki XAML i moduły zapisujące XAML  
 Aby zrozumieć rolę, która .NET Framework usług XAML odgrywa w relacji między językiem XAML i określonymi technologiami korzystającymi z języka XAML jako językiem, warto zrozumieć koncepcję strumienia węzła XAML i sposób, w jaki koncepcja ta tworzy kształt interfejsu API i Terminologia. Strumień węzłów XAML jest koncepcyjną pośrednią między reprezentacją języka XAML a wykresem obiektu, który reprezentuje lub definiuje kod XAML.  
  
- Czytnik XAML jest jednostką, która przetwarza kod XAML w postaci jakiejś i tworzy strumień węzłów XAML. W interfejsie API czytnik XAML jest reprezentowany przez klasę bazową <xref:System.Xaml.XamlReader>.  
  
- Składnik zapisywania XAML jest jednostką, która przetwarza strumień węzłów XAML i tworzy coś innego. W interfejsie API składnik zapisywania języka XAML jest reprezentowany przez klasę bazową <xref:System.Xaml.XamlWriter>.  
  
 Dwa najczęstsze scenariusze dotyczące języka XAML to ładowanie kodu XAML w celu utworzenia wystąpienia grafu obiektów i zapisanie grafu obiektów z poziomu aplikacji lub narzędzia i produkowanie reprezentacji języka XAML (zazwyczaj w postaci znaczników zapisanej jako plik tekstowy). Ładowanie języka XAML i tworzenie grafu obiektów jest często określane w tej dokumentacji jako ścieżka ładowania. Zapisywanie lub Serializowanie istniejącego grafu obiektów do języka XAML jest często określane jako ścieżka zapisu w tej dokumentacji.  
  
 Najpopularniejszy typ ścieżki ładowania można opisać w następujący sposób:  
  
- Zacznij od reprezentacji języka XAML w formacie XML zakodowanym przy użyciu kodowania UTF i zapisywane jako plik tekstowy.  
  
- Załaduj ten kod XAML do <xref:System.Xaml.XamlXmlReader>. <xref:System.Xaml.XamlXmlReader> jest <xref:System.Xaml.XamlReader> podklasą.  
  
- Wynik jest strumieniem węzła XAML. Można uzyskać dostęp do poszczególnych węzłów strumienia węzła XAML przy użyciu <xref:System.Xaml.XamlXmlReader> / <xref:System.Xaml.XamlReader> interfejsu API. Najbardziej typową operacją jest przechodzenie przez strumień węzłów XAML, przetwarzanie każdego węzła przy użyciu "bieżącego rekordu" metaphor.  
  
- Przekaż węzły z poziomu strumienia węzła XAML do interfejsu API <xref:System.Xaml.XamlObjectWriter>. <xref:System.Xaml.XamlObjectWriter> jest <xref:System.Xaml.XamlWriter> podklasą.  
  
- <xref:System.Xaml.XamlObjectWriter> zapisuje Graf obiektu, jeden obiekt w czasie, zgodnie z postępem przez źródłowy strumień węzłów XAML. Jest to realizowane z pomocą kontekstu schematu XAML i implementacji, która może uzyskać dostęp do zestawów i typów typu zapasowego systemu i struktury.  
  
- Wywołaj <xref:System.Xaml.XamlObjectWriter.Result%2A> na końcu strumienia węzła XAML, aby uzyskać obiekt główny grafu obiektów.  
  
 Najbardziej typowy typ ścieżki zapisu można opisać w następujący sposób:  
  
- Zacznij od grafu obiektów całego czasu uruchomienia aplikacji, zawartości interfejsu użytkownika i stanu czasu wykonywania lub mniejszego segmentu reprezentacji obiektu ogólnej aplikacji w czasie wykonywania.  
  
- Na podstawie logicznego obiektu uruchomieniowego, takiego jak główny katalog aplikacji lub katalog główny dokumentu, Załaduj obiekty do <xref:System.Xaml.XamlObjectReader>. <xref:System.Xaml.XamlObjectReader> jest <xref:System.Xaml.XamlReader> podklasą.  
  
- Wynik jest strumieniem węzła XAML. Można uzyskać dostęp do poszczególnych węzłów strumienia węzła XAML przy użyciu <xref:System.Xaml.XamlObjectReader> i <xref:System.Xaml.XamlReader> interfejsu API. Najbardziej typową operacją jest przechodzenie przez strumień węzłów XAML, przetwarzanie każdego węzła przy użyciu "bieżącego rekordu" metaphor.  
  
- Przekaż węzły z poziomu strumienia węzła XAML do interfejsu API <xref:System.Xaml.XamlXmlWriter>. <xref:System.Xaml.XamlXmlWriter> jest <xref:System.Xaml.XamlWriter> podklasą.  
  
- <xref:System.Xaml.XamlXmlWriter> zapisuje kod XAML w kodowaniu XML UTF. Można go zapisać jako plik tekstowy, jako strumień lub w innych formularzach.  
  
- Wywołaj <xref:System.Xaml.XamlXmlWriter.Flush%2A>, aby uzyskać końcowe dane wyjściowe.  
  
 Aby uzyskać więcej informacji o pojęciach dotyczących strumienia węzłów XAML, zobacz [Opis struktur i koncepcji strumienia węzła XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
### <a name="the-xamlservices-class"></a>Klasa XamlServices  
 Nie zawsze jest konieczne zaradzenie sobie ze strumieniem węzła XAML. Jeśli potrzebujesz podstawowej ścieżki ładowania lub ścieżki podstawowego zapisu, możesz użyć interfejsów API w klasie <xref:System.Xaml.XamlServices>.  
  
- Różne sygnatury <xref:System.Xaml.XamlServices.Load%2A> implementują ścieżkę ładowania. Można załadować plik lub strumień albo załadować <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader> lub <xref:System.Xaml.XamlReader> zawijające dane wejściowe XAML przez załadowanie z użyciem interfejsów API tego czytnika.  
  
- Różne sygnatury <xref:System.Xaml.XamlServices.Save%2A> zapisują Graf obiektu i tworzą dane wyjściowe jako strumień, plik lub <xref:System.Xml.XmlWriter>/wystąpienia <xref:System.IO.TextWriter>.  
  
- <xref:System.Xaml.XamlServices.Transform%2A> konwertuje kod XAML przez połączenie ścieżki ładowania i ścieżki zapisu jako pojedynczej operacji. W przypadku <xref:System.Xaml.XamlReader> i <xref:System.Xaml.XamlWriter>można użyć innego kontekstu schematu lub innego systemu typów zapasowych, co wpływa na sposób przekształcania wyniku w kodzie XAML.  
  
 Aby uzyskać więcej informacji o sposobach używania <xref:System.Xaml.XamlServices>, zobacz [Klasa XamlServices i podstawowy odczyt lub zapis XAML](xamlservices-class-and-basic-xaml-reading-or-writing.md).  
  
## <a name="xaml-type-system"></a>System typów XAML  
 System typów XAML udostępnia interfejsy API, które są wymagane do pracy z danym pojedynczym węzłem strumienia węzła XAML.  
  
 <xref:System.Xaml.XamlType> to reprezentacja obiektu — przetwarzanie między węzłem obiektu początkowego i węzłem obiektu końcowego.  
  
 <xref:System.Xaml.XamlMember> jest reprezentacją elementu członkowskiego obiektu — przetwarzanie między węzłem początkowym elementu członkowskiego a końcowym węzłem członkowskim.  
  
 Interfejsy API, takie jak <xref:System.Xaml.XamlType.GetAllMembers%2A> i <xref:System.Xaml.XamlType.GetMember%2A> i <xref:System.Xaml.XamlMember.DeclaringType%2A> raportują relacje między <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>.  
  
 Domyślne zachowanie systemu typu XAML zgodnie z implementacją .NET Framework usług XAML jest oparte na środowisku uruchomieniowym języka wspólnego (CLR) i statycznej analizie typów CLR w zestawach za pomocą odbicia. W związku z tym, w przypadku określonego typu CLR, domyślna implementacja systemu typu XAML może uwidaczniać schemat XAML tego typu i jego składowych, a następnie zgłaszać go pod względem systemu typu XAML. W domyślnym systemie typów XAML pojęcie przypisywania typów jest zamapowane na dziedziczenie CLR, a koncepcje wystąpień, typy wartości i tak dalej są również mapowane na zachowania i funkcje środowiska CLR.  
  
## <a name="reference-for-xaml-language-features"></a>Dokumentacja funkcji języka XAML  
 W celu obsługi języka XAML usługi .NET Framework XAML udostępniają specyficzne implementacje pojęć języka XAML zdefiniowane dla przestrzeni nazw XAML języka XAML. Są one udokumentowane jako określone strony odniesienia. Funkcje językowe są udokumentowane z punktu widzenia działania tych funkcji języka, gdy są przetwarzane przez czytnik XAML lub moduł zapisujący XAML, który jest zdefiniowany przez .NET Framework usług XAML. Aby uzyskać więcej informacji, zobacz [przestrzeń nazw XAML (x:) Funkcje językowe](xaml-namespace-x-language-features.md).
