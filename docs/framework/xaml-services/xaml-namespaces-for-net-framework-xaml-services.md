---
title: Przestrzeń nazw dla usług .NET Framework XAML
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 11bf5d112c64fb0b942decf7635f02b90a98bdeb
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837171"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Przestrzeń nazw dla usług .NET Framework XAML
Przestrzeń nazw XAML to koncepcja, która rozszerza definicję przestrzeni nazw XML. Podobnie jak w przypadku przestrzeni nazw XML, można zdefiniować przestrzeń nazw XAML przy użyciu atrybutu `xmlns` w znaczniku. Przestrzenie nazw XAML są również reprezentowane w strumieniu węzła XAML i innych interfejsów API usług XAML. Ten temat definiuje koncepcję przestrzeni nazw XAML i opisuje, jak przestrzenie nazw XAML mogą być definiowane i używane przez konteksty schematu XAML oraz inne aspekty .NET Framework usług XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Przestrzeń nazw XML i przestrzeń nazw XAML  
 Przestrzeń nazw XAML jest wyspecjalizowaną przestrzenią nazw XML, podobnie jak kod XAML jest wyspecjalizowaną formą XML i używa podstawowego formularza XML dla jego znaczników. W znaczniku deklarujesz przestrzeń nazw XAML i jej mapowanie przez atrybut `xmlns` stosowany do elementu. Deklaracja `xmlns` może zostać wykonana do tego samego elementu, w którym jest zadeklarowana przestrzeń nazw XAML. Deklaracja przestrzeni nazw XAML wprowadzona do elementu jest prawidłowa dla tego elementu, wszystkich atrybutów tego elementu i wszystkich elementów podrzędnych tego elementu. Atrybuty mogą używać przestrzeni nazw XAML, która nie jest taka sama jak element, który zawiera atrybut, tak długo, jak sama nazwa atrybutu odwołuje się do prefiksu jako część nazwy atrybutu w znaczniku.  
  
 Rozróżnienie przestrzeni nazw XAML w porównaniu z przestrzenią nazw XML polega na tym, że przestrzeń nazw XML może być używana do odwoływania się do schematu lub może być używana do zwykłego odróżnienia jednostek. W przypadku języka XAML typy i elementy członkowskie, które są używane w języku XAML, muszą ostatecznie zostać rozpoznane jako typy kopii zapasowych, a koncepcje schematu XML nie są dobrze stosowane w tej funkcji. Przestrzeń nazw XAML zawiera informacje, które muszą być dostępne w kontekście schematu XAML w celu przeprowadzenia mapowania tego typu.  
  
## <a name="xaml-namespace-components"></a>Składniki przestrzeni nazw XAML  
 Definicja przestrzeni nazw XAML ma dwa składniki: prefiks i identyfikator. Każdy z tych składników jest obecny, gdy przestrzeń nazw XAML jest zadeklarowana w znaczniku lub zdefiniowana w systemie typu XAML.  
  
 Prefiks może być dowolnym ciągiem dozwolonym przez [przestrzenie nazw W3C w specyfikacji XML 1,0](https://www.w3.org/TR/REC-xml-names/) . Według Konwencji prefiksy są zwykle bardzo krótkie, ponieważ prefiks powtarza się wiele razy w typowym pliku znaczników. Niektóre przestrzenie nazw XAML przeznaczone do użycia w wielu implementacjach języka XAML używają określonych konwencjonalnych prefiksów. Na przykład przestrzeń nazw XAML języka XAML jest zwykle mapowana przy użyciu prefiksu `x`. Można zdefiniować domyślną przestrzeń nazw XAML, w której prefiks nie jest określony w definicji, ale jest reprezentowany jako pusty ciąg, jeśli został zdefiniowany lub zbadał zapytanie by.NET Framework XAML Services API. Zazwyczaj domyślna przestrzeń nazw języka XAML jest celowo wybierana w celu promowania zmaksymalizowanej ilości pominięcia znaczników przez technologię implementującą kod XAML oraz jej scenariusze i słownictwo.  
  
 Identyfikator może być dowolnym ciągiem dozwolonym przez [przestrzenie nazw W3C w specyfikacji XML 1,0](https://www.w3.org/TR/REC-xml-names/). Zgodnie z Konwencją identyfikatory dla przestrzeni nazw XML lub przestrzeni nazw XAML często są wyrażane w formie identyfikatora URI, zazwyczaj jako bezwzględnie kwalifikowany protokół URI. Często informacje o wersji, które definiują konkretny słownik XAML, są implikowane jako część ciągu ścieżki. Przestrzenie nazw XAML dodają dodatkową Konwencję identyfikatora, która wykracza poza Konwencję identyfikatora URI XML. W przypadku przestrzeni nazw XAML identyfikator komunikuje informacje, które są konieczne przez kontekst schematu XAML w celu rozpoznania typów, które są określone jako elementy w tej przestrzeni nazw XAML, lub do rozpoznawania atrybutów do elementów członkowskich.  
  
 W celu przekazywania informacji do kontekstu schematu XAML identyfikator przestrzeni nazw XAML może nadal być w formie identyfikatora URI. Jednak w tym przypadku identyfikator URI jest również zadeklarowany jako pasujący identyfikator w określonym zestawie lub liście zestawów. Odbywa się to w zestawach poprzez przypisanie zestawu do <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta metoda identyfikacji przestrzeni nazw XAML i obsługa rozpoznawania typów opartych na środowisku CLR w zestawie z atrybutami jest obsługiwana przez domyślny kontekst schematu XAML w .NET Framework usługach XAML. Ogólnie rzecz biorąc, ta konwencja może być używana w przypadkach, gdy kontekst schematu XAML zawiera środowisko CLR lub opiera się na domyślnym kontekście schematu XAML, który jest niezbędny do odczytu atrybutów CLR z zestawów CLR.  
  
 Przestrzenie nazw XAML mogą być również identyfikowane przez Konwencję, która komunikuje się z przestrzenią nazw CLR i zestawem definiującym typ. Ta konwencja jest używana w przypadkach, gdy w zestawach zawierających typy nie istnieje przypisana <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta konwencja jest potencjalnie bardziej złożona niż Konwencja identyfikatora URI, a także ma możliwość niejednoznaczności i duplikowania, ponieważ istnieje wiele sposobów odwołujących się do zestawu.  
  
 Najbardziej podstawowa postać identyfikatora, który używa przestrzeni nazw CLR i Konwencji zestawu, jest następująca:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` i `; assembly=` są składnikami literału składni.  
  
 *clrnsName* jest nazwą ciągu identyfikującą przestrzeń nazw CLR. Ta nazwa ciągu zawiera wszystkie wewnętrzne znaki kropki (.), które zapewniają wskazówki dotyczące przestrzeni nazw CLR i jej relacji z innymi przestrzeniami nazw środowiska CLR.  
  
 *assemblyShortName* jest nazwą ciągu zestawu, który definiuje typy, które są przydatne w języku XAML. Typy, do których można uzyskać dostęp za pomocą zadeklarowanej przestrzeni nazw XAML, powinny być zdefiniowane przez zestaw i być jawnie zadeklarowane w przestrzeni nazw CLR określonej przez *clrnsName*. Ta nazwa ciąg zwykle określa informacje, które są raportowane przez <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Bardziej kompletna definicja przestrzeni nazw CLR i Konwencji zestawu jest następująca:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *AssemblyName*  
  
 element *AssemblyName* reprezentuje dowolny ciąg, który jest dozwolony jako dane wejściowe <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>. Ten ciąg może zawierać informacje o kulturze, kluczu publicznym lub wersji (definicje tych koncepcji są zdefiniowane w temacie referencyjnym dla <xref:System.Reflection.Assembly>). Format COFF i dowód (używany przez inne przeciążenia <xref:System.Reflection.Assembly.Load%2A>) nie mają zastosowania do celów ładowania zestawu XAML; wszystkie informacje o ładowaniu muszą być przedstawione jako ciąg.  
  
 Określenie klucza publicznego dla zestawu jest przydatną techniką dla zabezpieczeń języka XAML lub w celu usunięcia ewentualnej niejednoznaczności, która może istnieć, jeśli zestawy są załadowane przy użyciu prostej nazwy lub wcześniej istnieją w domenie lub aplikacji. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń języka XAML](xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklaracje przestrzeni nazw XAML w interfejsie API usług XAML  
 W interfejsie API usług XAML deklaracja przestrzeni nazw XAML jest reprezentowana przez obiekt <xref:System.Xaml.NamespaceDeclaration>. Jeśli deklarujesz przestrzeń nazw XAML w kodzie, wywołasz konstruktora <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>. Parametry `ns` i `prefix` są określone jako ciągi, a dane wejściowe dla tych parametrów odpowiadają definicji identyfikatora przestrzeni nazw XAML i prefiksu przestrzeni nazw XAML, jak opisano wcześniej w tym temacie.  
  
 Jeśli badasz informacje o przestrzeni nazw XAML jako część strumienia węzłów XAML lub inny dostęp do systemu typu XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> raportuje identyfikator przestrzeni nazw XAML, a <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> zgłasza prefiks przestrzeni nazw XAML.  
  
 W strumieniu węzła XAML informacje o przestrzeni nazw XAML mogą być wyświetlane jako węzeł XAML poprzedzający jednostkę, do której ma zastosowanie. Obejmuje to przypadki, w których informacje o przestrzeni nazw XAML poprzedzają `StartObject` elementu głównego XAML. Aby uzyskać więcej informacji, zobacz [Omówienie struktur i koncepcji strumienia węzła XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 W przypadku wielu scenariuszy, które używają .NET Framework interfejsu API usług XAML, oczekiwano co najmniej jednej deklaracji przestrzeni nazw XAML, a Deklaracja musi zawierać lub odwoływać się do informacji wymaganych przez kontekst schematu XAML. Przestrzenie nazw XAML muszą określać zestawy do załadowania lub pomagać w rozwiązywaniu określonych typów w przestrzeniach nazw i zestawach, które są już załadowane lub znane przez kontekst schematu XAML.  
  
 Aby można było wygenerować strumień węzłów XAML, informacje o typie XAML muszą być dostępne za pomocą kontekstu schematu XAML. Nie można ustalić informacji o typie XAML bez wcześniejszego określenia odpowiedniej przestrzeni nazw XAML dla każdego węzła do utworzenia. W tym momencie żadne wystąpienia typów nie są jeszcze tworzone, ale kontekst schematu XAML może wymagać wyszukania informacji z zestawu definiującego i typu zapasowego. Na przykład w celu przetworzenia znacznika `<Party><PartyFavor/></Party>`, kontekst schematu XAML musi być w stanie określić nazwę i typ `ContentProperty` `Party`i w związku z tym musi znać informacje o przestrzeni nazw XAML dla `Party` i `PartyFavor`. W przypadku domyślnego kontekstu schematu XAML, statyczne odbicie raportuje wiele informacji o systemie typu XAML, które są konieczne do generowania węzłów typu XAML w strumieniu węzła.  
  
 W celu wygenerowania grafu obiektów na podstawie strumienia węzłów XAML deklaracje przestrzeni nazw XAML muszą istnieć dla każdego prefiksu XAML używanego w oryginalnym oznaczeniu i zapisanego w strumieniu węzła XAML. W tym momencie wystąpienia są tworzone i występuje prawdziwe zachowanie mapowania typu.  
  
 Jeśli zachodzi potrzeba wstępnego wypełnienia informacji o przestrzeni nazw XAML, w przypadkach, gdy przestrzeń nazw XAML, w której ma zostać użyty kontekst schematu XAML, nie jest zdefiniowana w znaczniku, jedną z technik, której można użyć, jest zadeklarowanie deklaracji przestrzeni nazw XML w <xref:System.Xml.XmlParserContext> <xref:System.Xml.XmlReader>. Następnie użyj tej <xref:System.Xml.XmlReader> jako danych wejściowych dla konstruktora czytnika XAML lub <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Dwa inne interfejsy API, które mają zastosowanie do obsługi przestrzeni nazw XAML w .NET Framework usługach XAML, to atrybuty <xref:System.Windows.Markup.XmlnsDefinitionAttribute> i <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Te atrybuty mają zastosowanie do zestawów. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jest używany przez kontekst schematu XAML do interpretacji deklaracji przestrzeni nazw XAML, która zawiera identyfikator URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> jest używany przez narzędzia, które emitują XAML, aby można było serializować określoną przestrzeń nazw XAML z przewidywalnym prefiksem. Aby uzyskać więcej informacji, zobacz [atrybuty CLR związane z językiem XAML dla niestandardowych typów i bibliotek](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie struktur i koncepcji strumienia węzłów XAML](understanding-xaml-node-stream-structures-and-concepts.md)
