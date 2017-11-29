---
title: "Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2798659d3b53cb32af8e5976d4fee69780266633
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML
Dalej w tym temacie opisano obecności i celem dwóch mapowania przestrzeni nazw XAML tyle razy, znaleziony w tagu głównym pliku XAML w WPF. Również zawiera opis sposobu tworzenia podobne mapowania dla przy użyciu elementów zdefiniowanych w swoim własnym kodem i/lub w ramach oddzielne zestawy.  
  
  
## <a name="what-is-a-xaml-namespace"></a>Co to jest Namespace XAML?  
 Przestrzeń nazw XAML naprawdę jest rozszerzeniem pojęcia przestrzeni nazw XML. Określenie przestrzeni nazw XAML technik polegać na składni przestrzeni nazw XML z Konwencją przy użyciu identyfikatorów URI jako identyfikatory przestrzeni nazw, używanie prefiksów w celu zapewnienia sposób odwoływać się wiele obszarów nazw z tego samego źródła znaczników i tak dalej. Podstawowe pojęcia dodawanej do definicji XAML przestrzeni nazw XML jest oznacza zarówno zakres unikatowości użycia znaczników przestrzeni nazw XAML, a także wpływa na sposób znaczników jednostki są potencjalnie obsługiwanej przez określone obszary nazw CLR i odwołuje się do zestawy. Ten ostatni brany pod uwagę także ma wpływ pojęcie kontekst schematu XAML. Ale w celu jak WPF współpracuje z przestrzeni nazw XAML, można zwykle traktować przestrzeni nazw XAML pod względem domyślnej przestrzeni nazw XAML, przestrzeń nazw języka XAML i wszelkie dodatkowe przestrzenie nazw XAML, jako mapowany przez użytkownika znaczników XAML bezpośrednio do określonej zapasowego typu CLR obszary nazw i zestawy występujące w odwołaniach.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF i deklaracji Namespace XAML  
 W deklaracji przestrzeni nazw w tagu głównym wiele plików XAML zobaczysz, że są zwykle dwóch deklaracji przestrzeni nazw XML. Pierwszą deklaracją mapuje ogólną klienta WPF / przestrzeni nazw XAML framework jako domyślne:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druga deklaracja mapuje oddzielne nazw XAML (zwykle) do jego mapowania `x:` prefiks.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Relacja między deklaracji jest to, że `x:` mapowanie prefiksu obsługuje funkcje wewnętrzne, które są częścią definicji języka XAML, i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest jedna implementacja używa jako języka XAML, który definiuje słownik z jego obiekty dla języka XAML. Ponieważ użycia słownictwa WPF będzie znacznie częściej niż użycia funkcje wewnętrzne XAML, słownictwa WPF jest mapowany jako domyślny.  
  
 `x:` Konwencji prefiks mapowania obsługi funkcje wewnętrzne języka XAML następuje szablony projektów przykładowy kod i dokumentację języka funkcje w ramach tego [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Przestrzeń nazw XAML definiuje wiele funkcji najczęściej używanych, które są niezbędne, nawet w przypadku podstawowej aplikacji WPF. Na przykład, aby dołączyć wszystkie kodem do pliku XAML do klasy częściowej, nazwę tej klasy jako `x:Class` atrybutu w głównym elemencie odpowiedniego pliku XAML. Lub, w dowolnym elemencie zgodnie z definicją w strony XAML, który chcesz uzyskać dostęp jako kluczem zasobu powinna mieć `x:Key` atrybutu ustawionej dla elementu zagrożona. Aby uzyskać więcej informacji na temat tych i innych aspektów XAML, zobacz [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) lub [szczegółów w składni języka XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapowanie do zestawów i klas niestandardowych  
 Przestrzenie nazw XML można mapować na zestawy, używając szeregu tokenów wewnątrz `xmlns` prefiksu deklaracji, podobnie jak standardowy WPF i XAML — funkcje wewnętrzne XAML przestrzenie nazw są mapowane na prefiksy.  
  
 Składnia przyjmuje następujące możliwe tokeny nazwane i następujące wartości:  
  
 `clr-namespace:`Przestrzeń nazw środowiska CLR zadeklarowany w obrębie zestawu, który zawiera typy publiczne jako elementy.  
  
 `assembly=`Zestaw zawierający niektóre lub wszystkie przywoływana [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw. Ta wartość jest zazwyczaj tylko nazwę zestawu, a nie ścieżkę i nie ma rozszerzenia (takie jak .dll lub .exe). Ścieżka do tego zestawu, należy ustanowić jako odwołanie do projektu w pliku projektu, który zawiera XAML próbujesz mapy. Aby włączyć przechowywanie wersji i podpisywanie silną nazwą, `assembly` wartość może być ciągiem, zgodnie z definicją w <xref:System.Reflection.AssemblyName>, a nie nazwę prostego ciągu.  
  
 Należy pamiętać, że znak oddzielanie `clr-namespace` tokenu z jego wartość jest dwukropkiem (:) oddzielanie znak `assembly` tokenu z jego wartość jest znak równości (=). Znak między tych dwóch tokenów jest średnikiem. Ponadto nie zawierają żadnych spacji dowolne miejsce w deklaracji.  
  
### <a name="a-basic-custom-mapping-example"></a>Przykład podstawowego mapowania niestandardowe  
 Poniższy kod definiuje klasę niestandardowych przykład:  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 Ta klasa niestandardowych następnie jest kompilowany do biblioteki, który zgodnie z ustawieniami projektu (tego nie pokazano) o nazwie `SDKSampleLibrary`.  
  
 Aby można było odwołać tej klasy niestandardowej, należy również dołączyć ją jako punkt odniesienia dla bieżącego projektu, które zwykle należy za pomocą interfejsu użytkownika z Eksploratora rozwiązań w programie Visual Studio.  
  
 Teraz, gdy masz biblioteką klasę i odwołanie do niej w ustawieniach projektu można dodać następującego mapowania prefiks jako część w elemencie głównym w języku XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Aby zebranie wszystkich elementów, poniżej przedstawiono XAML zawiera niestandardowe mapowanie wraz z typowy domyślny i mapowania x: w tagu głównym, a następnie używa prefiksem odwołania do wystąpienia `ExampleClass` w tym interfejsie użytkownika:  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>Mapowanie do bieżącego zestawów  
 `assembly`można pominąć, jeśli `clr-namespace` przywoływanego mieści się w tym samym zestawie co kod aplikacji, która odwołuje się do klas niestandardowych. Lub równoważne składni dla tej sprawy jest określenie `assembly=`, nie tokenem ciągu po znaku równości.  
  
 Nie można użyć niestandardowej klasy jako element główny strony, jeśli została zdefiniowana w tym samym zestawie. Klasy częściowe nie muszą być mapowane; tylko klasy, które nie są częściowej klasy strony w potrzeb aplikacji można mapować, jeśli zamierzasz odwoływać je jako elementy w języku XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Przestrzenie nazw CLR mapowania do przestrzeni nazw XML w zestawie  
 WPF definiuje atrybut CLR, który jest używany przez procesorów XAML w celu zamapowania wiele nazw CLR jedna przestrzeń nazw XAML. Ten atrybut <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, znajduje się na poziomie zestawu w kodzie źródłowym, który spowoduje utworzenie zestawu. Kod źródłowy zestawu WPF używa tego atrybutu do mapowania różnych wspólnej przestrzeni nazw, takich jak <xref:System.Windows> i <xref:System.Windows.Controls>, do [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] przestrzeni nazw.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Przyjmuje dwa parametry: Nazwa przestrzeni nazw XML/XAML i nazwa przestrzeni nazw CLR. Więcej niż jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> może istnieć do mapowania wielu nazw środowiska CLR do tego samego obszaru nazw XML. Zmapowaniu, członkowie tych obszarów nazw mogą się też odwoływać bez pełnej kwalifikacji w razie potrzeby, podając odpowiednie `using` instrukcji na stronie kodem klasy częściowe. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Projektanta obszary nazw i inne prefiksy z szablonów XAML  
 Podczas pracy z środowisk deweloperskich i/lub narzędzia do projektowania dla WPF XAML, można zauważyć, że istnieją inne określonych przestrzeni nazw XAML / prefiksy w kodzie XAML.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]używa projektanta przestrzeni nazw, która zwykle jest zamapowana na prefiks `d:`. Nowych szablonów projektu dla WPF mogą być mapowane wstępnie tej przestrzeni nazw XAML do obsługi wymiany XAML między [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] i innych środowisk projektowania. Ta przestrzeń nazw XAML projektu jest używany do widoczny przy obsłudze często stan projektu podczas roundtripping opartych na języku XAML interfejsu użytkownika w projektancie. Jest również używana w przypadku funkcji takich jak `d:IsDataSource`, umożliwiające środowiska uruchomieniowego źródeł danych w projektancie.  
  
 Inny prefiks można napotkać mapowany jest `mc:`. `mc:`dla znaczników zgodności i polega na wykorzystaniu wzorca zgodności znaczników, który nie jest zawsze specyficzne dla języka XAML. W pewnym stopniu zgodności znaczników, funkcje mogą być używane do wymiany XAML między struktury lub inne bariery implementacji zapasowy pracy między kontekst schematu XAML, zapewniają zgodność dla trybów ograniczony w projektantach i tak dalej. Aby uzyskać więcej informacji na znaczników zgodności pojęcia i ich relacji z WPF, zobacz [zgodności znaczników (mc:) Funkcje języka](../../../../docs/framework/wpf/advanced/markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF i ładowania zestawu  
 Kontekst schematu WPF XAML integruje się z modelem aplikacji WPF, który z kolei używa pojęcie zdefiniowane CLR <xref:System.AppDomain>. Następująca sekwencja opisano, jak kontekst schematu XAML interpretuje jak ładowanie zestawów albo znaleźć typów w czasie wykonywania lub projektu, na podstawie z użyciem WPF <xref:System.AppDomain> i innych czynników.  
  
1.  Iterowanie za pomocą <xref:System.AppDomain>, wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwy, zaczynając od ostatniego załadowanego zestawu.  
  
2.  Jeśli nazwa jest kwalifikowana, wywołanie <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> w kwalifikowanej nazwie.  
  
3.  Jeśli krótka nazwa + token klucza publicznego kwalifikowana nazwa pasuje do zestawu, który znaczników został załadowany z, zwróć tego zestawu.  
  
4.  Użyj krótką nazwę + token klucza publicznego do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5.  W przypadku niekwalifikowana nazwa wywołania <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Luźne XAML nie korzysta z kroku 3; Nie załadowano z zestawu nie istnieje.  
  
 Skompilowany XAML dla WPF (wygenerowane za pomocą XamlBuildTask) nie korzysta z zestawów już załadowany z <xref:System.AppDomain> (krok 1). Ponadto nazwa nigdy nie należy niekwalifikowane z danych wyjściowych XamlBuildTask, tak, aby nie stosować krok 5.  
  
 Skompilowany BAML (wygenerowane za pomocą PresentationBuildTask) używa wszystkich kroków, chociaż BAML również nie powinny zawierać zestaw niekwalifikowanych nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Opis przestrzeni nazw XML](http://go.microsoft.com/fwlink/?LinkId=98069)  
 [Omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
