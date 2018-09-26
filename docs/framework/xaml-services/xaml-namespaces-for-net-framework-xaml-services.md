---
title: Przestrzeń nazw dla usług .NET Framework XAML
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: ac6554cbdeb5bc6e0fe7fb96ea95d0143c293d22
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070750"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Przestrzeń nazw dla usług .NET Framework XAML
Przestrzeń nazw XAML jest koncepcji, który rozwija w definicji przestrzeni nazw XML. Podobnie jak w przestrzeni nazw XML, można zdefiniować za pomocą nazw XAML `xmlns` atrybutów w znaczniku. Przestrzenie nazw XAML również jest reprezentowanych w strumień węzłów XAML i innych interfejsów API usług XAML. W tym temacie wprowadzono pojęcie przestrzeń nazw XAML i opisuje, jak przestrzenie nazw XAML mogą być definiowane i są używane przez kontekst schematu XAML i innymi aspektami usług programu .NET Framework XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML i XAML Namespace  
 Przestrzeń nazw XAML jest wyspecjalizowane przestrzeni nazw XML, tak samo, jak XAML jest formą specjalistyczne XML i używa podstawowej postaci XML dla jego znaczników. W znaczniku, możesz deklarować przestrzeń nazw XAML i jego mapowanie za pośrednictwem `xmlns` atrybut zastosowanych do elementu. `xmlns` Można wprowadzać tego samego elementu, który przestrzeń nazw XAML jest zadeklarowany w deklaracji. Deklaracja przestrzeni nazw XAML wprowadzone do elementu jest prawidłowy dla tego elementu, wszystkie atrybuty tego elementu, a wszystkie elementy podrzędne tego elementu. Atrybuty można używać przestrzeni nazw XAML, która jest taka sama jak element, który zawiera atrybut, tak długo, jak sama nazwa atrybutu odwołuje się do prefiksu jako część nazwy atrybutów w znaczniku.  
  
 Różnica w przestrzeni nazw XAML i przestrzeni nazw XML jest nazw XML może być używana do odwołania schematu lub mogą być używane po prostu rozróżnianie podmiotów. Dla XAML typów i członków w XAML ostatecznie muszą zostać rozwiązane do tworzenia kopii typów i pojęć dotyczących schematu XML nie dotyczą również tej funkcji. Przestrzeń nazw XAML zawiera informacje, że kontekst schematu XAML musi być dostępny, aby wykonać to mapowanie typu.  
  
## <a name="xaml-namespace-components"></a>Składniki Namespace XAML  
 Definicję przestrzeni nazw XAML ma dwa składniki: prefiksu i identyfikator. Każda z tych składników są obecne, gdy przestrzeń nazw XAML jest zadeklarowany w znacznikach lub zdefiniowanych w systemie typu XAML.  
  
 Prefiks może być dowolnym ciągiem, zgodnie z [przestrzenie nazw Specyfikacja XML 1.0 W3C](https://go.microsoft.com/fwlink/?LinkID=161735) . Zgodnie z Konwencją prefiksy są zazwyczaj bardzo krótkich ciągów, ponieważ prefiks jest powtarzany tyle razy w pliku typowe znaczników. Niektóre przestrzenie nazw XAML, które są przeznaczone do użycia w wielu implementacjach XAML używać określonego konwencjonalne prefiksów. Na przykład, przestrzeń nazw XAML dla języka XAML jest zazwyczaj mapować przy użyciu prefiksu `x`. Można zdefiniować domyślną XAML przestrzeń nazw, gdy nie zostanie podany w definicji prefiksu, ale jest reprezentowany jako ciąg pusty, jeśli zdefiniowany lub badane by.NET interfejsu API usług XAML Framework. Zazwyczaj domyślna przestrzeń nazw XAML jest wybierany celowo Aby podwyższyć poziom w trybie zmaksymalizowanym ilość pominięcie prefiksu znacznika przez technologię wykonywania XAML i scenariuszy i vocabularies.  
  
 Identyfikator może być dowolnym ciągiem, zgodnie z [przestrzenie nazw Specyfikacja XML 1.0 W3C](https://go.microsoft.com/fwlink/?LinkID=161735). Zgodnie z Konwencją identyfikatory dla przestrzeni nazw XML lub XAML przestrzenie nazw często podano w formie identyfikatora URI, zwykle jako bezwzględny identyfikator URI kwalifikowana protokołu. Często informacje o wersji, który definiuje określonego słownika XAML jest implikowane jako część ciąg ścieżki. Przestrzenie nazw XAML Dodaj Konwencji identyfikatora dodatkowe poza Konwencji identyfikatora URI XML. W przypadku przestrzeni nazw XAML identyfikator komunikuje się informacje, które są wymagane przez kontekst schematu XAML, aby rozwiązać typy, które są określane jako elementy w ramach tej przestrzeni nazw XAML lub rozwiązać atrybutów do elementów członkowskich.  
  
 W celu przekazywania informacji do kontekst schematu XAML identyfikator dla przestrzeni nazw XAML nadal może być w formie identyfikatora URI. Jednak w takim przypadku identyfikatora URI jest także zadeklarowana jako pasującym identyfikatorze określonego zestawu lub listę zestawów. Odbywa się w zestawach poprzez przypisywanie zestawu z <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta metoda identyfikowania przestrzeń nazw XAML i obsługi rozpoznawania typu opartego na CLR w zestawie opartego na atrybutach jest obsługiwana przez domyślny kontekst schematu XAML w .NET Framework XAML Services. Ogólnie rzecz biorąc ta Konwencja może służyć w przypadkach, w którym kontekst schematu XAML zawiera środowisko CLR lub opiera się na domyślny kontekst schematu XAML, co jest niezbędne, aby można było odczytać atrybuty CLR z zestawów CLR.  
  
 Przestrzenie nazw XAML można również zidentyfikować zgodnie z Konwencją, komunikujący się przestrzeń nazw środowiska CLR i zestaw Definiowanie typu. Ta konwencja jest używana w przypadkach, gdy nie <xref:System.Windows.Markup.XmlnsDefinitionAttribute> autorstwa istnieje w zestawach, które zawierają typy. Ta konwencja jest potencjalnie bardziej skomplikowane niż Konwencji identyfikatora URI i ma również możliwość niejednoznaczności i duplikatów, ponieważ istnieją różne sposoby odwoływania się do zestawu.  
  
 Podstawowe formie identyfikator, który jest używana konwencja przestrzeni nazw i zestawów CLR jest następująca:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` i `; assembly=` literału składników składni.  
  
 *clrnsName* jest nazwą ciągu, identyfikująca przestrzeń nazw CLR. Ta nazwa ciągu zawiera żadnych znaków wewnętrznego kropka (.), które dostarczanie wskazówek na temat przestrzeń nazw środowiska CLR i jego relacji z innych przestrzeniach nazw środowiska CLR.  
  
 *assemblyShortName* jest nazwą ciągu zestawu, który definiuje typy, które są przydatne w XAML. Typy, które można uzyskać dostęp za pomocą zadeklarowanej przestrzeni nazw XAML oczekuje określonych przez zestaw i specjalnie być zadeklarowany w przestrzeni nazw CLR, określony przez *clrnsName*. Ta nazwa ciągu zazwyczaj równoleżnikami informacje zgłoszone przez <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Bardziej kompletny definicję Konwencji przestrzeni nazw i zestawów CLR jest następująca:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* reprezentuje dowolny ciąg, który jest dozwolony jako <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> danych wejściowych. Ten ciąg może zawierać informacje o wersji kultury lub klucza publicznego (definicje te pojęcia są zdefiniowane w temacie dotyczącym <xref:System.Reflection.Assembly>). COFF format i dowody (używane przez inne przeciążenia <xref:System.Reflection.Assembly.Load%2A>) nie są istotne dla celów; z ładowaniem zestawu, XAML wszystkie informacje o ładowaniu muszą być przedstawione jako ciąg.  
  
 Określenie klucza publicznego dla zestawu jest przydatną techniką, dotyczące zabezpieczeń XAML lub usuwania niejednoznaczności możliwe, że może istnieć, jeśli zestawy są ładowane przez prostej nazwie lub wstępnie istnieje w domenie z pamięci podręcznej lub aplikacji. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklaracji Namespace XAML w usługach XAML interfejsu API  
 W interfejsie API usług XAML deklarację przestrzeni nazw XAML jest reprezentowany przez <xref:System.Xaml.NamespaceDeclaration> obiektu. Jeśli użytkownik deklaruje przestrzeni nazw XAML w kodzie, należy wywołać <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> konstruktora. `ns` i `prefix` parametry są określane jako ciągi, a dane wejściowe do przekazania do tych parametrów odnosi się do definicji identyfikatora przestrzeni nazw XAML i prefiksu przestrzeni nazw XAML, zgodnie z wcześniej w tym temacie.  
  
 Jeśli badaną informacji dotyczących przestrzeni nazw XAML w ramach strumienia węzłów XAML lub za pośrednictwem innych dostępu w systemie typu XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> zgłasza identyfikator przestrzeni nazw XAML i <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> raportów prefiks przestrzeni nazw XAML.  
  
 W postaci strumienia węzłów XAML informacji dotyczących przestrzeni nazw XAML może pojawić się jako węzeł XAML, który poprzedza jednostki, której dotyczy. Obejmuje to przypadki, w którym poprzedza informacji dotyczących przestrzeni nazw XAML `StartObject` głównego elementu XAML. Aby uzyskać więcej informacji, zobacz [opis XAML węzła Stream strukturami i koncepcjami](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Umożliwia obsługę wielu scenariuszy korzystających z interfejsu API programu .NET Framework XAML Services powinien istnieć co najmniej jedną deklarację przestrzeni nazw XAML i deklaracji musi zawierać lub odwoływać się do informacji, która jest wymagana przez kontekst schematu XAML. Przestrzenie nazw XAML musi określić zestawy do załadowania lub pomocne przy rozwiązywaniu określonych typów w przestrzeni nazw i zestawów, które są już załadowane lub znane przez kontekst schematu XAML.  
  
 W celu wygenerowania strumień węzłów XAML, informacje o typie XAML musi być dostępna, za pośrednictwem kontekst schematu XAML. Informacje o typie XAML nie można ustalić bez pierwszy określenie odpowiednich przestrzeni nazw XAML dla każdego węzła do utworzenia. W tym momencie żadnych wystąpień typów są jeszcze utworzony, ale kontekst schematu XAML może być konieczne do wyszukiwania informacji z Definiowanie zestawu i tworzenie kopii typu. Na przykład, aby przetworzyć znaczników `<Party><PartyFavor/></Party>`, kontekst schematu XAML musi być w stanie określić nazwę i typ `ContentProperty` z `Party`i dlatego również musi znać informacji dotyczących przestrzeni nazw XAML dla `Party` i `PartyFavor`. W przypadku domyślny kontekst schematu XAML statycznej odbicia raporty ilości XAML informacje o systemie typu, który jest potrzebny do generowania węzłów typu XAML w strumieniu węzła.  
  
 Aby można było wygenerować grafu obiektów ze strumienia węzłów XAML, deklaracje przestrzeni nazw XAML musi istnieć dla każdego prefiksu XAML używane w oryginalnej znaczników i rejestrowane w strumień węzłów XAML. W tym momencie tworzone są wystąpienia, a wartość true, mapowanie typu zachowanie.  
  
 Jeśli potrzebujesz wstępnie wypełnić informacji przestrzeń nazw XAML, w przypadkach, gdzie nie zdefiniowano przestrzeni nazw XAML, mają kontekst schematu XAML do użycia w znaczniku, jedna z technik umożliwia jest do deklarowania deklaracje przestrzeni nazw XML w <xref:System.Xml.XmlParserContext> dla <xref:System.Xml.XmlReader>. Użyj tego <xref:System.Xml.XmlReader> jako dane wejściowe dla konstruktora czytnika XAML lub <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Dwa API, które są istotne dla przestrzeni nazw XAML, obsługa w .NET Framework XAML Services są atrybuty <xref:System.Windows.Markup.XmlnsDefinitionAttribute> i <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Te atrybuty mają zastosowanie do zestawów. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jest używany przez kontekst schematu XAML do interpretacji żadnych deklaracji przestrzeni nazw XAML, która zawiera identyfikator URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> jest używana przez narzędzia, które emitują XAML, dzięki czemu określonej przestrzeni nazw XAML może być serializowany z prefiksem przewidywalne. Aby uzyskać więcej informacji, zobacz [XAML-Related atrybuty CLR dla niestandardowych typów i bibliotek](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie struktur i koncepcji strumienia węzłów XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
