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
ms.openlocfilehash: 6c06e18f7869f1b1041c4d5fb1608a87f2902d7b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460574"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>Przestrzeń nazw XAML i mapowanie przestrzeni nazw dla WPF XAML
W tym temacie wyjaśniono również obecność i cel dwóch mapowań przestrzeni nazw XAML, jak często znajdują się w tagu głównym pliku XAML WPF. Opisano w nim również, jak generować podobne mapowania dla elementów, które są zdefiniowane w własnym kodzie i/lub w różnych zestawach.  

## <a name="what-is-a-xaml-namespace"></a>Co to jest przestrzeń nazw XAML?  
 Przestrzeń nazw XAML jest w rzeczywistości rozszerzeniem koncepcji przestrzeni nazw XML. Techniki określania przestrzeni nazw XAML opierają się na składni przestrzeni nazw XML, Konwencji o użyciu identyfikatorów URI jako identyfikatorów przestrzeni nazw, przy użyciu prefiksów, aby umożliwić odwoływanie się do wielu przestrzeni nazw z tego samego źródła znaczników i tak dalej. Koncepcja podstawowa dodawana do definicji XAML przestrzeni nazw XML polega na tym, że przestrzeń nazw XAML oznacza zarówno zakres unikatowości użycia znaczników, jak i wpływa na sposób, w jaki jednostki znaczników są potencjalnie obsługiwane przez określone przestrzenie nazw CLR i przywoływane zestawów. Ten ostatni nacisk ma wpływ na koncepcję kontekstu schematu XAML. Ale w celach, w których WPF współpracuje z przestrzeniami nazw XAML, można ogólnie traktować przestrzenie nazw XAML pod względem domyślnej przestrzeni nazw XAML, przestrzeni nazw języka XAML oraz wszelkich innych przestrzeni nazw XAML, które są mapowane przez znaczniki XAML bezpośrednio do określonego środowiska CLR przestrzenie nazw i zestawy, do których istnieją odwołania.  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>Deklaracje przestrzeni nazw WPF i XAML  
 W deklaracjach przestrzeni nazw w tagu głównym wielu plików XAML zobaczysz, że istnieją zwykle dwie deklaracje przestrzeni nazw XML. Pierwsza deklaracja mapuje ogólnie przestrzeń nazw XAML klienta/platformy WPF jako domyślną:  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 Druga deklaracja mapuje oddzielną przestrzeń nazw XAML, mapując ją (zazwyczaj) na prefiks `x:`.  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 Relacja między tymi deklaracjami polega na tym, że mapowanie prefiksu `x:` obsługuje elementy wewnętrzne, które są częścią definicji języka XAML, a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to jedna implementacja, która używa języka XAML jako język i definiuje słownictwe obiektów dla języka XAML. Ze względu na to, że użycie słownictwa WPF będzie znacznie bardziej typowe niż użycie elementów wewnętrznych języka XAML, słownictwo WPF jest mapowane jako domyślne.  
  
 Konwencja prefiksu `x:` na potrzeby mapowania obsługi elementów wewnętrznych języka XAML jest przystosowana do szablonów projektu, przykładowego kodu i dokumentacji funkcji języka w tym [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]. Przestrzeń nazw XAML definiuje wiele powszechnie używanych funkcji, które są niezbędne nawet dla podstawowych aplikacji WPF. Na przykład w celu dołączenia dowolnego kodu do pliku XAML za pomocą klasy częściowej należy nazwać tę klasę jako atrybut `x:Class` w elemencie głównym odpowiedniego pliku XAML. Lub każdy element zdefiniowany na stronie XAML, do którego chcesz uzyskać dostęp jako zasób z kluczem, powinien mieć ustawiony atrybut `x:Key` dla danego elementu. Aby uzyskać więcej informacji na temat tych i innych aspektów języka XAML, zobacz [Omówienie języka XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) lub [składni języka XAML](xaml-syntax-in-detail.md).  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>Mapowanie na klasy niestandardowe i zestawy  
 Można mapować przestrzenie nazw XML na zestawy przy użyciu serii tokenów w deklaracji prefiksu `xmlns`, podobnie jak standardowe przestrzenie nazw WPF i XAML — elementy wewnętrzne języka XAML są mapowane na prefiksy.  
  
 Składnia przyjmuje następujące możliwe nazwane tokeny i następujące wartości:  
  
 `clr-namespace:` przestrzeń nazw środowiska CLR zadeklarowaną w zestawie, która zawiera typy publiczne do uwidocznienia jako elementy.  
  
 `assembly=` zestawu, który zawiera część lub całą przestrzeń nazw CLR, do której istnieje odwołanie. Ta wartość jest zazwyczaj tylko nazwą zestawu, a nie ścieżką i nie zawiera rozszerzenia (na przykład. dll lub. exe). Ścieżka do tego zestawu musi być ustanowiona jako odwołanie do projektu w pliku projektu, który zawiera kod XAML, który próbujesz zmapować. Aby włączyć przechowywanie wersji i podpisywanie silnej nazwy, wartość `assembly` może być ciągiem zdefiniowanym przez <xref:System.Reflection.AssemblyName>, a nie prostą nazwą ciągu.  
  
 Należy zauważyć, że znak oddzielający token `clr-namespace` od jego wartości jest dwukropek (:) natomiast znak oddzielający token `assembly` od jego wartości jest znakiem równości (=). Znak, który ma być używany między tymi dwoma tokenami, jest średnikiem. Ponadto nie należy umieszczać żadnych białych znaków w dowolnym miejscu w deklaracji.  
  
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
  
 Ta klasa niestandardowa jest następnie skompilowana do biblioteki, która na ustawienia projektu (niepokazywany) nosi nazwę `SDKSampleLibrary`.  
  
 Aby można było odwołać się do tej klasy niestandardowej, należy również uwzględnić ją jako odwołanie do bieżącego projektu, które zwykle można używać Eksplorator rozwiązań interfejsu użytkownika w programie Visual Studio.  
  
 Teraz, gdy masz bibliotekę zawierającą klasę i odwołanie do niej w ustawieniach projektu, możesz dodać następujące mapowanie prefiksu jako część elementu głównego w języku XAML:  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 Aby wszystkie te elementy umieścić razem, poniżej znajduje się kod XAML, który zawiera niestandardowe mapowanie wraz z typowymi domyślnymi i x: mapowaniami w tagu głównym, a następnie używa prefiksu przedrostka do tworzenia wystąpienia `ExampleClass` w tym interfejsie użytkownika:  
  
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
  
### <a name="mapping-to-current-assemblies"></a>Mapowanie na bieżące zestawy  
 `assembly` można pominąć, jeśli odwołanie do `clr-namespace` jest zdefiniowane w tym samym zestawie, co kod aplikacji, który odwołuje się do klas niestandardowych. Lub równoważną składnią w tym przypadku jest określenie `assembly=`, bez tokenu ciągu po znaku równości.  
  
 Klas niestandardowych nie można używać jako elementu głównego strony, jeśli są zdefiniowane w tym samym zestawie. Klasy częściowe nie muszą być mapowane; tylko klasy, które nie są częściową klasą strony w aplikacji, muszą być mapowane, jeśli zamierza się odwoływać do nich jako elementy w języku XAML.  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>Mapowanie przestrzeni nazw CLR na przestrzenie nazw XML w zestawie  
 WPF definiuje atrybut CLR, który jest używany przez procesory XAML w celu mapowania wielu przestrzeni nazw CLR na pojedynczą przestrzeń nazw XAML. Ten atrybut, <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, jest umieszczany na poziomie zestawu w kodzie źródłowym, który tworzy zestaw. Kod źródłowy zestawu WPF używa tego atrybutu do mapowania różnych wspólnych przestrzeni nazw, takich jak <xref:System.Windows> i <xref:System.Windows.Controls>, do przestrzeni nazw [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)].  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> przyjmuje dwa parametry: nazwa przestrzeni nazw XML/XAML i nazwa przestrzeni nazw środowiska CLR. Może istnieć więcej niż jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute>, aby zmapować wiele przestrzeni nazw środowiska CLR do tego samego obszaru nazw XML. Po zmapowaniu, w razie potrzeby można odwoływać się do członków tych przestrzeni nazw bez pełnej kwalifikacji, dostarczając odpowiednią instrukcję `using`ową na stronie kodowej powiązanej z kodem częściowym. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>Obszary nazw projektanta i inne prefiksy z szablonów XAML  
 Jeśli pracujesz ze środowiskami deweloperskimi i/lub narzędziami do projektowania dla języka XAML WPF, możesz zauważyć, że istnieją inne zdefiniowane przestrzenie nazw XAML/prefiksy w znaczniku XAML.  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] używa przestrzeni nazw projektanta, która jest zwykle mapowana na prefiks `d:`. Nowsze szablony projektów dla WPF mogą wstępnie zmapować tę przestrzeń nazw XAML, aby obsługiwać wymianę kodu XAML między [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] i innymi środowiskami projektowymi. Ta przestrzeń nazw XAML projektowania jest używana do perpetuate stanu projektu, podczas gdy roundtripping interfejs użytkownika oparty na języku XAML w projektancie. Jest on również używany w przypadku funkcji, takich jak `d:IsDataSource`, które umożliwiają tworzenie źródeł danych środowiska uruchomieniowego w projektancie.  
  
 Mapowanym innym prefiksem może być `mc:`. `mc:` jest zgodna ze zgodnością znaczników i korzysta ze wzorca zgodności znaczników, który nie musi być specyficzny dla języka XAML. W pewnym zakresie funkcje zgodności znaczników mogą służyć do wymiany kodu XAML między platformami lub między innymi granicami implementacji tworzenia kopii zapasowych, pracy między kontekstami schematu XAML, zapewnienia zgodności z ograniczonymi trybami w projektantach i tak dalej. Aby uzyskać więcej informacji o pojęciach dotyczących zgodności znaczników i sposobie ich powiązania z programem WPF, zobacz [zgodność znaczników (MC:) Funkcje językowe](markup-compatibility-mc-language-features.md).  
  
## <a name="wpf-and-assembly-loading"></a>Ładowanie WPF i zestawu  
 Kontekst schematu XAML dla WPF integruje się z modelem aplikacji WPF, który z kolei używa koncepcji zdefiniowanej przez środowisko CLR <xref:System.AppDomain>. Poniższa sekwencja opisuje sposób, w jaki kontekst schematu XAML interpretuje sposób ładowania zestawów lub znajdowania typów w czasie wykonywania lub projektowania, na podstawie użycia platformy WPF <xref:System.AppDomain> i innych czynników.  
  
1. Wykonaj iterację <xref:System.AppDomain>, szukając już załadowanego zestawu, który pasuje do wszystkich aspektów nazwy, rozpoczynając od ostatnio załadowanego zestawu.  
  
2. Jeśli nazwa jest kwalifikowana, wywołaj <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> na kwalifikowanej nazwie.  
  
3. Jeśli krótka nazwa i token klucza publicznego kwalifikowanej nazwy są zgodne z zestawem, z którego został załadowany znacznik, zwróć ten zestaw.  
  
4. Użyj krótkiej nazwy i tokenu klucza publicznego do wywoływania <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>.  
  
5. Jeśli nazwa jest niekwalifikowana, wywołaj <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>.  
  
 Luźny kod XAML nie używa kroku 3; Brak załadowanego zestawu.  
  
 Skompilowany kod XAML dla WPF (wygenerowany za pośrednictwem XamlBuildTask) nie używa już załadowanych zestawów z <xref:System.AppDomain> (krok 1). Ponadto nazwa nigdy nie powinna być niekwalifikowana z danych wyjściowych XamlBuildTask, więc krok 5 nie ma zastosowania.  
  
 Skompilowana BAML (wygenerowana za pośrednictwem PresentationBuildTask) używa wszystkich kroków, chociaż BAML nie powinna również zawierać niekwalifikowanych nazw zestawów.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje o przestrzeniach nazw XML](https://go.microsoft.com/fwlink/?LinkId=98069)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
