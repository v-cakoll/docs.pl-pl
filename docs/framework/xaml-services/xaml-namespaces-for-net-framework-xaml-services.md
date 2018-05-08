---
title: Przestrzeń nazw dla usług .NET Framework XAML
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 842cfb31e21c59bb886ccd266d19c40c64557519
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Przestrzeń nazw dla usług .NET Framework XAML
Przestrzeń nazw XAML jest działaniem rozwijający w definicji obszaru nazw XML. Podobnie jak w przestrzeni nazw XML, można określić przestrzeń nazw XAML przy użyciu `xmlns` atrybutów w znaczniku. Przestrzeń nazw XAML również są przedstawiane w strumieniu węzłów XAML i innych interfejsów API usługi języka XAML. W tym temacie wprowadzono pojęcie przestrzeni nazw XAML i opisuje sposób przestrzeń nazw XAML mogą być definiowane i są używane przez kontekst schematu XAML i inne aspekty usług .NET Framework XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML i Namespace XAML  
 Przestrzeń nazw XAML jest specjalne przestrzeni nazw XML, tak samo, jak XAML jest specjalna forma XML i używa podstawowej postaci XML dla jego znacznika. W znaczniku, należy zadeklarować przestrzeni nazw XAML i jego mapowania za pomocą `xmlns` atrybut zastosowany do elementu. `xmlns` Deklaracja może się samemu elementowi, zadeklarowana w przestrzeni nazw XAML. Deklaracja przestrzeni nazw XAML do elementu jest nieprawidłowa dla tego elementu, wszystkie atrybuty tego elementu, a wszystkie elementy podrzędne tego elementu. Atrybuty można użyć przestrzeni nazw XAML, który nie jest, taki sam jak element, który zawiera atrybut tak długo, jak prefiks odwołuje się nazwa atrybutu jako część nazwy atrybutów w znaczniku.  
  
 Różnica w przestrzeni nazw XAML i przestrzeni nazw XML nie mogą być wykorzystane do odwołuje się do schematu przestrzeni nazw XML, lub mogą być wykorzystane do odróżnienia po prostu jednostek. Dla języka XAML typy i elementy członkowskie w XAML ostatecznie muszą zostać rozwiązane do tworzenia kopii typów, a pojęcia schematu XML nie dotyczą również tej możliwości. Przestrzeń nazw XAML zawiera informacje, które kontekst schematu XAML muszą być dostępne w celu wykonania tego mapowania typu.  
  
## <a name="xaml-namespace-components"></a>Składniki Namespace XAML  
 Definicja przestrzeni nazw XAML zawiera dwa składniki: prefiks i identyfikator. Każdy z tych składników są dostępne dla przestrzeni nazw XAML jest zadeklarowany w znaczniku lub zdefiniowane w systemie typów języka XAML.  
  
 Prefiks może być dowolnym ciągiem, zgodnie z [przestrzenie nazw W3C w specyfikacji XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735) . Według Konwencji prefiksy są zazwyczaj bardzo krótkich ciągów, ponieważ prefiks jest powtarzany tyle razy w pliku znaczników typowych. Niektórych przestrzeni nazw XAML, które mają być używane w wielu wdrożeniach XAML użyć konkretnego z konwencjonalnej prefiksy. Na przykład przestrzeni nazw XAML języka XAML jest zwykle mapować przy użyciu prefiksu `x`. Można zdefiniować domyślny XAML przestrzeni nazw, gdy prefiks nie zostanie podany w definicji, ale jest reprezentowany jako ciąg pusty, jeśli definicja lub zbadać by.NET Framework XAML Services API. Zazwyczaj domyślnej przestrzeni nazw XAML celowo jest wybierany Aby podwyższyć poziom zmaksymalizowane ilość pominięcie prefiks znacznika przez Implementowanie XAML technologii i scenariuszy i vocabularies.  
  
 Identyfikator może być dowolnym ciągiem, zgodnie z [przestrzenie nazw W3C w specyfikacji XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735). Według Konwencji identyfikatorów dla przestrzeni nazw XML lub przestrzeń nazw XAML często podano w formie identyfikatora URI, zazwyczaj jako bezwzględnego identyfikatora URI kwalifikowana protokołu. Często informacje o wersji, który definiuje określonego słownika XAML jest domyślna jako część ciągu ścieżki. Przestrzeń nazw XAML dodać Konwencji identyfikatora dodatkowe poza Konwencji identyfikatora XML URI. W przypadku przestrzeni nazw XAML identyfikator komunikuje się informacje, które są wymagane przez kontekst schematu XAML, aby rozpoznać typy, które są określone jako elementy w tej przestrzeni nazw XAML lub rozwiązać atrybutów do elementów członkowskich.  
  
 W celu przekazywania informacji do kontekst schematu XAML identyfikator przestrzeni nazw XAML może nadal być w formie identyfikatora URI. Jednak w takim przypadku identyfikatora URI jest również zadeklarowany jako pasującym identyfikatorem, w szczególności zestawu lub lista zestawów. Odbywa się w zestawach poprzez przypisywanie zestaw z <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Ta metoda identyfikowania przestrzeni nazw XAML i obsługa sposób rozpoznawania typu na podstawie CLR w zestawie oparte na atrybutach jest obsługiwana przez domyślny kontekst schematu XAML w usługach programu .NET Framework XAML. Ogólnie rzecz biorąc tę Konwencję może służyć do przypadkach, gdy kontekst schematu XAML zawiera CLR lub opiera się na domyślny kontekst schematu XAML, który jest konieczny do odczytu atrybuty CLR z zestawów CLR.  
  
 Przestrzeń nazw XAML mogą również zidentyfikowane przez Konwencję komunikującego przestrzeń nazw CLR i zestawem Definiowanie typu. Tę Konwencję jest używany w przypadku, jeśli nie <xref:System.Windows.Markup.XmlnsDefinitionAttribute> autorstwa istnieje w zestawy, które zawierają typy. Konwencja jest potencjalnie bardziej skomplikowane niż Konwencji identyfikatora URI i ma również możliwości niejednoznaczności i duplikatów, ponieważ istnieje wiele sposobów odwoływania się do zestawu.  
  
 Najbardziej podstawowa formę identyfikatora, który używa konwencji przestrzeń nazw i zestawu CLR jest następujący:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` i `; assembly=` są składnikami literału składni.  
  
 *clrnsName* jest nazwa ciągu, który identyfikuje przestrzeń nazw CLR. Ta nazwa ciągu obejmuje wszystkie znaki wewnętrzny kropka (.), które udostępnia wskazówek dotyczących przestrzeń nazw środowiska CLR i jego powiązanie innych przestrzeniach nazw CLR.  
  
 *assemblyShortName* jest nazwą ciągu zestawu, który definiuje typy, które są przydatne w języku XAML. Oczekiwane są typy przy użyciu przestrzeni nazw XAML zadeklarowane, określonych przez zestaw, a w szczególności można zadeklarować w przestrzeni nazw CLR określony przez *clrnsName*. Ta nazwa ciągu zwykle równoleżnikami informacje zgodnie z raportem <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Bardziej szczegółowy definicję Konwencji przestrzeń nazw i zestawu CLR jest następujący:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* reprezentuje dowolny ciąg, który jest dozwolony jako <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> wejściowego. Ten ciąg może zawierać kultury, klucz publiczny lub informacje o wersji (definicje tych założeń są definiowane w temacie dotyczącym <xref:System.Reflection.Assembly>). COFF format i dokumentów (jak używany przez inne przeciążenia <xref:System.Reflection.Assembly.Load%2A>) nie są istotne dla celów; ładowanie zestawu XAML wszystkie informacje obciążenia muszą być przedstawione jako ciąg.  
  
 Określanie klucza publicznego dla zestawu to technika przydatne dla zabezpieczeń XAML lub usuwania niejednoznaczności możliwe, że mogą istnieć zestawy są ładowane przez prostą nazwą, czy wstępnie istnieje w domenie z pamięci podręcznej lub aplikacji. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklaracje Namespace XAML w usługach XAML interfejsu API  
 W interfejsie API usług XAML deklaracji przestrzeni nazw XAML jest reprezentowana przez <xref:System.Xaml.NamespaceDeclaration> obiektu. Jeśli są deklarowanie przestrzeni nazw XAML w kodzie, należy wywołać <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> konstruktora. `ns` i `prefix` parametry są określane jako ciągi i podanie tych parametrów w danych wejściowych odpowiada definicji z identyfikatorem przestrzeni nazw XAML i prefiks przestrzeni nazw XAML zgodnie z wcześniej w tym temacie.  
  
 Jeśli są badanie informacji dotyczących przestrzeni nazw XAML w ramach strumienia węzłów XAML lub przez inne dostępu do sieci typu XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> identyfikatorem przestrzeni nazw XAML, raporty i <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> raporty prefiks przestrzeni nazw XAML.  
  
 W strumieniu węzłów XAML informacji dotyczących przestrzeni nazw XAML może występować jako węzeł XAML poprzedzający jednostki, której dotyczy. Dotyczy to przypadków, w którym poprzedza informacji dotyczących przestrzeni nazw XAML `StartObject` elementu głównego XAML. Aby uzyskać więcej informacji, zobacz [opis XAML węzła strukturami i koncepcjami strumienia](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Dla wielu scenariuszy korzystających z interfejsu API programu .NET Framework XAML Services powinna występować co najmniej jedną deklarację przestrzeni nazw XAML, a deklaracja musi zawierać lub odwoływać się do informacji, który jest wymagany przez kontekst schematu XAML. Przestrzeń nazw XAML musi określić zestawów do załadowania lub pomóc w rozwiązaniu określonych typów w przestrzeni nazw i zestawy, które już są załadowane lub znany przez kontekst schematu XAML.  
  
 Aby można było wygenerować strumień węzłów XAML, informacje o typie XAML musi być dostępny za pośrednictwem kontekst schematu XAML. Nie można ustalić informacji o typie XAML bez pierwszy określania odpowiednich przestrzeni nazw XAML dla każdego węzła do utworzenia. W tym momencie utworzone nie wystąpienia typów, ale kontekst schematu XAML może być konieczne do wyszukiwania informacji z zestawu definiującego i tworzenie kopii typu. Na przykład, aby przetworzyć znaczników `<Party><PartyFavor/></Party>`, kontekst schematu XAML musi być możliwe ustalenie, nazwę i typ `ContentProperty` z `Party`i w związku z tym również musi znać informacji dotyczących przestrzeni nazw XAML dla `Party` i `PartyFavor`. W przypadku domyślny kontekst schematu XAML statyczne odbicia raporty wiele informacji system typu XAML, który jest potrzebny do generowania węzłów typu XAML w strumieniu węzłów.  
  
 Aby można było wygenerować grafu obiektów ze strumienia węzłów XAML, deklaracje przestrzeni nazw XAML musi istnieć dla każdego prefiksu XAML używane w oryginalnej znaczników i zapisane w strumieniu węzłów XAML. W tym momencie tworzone są wystąpienia, a wartość true, mapowanie typu zachowanie.  
  
 Aby wstępnie wypełnić informacji dotyczących przestrzeni nazw XAML, w przypadkach, gdzie przestrzeni nazw XAML mają kontekst schematu XAML do użycia nie jest zdefiniowany w znaczniku, co technika, można użyć jest aby zadeklarować deklaracje przestrzeni nazw XML w <xref:System.Xml.XmlParserContext> dla <xref:System.Xml.XmlReader>. Użyj tego <xref:System.Xml.XmlReader> jako dane wejściowe dla konstruktora czytnika XAML lub <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Atrybuty są dwa API, które są odpowiednie dla przestrzeni nazw XAML Obsługa w .NET Framework XAML Services <xref:System.Windows.Markup.XmlnsDefinitionAttribute> i <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Te atrybuty stosowane do zestawów. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jest używany przez kontekst schematu XAML interpretować wszystkie deklaracji przestrzeni nazw XAML, który zawiera identyfikator URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> jest używana przez narzędzia, które Emituj XAML, aby określonej przestrzeni nazw XAML może być Zserializowany z prefiksem przewidywalne. Aby uzyskać więcej informacji, zobacz [XAML-Related atrybuty CLR dotyczące niestandardowych typów i bibliotek](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie struktur i koncepcji strumienia węzłów XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
