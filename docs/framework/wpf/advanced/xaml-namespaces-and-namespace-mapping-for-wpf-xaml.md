---
title: XAML Obszary nazw i Mapowanie obszaru nazw
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
ms.openlocfilehash: 9b01643e8f8d77073595253580ebea60fabfd23b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186233"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML
W tym temacie wyjaśniono obecność i cel dwóch mapowań przestrzeni nazw XAML, jak często znajduje się w tagu głównym pliku WPF XAML. Opisano również, jak utworzyć podobne mapowania dla przy użyciu elementów, które są zdefiniowane w kodzie własnym i/lub w oddzielnych zestawów.  

## <a name="what-is-a-xaml-namespace"></a>Co to jest obszar nazw XAML?  
 Obszar nazw XAML jest naprawdę rozszerzenie koncepcji przestrzeni nazw XML. Techniki określania przestrzeni nazw XAML opierają się na składni obszaru nazw XML, konwencji używania identyfikatorów URI jako identyfikatorów obszaru nazw, przy użyciu prefiksów w celu zapewnienia możliwości odwoływania się do wielu obszarów nazw z tego samego źródła znaczników itd. Podstawową koncepcją dodaną do definicji XAML obszaru nazw XML jest to, że obszar nazw XAML oznacza zarówno zakres unikatowości dla użycia znaczników, jak i wpływa na sposób, w jaki jednostki znaczników są potencjalnie wspierane przez określone przestrzenie nazw CLR i odwołują się do nich, a także Zestawów. Na tę ostatnią uwagę ma również wpływ pojęcie kontekstu schematu XAML. Jednak na potrzeby działania WPF w obszarze nazw XAML można ogólnie myśleć o przestrzeniach nazw XAML w kontekście domyślnej przestrzeni nazw XAML, przestrzeni nazw języka XAML i wszelkich innych obszarów nazw XAML mapowanych przez znaczniki XAML bezpośrednio do określonego kopii CLR przestrzenie nazw i zestawy, do których się odwołuje.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>Deklaracje obszaru nazw WPF i XAML  
 W deklaracjach obszaru nazw w tagu głównym wielu plików XAML zobaczysz, że zazwyczaj istnieją dwie deklaracje obszaru nazw XML. Pierwsza deklaracja mapuje ogólny obszar nazw XAML klienta WPF / frameworka jako domyślny:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druga deklaracja mapuje oddzielny obszar nazw XAML, mapując go (zazwyczaj) do prefiksu. `x:`  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Relacja między tymi deklaracjami `x:` jest, że mapowanie prefiks obsługuje wewnętrzne, które są częścią [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definicji języka XAML i jest jedną implementację, która używa XAML jako języka i definiuje słownictwo jego obiektów dla XAML. Ponieważ użycie słownictwa WPF będzie znacznie bardziej powszechne niż użycie wewnętrznego XAML, słownictwa WPF jest mapowane jako domyślne.  
  
 Konwencja `x:` prefiksu do mapowania obsługi wewnętrznego języka XAML następuje szablony projektu, przykładowy kod i dokumentacja funkcji języka w tym zestawie SDK. Obszar nazw XAML definiuje wiele często używanych funkcji, które są niezbędne nawet dla podstawowych aplikacji WPF. Na przykład, aby dołączyć do dowolnego kodu do pliku XAML za pośrednictwem klasy `x:Class` częściowej, należy nazwać tę klasę jako atrybut w elemencie głównym odpowiedniego pliku XAML. Lub dowolny element zdefiniowany na stronie XAML, który chcesz uzyskać dostęp `x:Key` jako zasób z kluczem powinien mieć atrybut ustawiony na danym elemencie. Aby uzyskać więcej informacji na temat tych i innych aspektów XAML zobacz [Omówienie XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) lub [Składnia XAML w szczegółach](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapowanie do niestandardowych klas i zestawów  
 Obszary nazw XML można mapować do zestawów przy `xmlns` użyciu serii tokenów w deklaracji prefiksu, podobnie jak standardowe przestrzenie nazw XAML w warstwie WPF i XAML są mapowane na prefiksy.  
  
 Składnia przyjmuje następujące możliwe nazwane tokeny i następujące wartości:  
  
 `clr-namespace:`Obszar nazw CLR zadeklarowany w zestawie, który zawiera typy publiczne, aby udostępnić jako elementy.  
  
 `assembly=`Zestaw, który zawiera niektóre lub wszystkie obszaru nazw CLR, do którego istnieje odwołanie. Ta wartość jest zazwyczaj tylko nazwa zestawu, a nie ścieżka i nie zawiera rozszerzenia (takich jak .dll lub .exe). Ścieżka do tego zestawu musi być ustanowiona jako odwołanie do projektu w pliku projektu, który zawiera XAML, który próbujesz mapować. Aby włączyć przechowywanie wersji i podpisywanie `assembly` silnej nazwy, wartość <xref:System.Reflection.AssemblyName>może być ciągiem zdefiniowanym przez program , a nie prostą nazwą ciągu.  
  
 Należy zauważyć, że `clr-namespace` znak oddzielający token od jego wartości jest dwukropkiem (:) mając na uwadze, `assembly` że znak oddzielający token od jego wartości jest znakiem równości (=). Znak do użycia między tymi dwoma tokenami jest średnikiem. Ponadto nie należy dołączać żadnych białych spacji w dowolnym miejscu w deklaracji.  
  
### <a name="a-basic-custom-mapping-example"></a>Przykład podstawowego mapowania niestandardowego  
 Poniższy kod definiuje przykładową klasę niestandardową:  
  
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
  
 Ta klasa niestandardowa jest następnie kompilowana do biblioteki, która `SDKSampleLibrary`zgodnie z ustawieniami projektu (nie pokazano) nosi nazwę .  
  
 Aby odwołać się do tej klasy niestandardowej, należy również dołączyć go jako odwołanie do bieżącego projektu, które zazwyczaj można zrobić przy użyciu interfejsu użytkownika Eksploratora rozwiązania w programie Visual Studio.  
  
 Teraz, gdy masz bibliotekę zawierającą klasę i odwołanie do niej w ustawieniach projektu, możesz dodać następujące mapowanie prefiksów jako część elementu głównego w języku XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Aby umieścić to wszystko razem, poniżej znajduje się XAML, który zawiera mapowanie niestandardowe wraz z typowych mapowań domyślnych i x: w tagu głównym, a następnie używa prefixed odwołanie do wystąpienia w tym interfejsie `ExampleClass` użytkownika:  
  
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
  
### <a name="mapping-to-current-assemblies"></a>Mapowanie do bieżących zestawów  
 `assembly`można pominąć, `clr-namespace` jeśli odwołuje się jest zdefiniowany w tym samym zestawie jako kod aplikacji, który odwołuje się do klas niestandardowych. Lub równoważną składnią dla tego `assembly=`przypadku jest określenie , bez tokenu ciągu po znaku równości.  
  
 Klasy niestandardowe nie mogą być używane jako element główny strony, jeśli są zdefiniowane w tym samym zestawie. Klasy częściowe nie muszą być mapowane; tylko klasy, które nie są częściową klasą strony w aplikacji, muszą być mapowane, jeśli zamierzasz odwoływać się do nich jako elementów w języku XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mapowanie obszarów nazw PROGRAMU CLR na obszary nazw XML w zestawie  
 WPF WPF definiuje atrybut CLR, który jest zużywany przez procesory XAML w celu mapowania wielu obszarów nazw CLR do jednego obszaru nazw XAML. Ten atrybut <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, jest umieszczany na poziomie zestawu w kodzie źródłowym, który tworzy zestaw. Kod źródłowy zestawu WPF używa tego atrybutu do mapowania <xref:System.Windows> różnych <xref:System.Windows.Controls>wspólnych `http://schemas.microsoft.com/winfx/2006/xaml/presentation` obszarów nazw, takich jak i , do obszaru nazw.  
  
 Przyjmuje <xref:System.Windows.Markup.XmlnsDefinitionAttribute> dwa parametry: nazwę obszaru nazw XML/XAML i nazwę obszaru nazw CLR. Więcej niż <xref:System.Windows.Markup.XmlnsDefinitionAttribute> jeden może istnieć do mapowania wielu obszarów nazw CLR do tego samego obszaru nazw XML. Po zamapowania członków tych obszarów nazw można również odwoływać się `using` bez pełnej kwalifikacji w razie potrzeby, zapewniając odpowiednią instrukcję na stronie częściowej klasy zakodowane. Aby uzyskać więcej <xref:System.Windows.Markup.XmlnsDefinitionAttribute>informacji, zobacz .  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Designerskie przestrzenie nazw i inne prefiksy z szablonów XAML  
 Jeśli pracujesz ze środowiskami programistycznymi i/lub narzędziami do projektowania dla WPF XAML, można zauważyć, że istnieją inne zdefiniowane przestrzenie nazw XAML / prefiksy w znacznikach XAML.  
  
 WPF Designer for Visual Studio używa projektanta obszaru nazw, który `d:`jest zazwyczaj mapowane do prefiksu. Nowsze szablony projektów dla WPF może wstępnie mapować ten obszar nazw XAML do obsługi wymiany XAML między WPF Designer dla programu Visual Studio i innych środowisk projektowych. Ten projekt XAML przestrzeni nazw jest używany do utrwalania stanu projektu podczas zaokrąglania XAML oparte na interfejsie użytkownika w projektancie. Jest również używany dla `d:IsDataSource`funkcji, takich jak , które umożliwiają źródła danych środowiska wykonawczego w projektancie.  
  
 Innym prefiksem, który `mc:`może być zamapowany, jest . `mc:`jest dla zgodności znaczników i wykorzystuje wzorzec zgodności znaczników, który niekoniecznie jest specyficzny dla XAML. Do pewnego stopnia funkcje zgodności znaczników mogą służyć do wymiany XAML między strukturami lub w innych granicach implementacji kopii zapasowej, pracy między kontekstami schematu XAML, zapewnienia zgodności dla ograniczonych trybów w projektantów i tak dalej. Aby uzyskać więcej informacji na temat pojęć zgodności znaczników i ich relacji z filtrem WPF, zobacz [Zgodność z znacznikami (mc:) Funkcje językowe](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>Obciążenie WPF i zespołu  
 Kontekst schematu XAML dla WPF integruje się z modelem aplikacji WPF, <xref:System.AppDomain>który z kolei używa pojęcia zdefiniowanego przez CLR . W poniższej sekwencji opisano, jak kontekst schematu XAML interpretuje sposób ładowania zestawów lub znajdowania <xref:System.AppDomain> typów w czasie wykonywania lub czasie projektowania, na podstawie użycia WPF i innych czynników.  
  
1. Iteracji przez <xref:System.AppDomain>, szukając już załadowany zestaw, który pasuje do wszystkich aspektów nazwy, począwszy od ostatnio załadowanyzesoń.  
  
2. Jeśli nazwa jest kwalifikowana, zadzwoń <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na nazwę kwalifikowaną.  
  
3. Jeśli skrócona nazwa + token klucza publicznego nazwy kwalifikowanej pasuje do zestawu, z których został załadowany znacznik, zwróć ten zestaw.  
  
4. Użyj krótkiej nazwy + tokenu klucza publicznego, aby wywołać <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5. Jeśli nazwa nie jest zastrzeżeń, zadzwoń <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Luźny XAML nie używa kroku 3; nie ma załadowanego zestawu.  
  
 Skompilowany kod XAML dla WPF (generowany przez XamlBuildTask) <xref:System.AppDomain> nie używa już załadowanych zestawów z (Krok 1). Ponadto nazwa nigdy nie powinna być niezakwalifikowana z danych wyjściowych XamlBuildTask, więc krok 5 nie ma zastosowania.  
  
 Skompilowany BAML (generowany za pośrednictwem PresentationBuildTask) używa wszystkich kroków, chociaż BAML również nie powinien zawierać niekwalifikowanych nazw zestawów.  
  
## <a name="see-also"></a>Zobacz też

- [Opis obszarów nazw XML](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
