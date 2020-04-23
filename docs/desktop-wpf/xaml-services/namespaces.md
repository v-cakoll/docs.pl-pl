---
title: Przestrzenie nazw XAML dla usług .NET XAML
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071844"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a>Przestrzenie nazw XAML dla usług .NET XAML
Obszar nazw XAML to koncepcja, która rozszerza definicję obszaru nazw XML. Podobnie jak w przypadku obszaru nazw XML, można zdefiniować obszar nazw XAML przy użyciu atrybutu `xmlns` w znacznikach. Przestrzenie nazw XAML są również reprezentowane w strumieniu węzłów XAML i innych interfejsach API usług XAML. W tym temacie zdefiniowano koncepcję przestrzeni nazw XAML i opisano, jak obszary nazw XAML mogą być definiowane i używane przez konteksty schematu XAML i inne aspekty usług XAML .NET.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Obszar nazw XML i obszar nazw XAML  
 Obszar nazw XAML jest wyspecjalizowaną przestrzenią nazw XML, podobnie jak XAML jest wyspecjalizowaną formą XML i używa podstawowego formularza XML dla znaczników. W znacznikach deklarujesz obszar nazw XAML i `xmlns` jego mapowanie za pomocą atrybutu zastosowanego do elementu. Deklarację `xmlns` można dokonać do tego samego elementu, w który jest zadeklarowany obszar nazw XAML. Deklaracja przestrzeni nazw XAML do elementu jest prawidłowa dla tego elementu, wszystkie atrybuty tego elementu i wszystkie elementy podrzędne tego elementu. Atrybuty można użyć przestrzeni nazw XAML, który nie jest taki sam jak element, który zawiera atrybut, tak długo, jak sama nazwa atrybutu odwołuje się do prefiksu jako część jego nazwy atrybutu w znacznikach.  
  
 Rozróżnienie obszaru nazw XAML w porównaniu z obszarem nazw XML polega na tym, że obszar nazw XML może być używany do odwoływania się do schematu lub po prostu do rozróżniania jednostek. W przypadku xaml typy i elementy członkowskie używane w XAML muszą ostatecznie zostać rozpoznane do typów kopii zapasowych, a pojęcia schematu XML nie mają również zastosowania do tej możliwości. Obszar nazw XAML zawiera informacje, które kontekst schematu XAML musi być dostępny w celu wykonania mapowania tego typu.  
  
## <a name="xaml-namespace-components"></a>Składniki obszaru nazw XAML  
 Definicja obszaru nazw XAML ma dwa składniki: prefiks i identyfikator. Każdy z tych składników jest obecny, gdy obszar nazw XAML jest zadeklarowany w znacznikach lub zdefiniowany w systemie typu XAML.  
  
 Prefiks może być dowolny ciąg, jak dozwolone przez [W3C Przestrzenie nazw w specyfikacji XML 1.0](https://www.w3.org/TR/REC-xml-names/). Zgodnie z konwencją prefiksy są zazwyczaj krótkie ciągi, ponieważ prefiks jest powtarzany wiele razy w typowym pliku znaczników. Niektóre obszary nazw XAML, które są przeznaczone do użycia w wielu implementacjach XAML, używają określonych prefiksów konwencjonalnych. Na przykład obszar nazw XAML języka XAML języka XAML jest zazwyczaj mapowany przy użyciu prefiksu `x`. Można zdefiniować domyślny obszar nazw XAML, gdzie prefiks nie jest podany w definicji, ale jest reprezentowany jako pusty ciąg, jeśli jest zdefiniowany lub by.NET wyszukiwany by.NET interfejsu API usług XAML. Zazwyczaj domyślny obszar nazw XAML jest celowo wybierany w celu promowania zmaksymalizowanej ilości znaczników pomijających prefiks przez technologię implementującą XAML oraz jej scenariusze i słownictwo.  
  
 Identyfikatorem może być dowolny ciąg znaków dozwolony przez [obszary nazw W3C w specyfikacji XML 1.0](https://www.w3.org/TR/REC-xml-names/). Zgodnie z konwencją identyfikatory obszarów nazw XML lub XAML są często podane w formularzu URI, zazwyczaj jako bezwzględny identyfikator URI kwalifikowany do protokołu. Często informacje o wersji, która definiuje określone słownictwo XAML jest implikowane jako część ciągu ścieżki. Przestrzenie nazw XAML dodają dodatkową konwencję identyfikatorów poza konwencją URI XML. W przypadku obszarów nazw XAML identyfikator komunikuje informacje, które są potrzebne w kontekście schematu XAML w celu rozwiązania typów, które są określone jako elementy w tym obszarze nazw XAML lub w celu rozpoznania atrybutów dla członków.  
  
 Na potrzeby przekazywania informacji do kontekstu schematu XAML identyfikator obszaru nazw XAML może nadal być w formie identyfikatora URI. Jednak w tym przypadku identyfikator URI jest również zadeklarowany jako pasujący identyfikator w określonym zestawie lub na liście zestawów. Odbywa się to w złożeniach, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>przypisując zestaw za pomocą . Ta metoda identyfikowania obszaru nazw XAML i obsługi zachowania rozpoznawania typów na podstawie platformy CLR w przypisanym zestawie jest obsługiwana przez domyślny kontekst schematu XAML w usługach .NET XAML Services. Bardziej ogólnie tej konwencji może służyć w przypadkach, gdy kontekst schematu XAML zawiera CLR lub opiera się na domyślnym kontekście schematu XAML, który jest niezbędny do odczytu atrybutów CLR z zestawów CLR.  
  
 Przestrzenie nazw XAML mogą być również identyfikowane przez konwencję, która komunikuje obszar nazw CLR i zestaw definiujący typ. Ta konwencja jest używana <xref:System.Windows.Markup.XmlnsDefinitionAttribute> w przypadkach, gdy nie istnieje przypisanie w zestawach, które zawierają typy. Ta konwencja jest potencjalnie bardziej złożone niż konwencja URI, a także ma potencjał niejednoznaczności i powielania, ponieważ istnieje wiele sposobów odwoływania się do zestawu.  
  
 Najbardziej podstawową formą identyfikatora, który używa obszaru nazw CLR i konwencji zestawu jest w następujący sposób:  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 `clr-namespace:`i `; assembly=` są dosłowne składniki składni.  
  
 *clrnsName* jest nazwą ciągu identyfikującego obszar nazw CLR. Ta nazwa ciągu zawiera wszystkie wewnętrzne znaki kropki (.), które zawierają wskazówki dotyczące obszaru nazw CLR i jego relacji z innymi obszarami nazw CLR.
  
 *assemblyShortName* jest nazwą ciągu zestawu, który definiuje typy, które są przydatne w XAML. Typy, które mają być dostępne za pośrednictwem zadeklarowanej przestrzeni nazw XAML oczekuje się, że zostaną zdefiniowane przez zestaw i mają być zadeklarowane w obszarze nazw CLR określonym przez *clrnsName*. Ta nazwa ciągu zazwyczaj jest równoległa <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>do informacji zgłoszonych przez program .  
  
 Bardziej kompletna definicja obszaru nazw CLR i konwencji zestawu jest następująca:  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 *assemblyName* reprezentuje dowolny ciąg, <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> który jest legalny jako dane wejściowe. Ten ciąg może zawierać informacje o kulturze, kluczu publicznym lub wersji (definicje tych pojęć są zdefiniowane w temacie odniesienia dla <xref:System.Reflection.Assembly>). Format i dowody COFF (używane przez <xref:System.Reflection.Assembly.Load%2A>inne przeciążenia) nie są istotne dla celów ładowania zespołu XAML; wszystkie informacje o obciążeniu muszą być przedstawione jako ciąg.  
  
 Określenie klucza publicznego dla zestawu jest użyteczną techniką zabezpieczeń XAML lub usuwania możliwych niejednoznaczności, które mogą istnieć, jeśli zestawy są ładowane przez prostą nazwę lub wstępnie istnieją w domenie pamięci podręcznej lub aplikacji. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące zabezpieczeń XAML](security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklaracje obszaru nazw XAML w interfejsie API usług XAML  
 W interfejsie API usług XAML deklaracja obszaru nazw <xref:System.Xaml.NamespaceDeclaration> XAML jest reprezentowana przez obiekt. Jeśli deklarujesz obszar nazw XAML w kodzie, należy wywołać konstruktora. <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> Parametry `ns` `prefix` i są określone jako ciągi, a dane wejściowe, aby zapewnić dla tych parametrów odpowiada definicji identyfikatora przestrzeni nazw XAML i prefiks przestrzeni nazw XAML, jak podano wcześniej w tym temacie.  
  
 W przypadku sprawdzania informacji o obszarze nazw XAML w ramach strumienia węzła XAML <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> lub innego dostępu do systemu typu <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> XAML należy zgłaszać identyfikator obszaru nazw XAML i zgłasza prefiks obszaru nazw XAML.  
  
 W strumieniu węzła XAML informacje o przestrzeni nazw XAML mogą być wyświetlane jako węzeł XAML, który poprzedza jednostkę, do której ma zastosowanie. Obejmuje to przypadki, w których informacje o `StartObject` przestrzeni nazw XAML poprzedzają element główny XAML. Aby uzyskać więcej informacji, zobacz [Opis struktur i pojęć strumienia węzłów XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 W wielu scenariuszach, które używają interfejsu API usług .NET XAML, oczekuje się, że istnieje co najmniej jedna deklaracja obszaru nazw XAML, a deklaracja musi zawierać lub odwoływać się do informacji wymaganych przez kontekst schematu XAML. Przestrzenie nazw XAML muszą określać zestawy, które mają być ładowane, lub pomagać w rozpoznawaniu określonych typów w obszarach nazw i zestawach, które są już załadowane lub znane w kontekście schematu XAML.  
  
 Aby wygenerować strumień węzła XAML, informacje o typie XAML muszą być dostępne za pośrednictwem kontekstu schematu XAML. Nie można określić informacji o typie XAML bez uprzedniego określenia odpowiedniego obszaru nazw XAML dla każdego węzła do utworzenia. W tym momencie nie wystąpienia typów są jeszcze tworzone, ale kontekst schematu XAML może być konieczne wyszukanie informacji z definiowania zestawu i typu kopii zapasowej. Na przykład, aby przetworzyć `<Party><PartyFavor/></Party>`znaczniki, kontekst schematu XAML musi być w `ContentProperty` `Party`stanie określić nazwę i typ , a `Party` `PartyFavor`zatem musi również znać informacje o przestrzeni nazw XAML dla i . W przypadku domyślnego kontekstu schematu XAML statyczne odbicie raportuje wiele informacji o systemie typu XAML, które są potrzebne do generowania węzłów typu XAML w strumieniu węzłów.  
  
 Aby wygenerować wykres obiektu ze strumienia węzła XAML, deklaracje przestrzeni nazw XAML muszą istnieć dla każdego prefiksu XAML używanego w oryginalnym znaczniku i rejestrowanego w strumieniu węzła XAML. W tym momencie są tworzone wystąpienia i występuje zachowanie mapowania typu true.  
  
 Jeśli chcesz wstępnie wypełnić informacje o przestrzeni nazw XAML, w przypadkach, gdy obszar nazw XAML, którego zamierzasz użyć kontekst schematu XAML, nie jest <xref:System.Xml.XmlParserContext> zdefiniowany <xref:System.Xml.XmlReader>w znacznikach, jedną z technik, których można użyć, jest deklarowanie deklaracji obszaru nazw XML w forach . Następnie użyj <xref:System.Xml.XmlReader> tego jako danych wejściowych dla <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>konstruktora czytnika XAML lub .  
  
 Dwa inne interfejsy API, które są istotne dla obsługi obszaru nazw XAML w usługach .NET XAML są atrybuty <xref:System.Windows.Markup.XmlnsDefinitionAttribute> i <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Te atrybuty mają zastosowanie do zestawów. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>jest używany przez kontekst schematu XAML do interpretacji dowolnej deklaracji przestrzeni nazw XAML, która zawiera identyfikator URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>jest używany przez narzędzia, które emitują XAML, dzięki czemu określonego obszaru nazw XAML mogą być serializowane z przewidywalnym prefiksem. Aby uzyskać więcej informacji, zobacz [Atrybuty CLR związane z XAML dla typów niestandardowych i bibliotek](clr-attributes-with-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zapoznanie się ze strukturami i koncepcjami strumienia węzłów XAML](understanding-xaml-node-stream-structures-and-concepts.md)
