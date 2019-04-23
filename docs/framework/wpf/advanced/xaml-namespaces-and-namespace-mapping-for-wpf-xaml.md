---
title: Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML
ms.date: 03/30/2017
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
ms.openlocfilehash: c238bd3c014c07c541bed0c8f7bc12fc5a910f1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301038"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML
Dalej w tym temacie opisano obecności i celem dwóch mapowań przestrzeni nazw XAML, jak często występuje w tagu głównego pliku XAML w WPF. On również zawiera opis sposobu tworzenia podobnych mapowania dla za pomocą elementów, które są zdefiniowane we własnym kodzie i/lub w ramach oddzielne zestawy.  

## <a name="what-is-a-xaml-namespace"></a>Co to jest Namespace XAML?  
 Przestrzeń nazw XAML tak naprawdę to rozszerzenie pojęcia obszar nazw XML. Techniki określania przestrzeni nazw XAML zależą od składni przestrzeni nazw XML Konwencji za pomocą identyfikatorów URI jako identyfikatory przestrzeni nazw, przy użyciu prefiksy zapewnienie sposób odwoływać się wiele przestrzeni nazw z tego samego źródła znaczników i tak dalej. Podstawowe pojęcia, dodane do definicji XAML przestrzeni nazw XML jest nazw XAML oznacza zarówno zakres unikatowości użycia znaczników i również wpływ na sposób jednostek znaczników potencjalnie są wspierane przez określonych przestrzeni nazw CLR i odwołanie do zestawy. Ten ostatni brany pod uwagę także ma wpływ koncepcji kontekst schematu XAML. Ale w celu współdziałania WPF z przestrzeni nazw XAML, można zwykle traktować przestrzeni nazw XAML w kontekście domyślna przestrzeń nazw XAML, przestrzeni nazw języka XAML i wszelkie dodatkowe przestrzenie nazw XAML, ponieważ mapowany przez znaczników XAML bezpośrednio do określonej zapasowego typu CLR przestrzenie nazw i przywoływanych zestawów.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF i deklaracji Namespace XAML  
 W ramach deklaracji przestrzeni nazw w tagu głównego wiele plików XAML zobaczysz, że zwykle istnieją dwie deklaracje przestrzeni nazw XML. Pierwszej deklaracji mapuje ogólnych klienta WPF / framework przestrzeń nazw XAML jako domyślny:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Drugi deklaracji mapuje oddzielnych przestrzeni nazw XAML, mapowania ich (zazwyczaj) do `x:` prefiks.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Relacja między tych deklaracji jest to, że `x:` mapowanie prefiksu obsługuje funkcje wewnętrzne, które są częścią definicji języka XAML, i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jest jedna implementacja używa XAML jako język, który definiuje słownictwa używanego w jego obiekty dla XAML. Ponieważ słownictwa WPF użycia będzie znacznie częściej niż użycia funkcji wewnętrznych XAML, słownictwa WPF jest mapowany jako domyślny.  
  
 `x:` Konwencji prefiks mapowanie obsługi wewnętrznych elementów języka XAML następuje szablonów projektu przykładowego kodu i dokumentacji języka funkcji w ramach tej [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Przestrzeń nazw XAML definiuje wiele najczęściej używanych funkcji, które są niezbędne, nawet w przypadku podstawowych aplikacji WPF. Na przykład, aby można było dołączyć wszelkie związane z kodem w pliku XAML, za pośrednictwem klasy częściowej, musisz nazwać tę klasę jako `x:Class` atrybutu w elemencie głównym odpowiedniego pliku XAML. Lub dowolnego elementu zgodnie z definicją w strony XAML, który uzyskiwany jest dostęp zgodnie z kluczem zasobu powinny mieć `x:Key` ustawić atrybutu w elemencie zagrożona. Aby uzyskać więcej informacji na temat tych i innych aspektów XAML, zobacz [Przegląd XAML (WPF)](xaml-overview-wpf.md) lub [składnia XAML w szczegółów](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapowanie niestandardowej klasy i zestawy  
 Obszary nazw XML można mapować do zestawów przy użyciu serii tokenów w ramach `xmlns` prefiksu deklaracji, podobnie jak standardowy WPF i XAML — funkcje wewnętrzne XAML przestrzenie nazw są mapowane na prefiksy.  
  
 Składnia przyjmuje następujące generatory kodów nazwane możliwe i następujące wartości:  
  
 `clr-namespace:` Przestrzeń nazw środowiska CLR są zadeklarowane w obrębie zestawu, który zawiera typy publiczne do udostępnienia jako elementy.  
  
 `assembly=` Zestaw, który zawiera niektóre lub wszystkie występujących w odwołaniu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] przestrzeni nazw. Ta wartość jest zazwyczaj tylko nazwę zestawu, a nie ścieżkę i nie zawiera rozszerzenia (na przykład .dll lub .exe). Ścieżka do tego zestawu, należy ustanowić jako odwołanie do projektu w pliku projektu, który zawiera XAML próbujesz mapy. Aby można było przechowywanie wersji i podpisu silnej nazwy, `assembly` wartość może być ciągiem, zgodnie z definicją <xref:System.Reflection.AssemblyName>, zamiast nazwy prostego ciągu.  
  
 Należy pamiętać, że znak, rozdzielając `clr-namespace` token od jego wartość to dwukropek (:) a znak, rozdzielając `assembly` token od jego wartość jest znak równości (=). Znak do użycia między tymi dwoma tokenami jest średnikami. Ponadto nie należy dołączać dowolny biały obszar gdziekolwiek w deklaracji.  
  
### <a name="a-basic-custom-mapping-example"></a>Przykład podstawowego mapowanie niestandardowego  
 Poniższy kod definiuje przykład klasy niestandardowej:  
  
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
  
 Ta klasa niestandardowa jest następnie kompilowane do biblioteki, który zgodnie z ustawieniami projektu (niewyświetlany) o nazwie `SDKSampleLibrary`.  
  
 Aby można było odwoływać się do tej klasy niestandardowej, należy również uwzględnić go jako odniesienie do bieżącego projektu, który zazwyczaj samo, jak za pomocą interfejsu użytkownika Eksploratora rozwiązań w programie Visual Studio.  
  
 Teraz, gdy biblioteka zawierająca klasę i odwołanie do niej w ustawieniach projektu, można dodać następujące mapowanie prefiksu w ramach elementu głównego w XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Aby przełączyć wszystko ze sobą, Oto XAML, który zawiera niestandardowe mapowanie wraz z typową domyślną i mapowania x: tag główny, a następnie używa prefiksem odwołania do utworzenia wystąpienia `ExampleClass` w tym interfejsie użytkownika:  
  
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
  
### <a name="mapping-to-current-assemblies"></a>Mapowanie aktualna liczba zestawów  
 `assembly` można pominąć, jeśli `clr-namespace` odwołania jest definiowany w obrębie tego samego zestawu jako kod aplikacji, który odwołuje się do niestandardowych klas. Lub równoważny składni w tym przypadku jest określenie `assembly=`, nie tokenem ciąg po znaku równości.  
  
 Nie można użyć niestandardowych klas jako element główny strony, jeśli zdefiniowany w tym samym zestawie. Klasy częściowe nie muszą być mapowane; tylko klasy, które nie są klasy częściowej strony w swoje wymagania aplikacji mają być mapowane, jeśli zamierzasz odwoływać się do nich jako elementy XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mapowanie przestrzeni nazw CLR do przestrzeni nazw XML w zestawie  
 WPF definiuje atrybut CLR, który jest używany przez procesory XAML w celu zamapowania wiele przestrzeni nazw CLR w jednej przestrzeni nazw XAML. Ten atrybut <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, jest umieszczany w kodzie źródłowym, który produkuje zestawu na poziomie zestawu. Kod źródłowy zestawu WPF korzysta z tego atrybutu do mapowania różnych popularnych przestrzeni nazw, takich jak <xref:System.Windows> i <xref:System.Windows.Controls>, [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] przestrzeni nazw.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> Przyjmuje dwa parametry: Nazwa przestrzeni nazw XML/XAML, a nazwa przestrzeni nazw CLR. Więcej niż jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> może istnieć w celu zamapowania wiele przestrzeni nazw CLR na tej samej przestrzeni nazw XML. Po mapowane, te obszary nazw elementów członkowskich mogą się też odwoływać bez pełnej kwalifikacji w razie potrzeby, podając odpowiednie `using` instrukcji na stronie częściowej klasy CodeBehind. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Przestrzenie nazw projektanta i innymi prefiksami za pomocą szablonów XAML  
 Jeśli pracujesz z środowisk deweloperskich i/lub narzędzi do projektowania dla WPF XAML, można zauważyć, że nie istnieją inne zdefiniowanych przestrzeni nazw XAML / prefiksy w ramach znaczników XAML.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] używa projektanta przestrzeni nazw, który zazwyczaj jest mapowany na prefiksie `d:`. Więcej ostatnie szablony projektu dla WPF wstępnie mogą być mapowane na tę przestrzeń nazw XAML w celu obsługi wymiany XAML między [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] i innych środowisk projektowych. Ta przestrzeń nazw XAML projektu jest używany do widoczny przy obsłudze często stanie projektu podczas roundtripping interfejsu użytkownika opartego na XAML w projektancie. Jest również używany do funkcji takich jak `d:IsDataSource`, umożliwiają one środowiska uruchomieniowego źródeł danych w projektancie.  
  
 Inny prefiks może zostać wyświetlony mapowane jest `mc:`. `mc:` dotyczy zgodność znaczników i polega na wykorzystaniu wzorca zgodność znaczników, który nie jest koniecznie specyficzne dla XAML. Do pewnego stopnia zgodności znaczników, funkcji może być używane do wymiany XAML między struktur lub innych granice wykonania zapasowy wykorzystują współdziałanie kontekst schematu XAML, zapewniają zgodność dla trybów ograniczone w projektantach i tak dalej. Aby uzyskać więcej informacji na temat pojęć zgodności znaczników i ich relacje z WPF, zobacz [zgodność znaczników (mc:) Funkcje języka](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>WPF i ładowania zestawu  
 Kontekst schematu WPF XAML integruje się z modelem aplikacji WPF, który z kolei używa zdefiniowane CLR koncepcji <xref:System.AppDomain>. Poniższa sekwencja opisuje, jak kontekst schematu XAML interpretuje jak ładować zestawy lub znaleźć typów w czasie wykonywania lub czasie projektowania na podstawie związane z użyciem WPF <xref:System.AppDomain> i inne czynniki.  
  
1. Iteracyjne przeglądanie <xref:System.AppDomain>, wyszukiwanie już załadowany zestaw, który dopasowuje wszystkie aspekty nazwę, od ostatniego załadowany zestaw.  
  
2. Jeśli nazwa jest kwalifikowana, wywołaj <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> kwalifikowanej nazwy.  
  
3. Jeśli krótką nazwę i token klucza publicznego kwalifikowana nazwa pasuje do zestawu, który znaczników został załadowany z, zwróć tego zestawu.  
  
4. Użyj krótkiej nazwy i token klucza publicznego do wywołania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5. Jeśli nazwa jest niekwalifikowana, wywołaj <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Luźne XAML nie korzysta z kroku 3; nie ma żadnego załadowane z zestawu.  
  
 Skompilowany XAML dla WPF (generowany za pośrednictwem XamlBuildTask) nie używa zestawów już załadowany z <xref:System.AppDomain> (krok 1). Ponadto nazwę nigdy nie należy niekwalifikowanej z danych wyjściowych XamlBuildTask, więc nie ma zastosowania kroku 5.  
  
 Skompilowanych BAML (generowany za pośrednictwem PresentationBuildTask) używa wszystkich kroków, mimo że BAML także nie może zawierać nazwy niekwalifikowanej zestawów.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje o przestrzeni nazw XML](https://go.microsoft.com/fwlink/?LinkId=98069)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
