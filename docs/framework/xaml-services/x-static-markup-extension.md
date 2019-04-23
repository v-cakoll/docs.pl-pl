---
title: x:Static — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
ms.openlocfilehash: 3da2f6afc7e7ecf20c91f0badca38bc26083d3ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295713"
---
# <a name="xstatic-markup-extension"></a>x:Static — Rozszerzenie znaczników
Odwołuje się do dowolnej jednostki kodu przez wartość statyczną, która jest zdefiniowana w [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]— sposób zgodne. Właściwość statyczna, do którego istnieje odwołanie może służyć do zapewnienia wartości właściwości w XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
| | |  
|-|-|  
|`prefix`|Opcjonalna. Prefiks, który odwołuje się do przestrzeni nazw XAML zamapowany, innych niż domyślne. `prefix` przedstawiono jawnie na użycie ponieważ właściwości statyczne, które pochodzą z domyślną przestrzeń nazw XAML odwołujesz się rzadko. Zobacz uwagi.|  
|`typeName`|Wymagana. Nazwa typu, który definiuje żądany statyczny element członkowski.|  
|`staticMemberName`|Wymagana. Nazwa elementu członkowskiego żądaną wartość statyczną (stałą, statycznej właściwości, pola lub wartości wyliczenia).|  
  
## <a name="remarks"></a>Uwagi  

Jednostki kodu, do którego odwołuje się musi mieć jedną z następujących czynności:  
  
-   — Stała  
-   Właściwość statyczna  
-   Pola  
-   Wartość wyliczenia

Określanie innej jednostki kodu, takich jak niestatycznej właściwości powoduje błąd w czasie kompilacji, jeśli XAML jest skompilowany kod znaczników lub wyjątek analizy w czasie ładowania XAML.  

Możesz wprowadzić `x:Static` odwołania do statycznego pola lub właściwości, które nie znajdują się w domyślnej przestrzeni nazw XAML dla bieżącego dokumentu XAML; jednak wymaga to mapowanie prefiksu. Przestrzenie nazw XAML prawie zawsze są definiowane w elemencie głównym dokumentu XAML.  

Można wykonać operacji wyszukiwania dla właściwości statyczne przez usług programu .NET Framework XAML i XAML czytniki i moduły zapisujące XAML, uruchamianego z domyślny kontekst schematu XAML. Ten kontekst schematu XAML umożliwia artości niezbędne statyczne konstruowania wykresu obiektu CLR odbicia. `typeName` Określ jest faktycznie XAML nazwę typu, nie nazwę typu CLR, mimo że są zasadniczo taką samą nazwę, korzystając z domyślny kontekst schematu XAML lub w przypadku używania wszystkich istniejących środowisk opartych na CLR XAML — Implementowanie.  

Należy zachować ostrożność podczas wprowadzania `x:Static` odwołań, które nie są bezpośrednio typ wartości właściwości. W XAML przetwarzania sekwencji, podane wartości z rozszerzeniem znacznika nie wywołać konwersja dodatkowe wartości. Ta zasada obowiązuje nawet wtedy, gdy Twoje `x:Static` odwołanie tworzy ciąg tekstowy i konwersji wartości dla wartości atrybutów oparte na ciąg tekstowy zazwyczaj występuje dla tego określonego członka lub dowolnej wartości elementów członkowskich typu zwracanego.  

Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podawany po `x:Static` ciągu identyfikatora jest przypisany jako <xref:System.Windows.Markup.StaticExtension.Member%2A> wartości elementu bazowego <xref:System.Windows.Markup.StaticExtension> rozszerzenie klasy.  

Istnieją dwa inne zastosowania XAML, które są technicznie możliwa. Jednak te zastosowania są mniej typowe, ponieważ są one niepotrzebne powielenie informacji:  

1. Składnia elementu obiektu.

    ```xaml
    <x:Static Member="prefix:typeName.staticMemberName" ... />
    ```

2. Atrybut składni z jawną właściwością elementu członkowskiego dla ciągu inicjującego.

    ```xaml
    <object property="{x:Static Member=prefix:typeName.staticMemberName}" ... />
    ```

W implementacji .NET Framework XAML Services obsługi dla tego rozszerzenia znacznika jest definiowany przez <xref:System.Windows.Markup.StaticExtension> klasy.  

`x:Static` jest rozszerzeniem znacznika. Wszystkie rozszerzenia znaczników w XAML użyj `{` i `}` znaków w składni swoich atrybutów, które jest do Konwencja, za pomocą którego procesor XAML rozpoznaje, że rozszerzenie znaczników należy podać wartość. Aby uzyskać więcej informacji na temat rozszerzenia znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 Domyślna przestrzeń nazw XAML, użyj dla programowania WPF nie zawiera wiele użytecznych właściwości statycznej, a większość użytecznych właściwości statycznej obsługuje takie jak konwerterów typów, które ułatwiają użycie bez konieczności `{x:Static}` . W przypadku statycznej właściwości możesz zamapować prefiksu dla przestrzeni nazw XAML, jeśli jest spełniony jeden z następujących czynności:  
  
-   Utworzono odwołanie do typu, który istnieje w WPF, ale nie jest częścią domyślnej przestrzeni nazw XAML dla WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). Jest to dość typowy scenariusz używania `x:Static`. Na przykład, można na przykład `x:Static` odwołania za pomocą mapowania przestrzeni nazw XAML, aby <xref:System> zestaw przestrzeni nazw i mscorlib CLR aby odwołanie statyczne właściwości <xref:System.Environment> klasy.  
  
-   Z niestandardowego zestawu odwołuje się do typu.  
  
-   Utworzono odwołanie do typu, który istnieje w zestawie WPF, jednak, że typ znajduje się w przestrzeni nazw CLR, który nie został zmapowany jako część domyślnej WPF XAML przestrzeni nazw. Mapowanie przestrzeni nazw CLR do domyślnej przestrzeni nazw XAML dla WPF odbywa się przez definicje w różnych zestawach WPF (Aby uzyskać więcej informacji dotyczących tej reguły, zobacz [przestrzeń nazw XAML i mapowanie Namespace dla WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Zamapowane bez przestrzeni nazw CLR może istnieć, jeśli przestrzeń nazw CLR składa się głównie z definicji klas, które nie są zwykle przeznaczone dla XAML, takich jak <xref:System.Windows.Threading>.  
  
 Aby uzyskać więcej informacji na temat korzystania z prefiksy i XAML w przestrzeni nazw dla WPF, zobacz [przestrzeni nazw XAML i Namespace mapowania dla WPF XAML](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz także

- [x:Type, rozszerzenie znaczników](x-type-markup-extension.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
