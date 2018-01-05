---
title: "x:Static — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticExtension
- xStatic
- x:Static
helpviewer_keywords:
- x:Static markup extension [XAML Services]
- Static markup extension in XAML [XAML Services]
- XAML [XAML Services], x:Static markup extension
ms.assetid: 056aee79-7cdd-434f-8174-dfc856cad343
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 647bfed7b321a949090f6da047f9b8105d335101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="xstatic-markup-extension"></a>x:Static — Rozszerzenie znaczników
Odwołuje się do dowolnej jednostki kodu przez wartość statyczną, która jest zdefiniowana w [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]— sposób zgodne. Właściwość statyczna, do którego odwołuje się może służyć do zapewnienia wartości właściwości w języku XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Static prefix:typeName.staticMemberName}" .../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`prefix`|Opcjonalny. Prefiks, który odwołuje się do mapowanej, innej niż domyślna przestrzeń nazw XAML. `prefix`pokazano jawnie użycia, ponieważ odwołuje się rzadko statycznej właściwości, które pochodzą z domyślnej przestrzeni nazw XAML. Zobacz uwagi.|  
|`typeName`|Wymagany. Nazwa typu, który definiuje żądany statycznego elementu członkowskiego.|  
|`staticMemberName`|Wymagany. Nazwa elementu członkowskiego żądaną wartość statyczną (stałą, właściwość statyczna, pole lub wartością wyliczenia).|  
  
## <a name="remarks"></a>Uwagi  
 Jednostek kodu, do którego odwołuje się musi być jedną z następujących czynności:  
  
-   Stała  
  
-   Właściwość statyczna  
  
-   Pola  
  
-   Wartość wyliczenia  
  
 Określenie żadnych innych jednostek kodu, takie jak niestatycznej właściwości, powoduje błąd kompilacji, jeśli XAML jest kompilacji znaczników lub wyjątek analizy czas ładowania XAML.  
  
 Możesz wprowadzić `x:Static` odwołania do statycznego pola lub właściwości, które nie znajdują się w domyślnej przestrzeni nazw XAML dla bieżącego dokumentu XAML; jednak wymaga to mapowanie prefiksu. Przestrzeń nazw XAML prawie zawsze są definiowane dla elementu głównego dokumentu XAML.  
  
 Operacje wyszukiwania dla właściwości statyczne może zostać przeprowadzone przez usług .NET Framework XAML i czytników XAML i zapisywania XAML działają domyślny kontekst schematu XAML. Ten kontekst schematu XAML służy odbicia CLR do zapewnienia niezbędnych wartości statyczne Tworzenie wykresu obiektu. `typeName` Określ jest rzeczywiście XAML nazwę typu, nie nazwę typu CLR, chociaż są zasadniczo taką samą nazwę, używając domyślny kontekst schematu XAML lub w przypadku używania wszystkich istniejących struktur opartych na CLR XAML — wdrażanie.  
  
 Należy zachować ostrożność podczas wprowadzania `x:Static` odwołań, które nie są bezpośrednio typ wartości właściwości. W kodzie XAML przetwarzania udostępnia wartości z rozszerzeniem znacznika sekwencji nie wywołuj konwersja dodatkowe wartości. Dotyczy to nawet wtedy, gdy Twoje `x:Static` odwołanie tworzy ciąg tekstowy, a konwersja wartości dla wartości atrybutu oparte na ciąg tekstowy zwykle odbywa się dla tego określonego elementu członkowskiego lub dla każdej wartości elementu członkowskiego typu zwracanego.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu po `x:Static` przypisany jako identyfikator ciągu <xref:System.Windows.Markup.StaticExtension.Member%2A> wartości podstawowych <xref:System.Windows.Markup.StaticExtension> rozszerzenie klasy.  
  
 Istnieją dwa inne użycia XAML, które są często technicznie możliwa. Jednak te użycia są mniej typowe, ponieważ są one niepotrzebnie pełne:  
  
 **Obiekt składni elementu:** `<x:Static Member="` `prefix` `:` `typeName` `.` `staticMemberName``" .../>`  
  
 **Atrybut składni jawną właściwość elementu członkowskiego dla ciągu inicjującego:** `<` `object`  ``  `property` `="{x:Static Member=` `prefix` `:` `typeName` `.` `staticMemberName``}" .../>`  
  
 W implementacji usług .NET Framework XAML obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.StaticExtension> klasy.  
  
 `x:Static`to rozszerzenie znacznika. Wszystkie rozszerzenia znaczników w XAML, użyj `{` i `}` znaków w ich składni atrybutu Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znaczników należy podać wartość. Aby uzyskać więcej informacji na temat rozszerzeń znaczników, zobacz [rozszerzenia znaczników dla przeglądu XAML](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Domyślna przestrzeń nazw XAML, użyj programowania WPF nie zawiera wiele przydatnych właściwości statycznej, a najbardziej przydatne właściwości statyczne obsługuje takie jak konwertery typu, które ułatwiają bez konieczności użycia `{x:Static}` . W przypadku statycznej właściwości należy zamapować prefiksu dla przestrzeni nazw XAML po spełnieniu jednego z następujących warunków:  
  
-   Odwołanie do typu, który istnieje w WPF, ale nie jest częścią domyślnej przestrzeni nazw XAML WPF ([!INCLUDE[TLA#tla_wpfxmlnsv1](../../../includes/tlasharptla-wpfxmlnsv1-md.md)]). To jest dość typowy scenariusz dla przy użyciu `x:Static`. Na przykład może użyć `x:Static` odwołanie z mapowania przestrzeni nazw XAML, aby <xref:System> przestrzeni nazw i mscorlib Zestaw CLR aby odwołanie statycznej właściwości <xref:System.Environment> klasy.  
  
-   Z niestandardowego zestawu odwołuje się do typu.  
  
-   Odwołujesz się do typu, który istnieje w zestawie WPF, ale ten typ znajduje się w przestrzeni nazw CLR, który nie został zmapowany jako część domyślnej WPF XAML przestrzeni nazw. Mapowanie przestrzeni nazw CLR w domyślnej przestrzeni nazw XAML dla WPF jest wykonywane przez definicje w różnych zestawach WPF (Aby uzyskać więcej informacji dotyczących tej reguły, zobacz [przestrzeń nazw XAML i Namespace mapowanie dla WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)). Mapowane bez nazw CLR może istnieć, jeśli tej przestrzeni nazw CLR składa się przede wszystkim z definicje klas, które nie są zwykle przeznaczone dla XAML, takich jak <xref:System.Windows.Threading>.  
  
 Aby uzyskać więcej informacji na temat korzystania z prefiksami i przestrzeni nazw XAML dla WPF, zobacz [przestrzeń nazw XAML i Namespace mapowanie WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
## <a name="see-also"></a>Zobacz też  
 [x:Type, rozszerzenie znaczników](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [Typy migrowane z WPF do System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
