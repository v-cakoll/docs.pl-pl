---
title: x:Type — Rozszerzenie znaczników
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: e4d56c5b5deda0bd1df8827020e0b76cc6276c1c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560940"
---
# <a name="xtype-markup-extension"></a>x:Type — Rozszerzenie znaczników
Dostarcza CLR <xref:System.Type> obiekt, który jest typem podstawowym dla określonego typu XAML.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|`prefix`|Opcjonalna. Prefiks, który mapuje przestrzeń nazw XAML innych niż domyślne. Określenie prefiksu często nie jest konieczne. Zobacz uwagi.|  
|`typeNameValue`|Wymagane. Nazwa typu, który jest rozpoznawalna do bieżącej domyślnej XAML przestrzeni nazw; lub określony mapowanych prefiks Jeśli `prefix` podano.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Type` — Rozszerzenie znaczników ma podobną funkcję do `typeof()` operatora w języku C# lub `GetType` operatora programu Microsoft Visual Basic.  
  
 `x:Type` — Rozszerzenie znaczników dostarcza zachowanie konwersję z ciągu dla właściwości, które przyjmują typ <xref:System.Type>. Dane wejściowe są typu XAML. Relacja między typ XAML w danych wejściowych i wyjściowych CLR <xref:System.Type> jest to, że dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> danych wejściowych <xref:System.Xaml.XamlType>, po wyszukaniu niezbędne <xref:System.Xaml.XamlType> na podstawie kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver>dostarcza kontekst usługi.  
  
 W programie .NET Framework XAML Services obsługi dla tego rozszerzenia znacznika jest definiowany przez <xref:System.Windows.Markup.TypeExtension> klasy.  
  
 W ramach określonej implementacji, niektóre właściwości, które wymagają <xref:System.Type> zgodnie z wartością może zaakceptować nazwę typu bezpośrednio (wartość ciągu typu `Name`). Jednak implementacja to zachowanie jest złożonych scenariuszach. Przykłady zobacz sekcję "Uwagi dotyczące użycia WPF", która jest zgodna.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podawany po `x:Type` ciągu identyfikatora jest przypisany jako <xref:System.Windows.Markup.TypeExtension.TypeName%2A> wartości elementu bazowego <xref:System.Windows.Markup.TypeExtension> rozszerzenie klasy. W obszarze domyślny kontekst schematu XAML dla usług .NET Framework XAML, która jest oparta na typy CLR, wartość tego atrybutu jest <xref:System.Reflection.MemberInfo.Name%2A> żądanego typu, lub który zawiera <xref:System.Reflection.MemberInfo.Name%2A> poprzedzone prefiksu dla przestrzeni nazw XAML innych niż domyślne mapowania.  
  
 `x:Type` — Rozszerzenie znaczników mogą być używane w składni obiektów. W tym przypadku określającą wartość <xref:System.Windows.Markup.TypeExtension.TypeName%2A> właściwość jest wymagana, aby poprawnie zainicjować rozszerzenia.  
  
 `x:Type` — Rozszerzenie znaczników może również służyć jako pełne atrybutu; jednak to wykorzystania nie jest to typowe: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Domyślne Namespace XAML i mapowanie typu  
 Domyślna przestrzeń nazw XAML dla programowania WPF zawiera większość typów XAML, czego potrzebujesz do typowych scenariuszy XAML; Dlatego możesz często uniknąć prefiksy podczas odwoływania się do wartości typu XAML. Może być konieczne zamapować prefiksu, jeśli odwołujesz się do typu z niestandardowego zestawu lub dla typów, które istnieją w zestawie WPF, ale od przestrzeń nazw środowiska CLR, który nie został zmapowany do domyślnej przestrzeni nazw XAML. Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XAML i mapowanie środowiska CLR w przestrzeni nazw, zobacz [przestrzeń nazw XAML i mapowanie Namespace dla WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Typ właściwości tej obsługi Typename co String  
 WPF obsługuje technik, które umożliwiają określenie wartości niektórych właściwości typu <xref:System.Type> bez konieczności `x:Type` użycie rozszerzenia znaczników. Zamiast tego można określić wartość jako ciąg znaków zapewniający nazwę typu. Przykładami są <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> i <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Obsługa tego zachowania nie jest dostępna za pośrednictwem typy konwerterów i rozszerzenia znaczników. Zamiast tego jest to zachowanie odroczenia implementowane za pomocą <xref:System.Windows.FrameworkElementFactory>.  
  
 Technologia Silverlight obsługuje podobne Konwencji. W rzeczywistości Silverlight nie obsługuje obecnie `{x:Type}` w jego obsługa języka XAML i nie akceptuje `{x:Type}` użycia poza w niektórych przypadkach, które są przeznaczone do obsługi migracji XAML w WPF i Silverlight. W związku z tym, zachowanie typename jako ciąg znaków jest wbudowana wszystkie oceny właściwości macierzystej Silverlight gdzie <xref:System.Type> jest wartością.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 zapewnia dodatkową obsługę dla ogólnych typów i modyfikuje zachowanie funkcji `x:TypeArguments` i `x:Type` zapewnienie tej obsługi.  
  
-   `x:TypeArguments` i elementu skojarzonego obiektu dla wystąpienia obiektu ogólny może być w przypadku elementów innych niż katalog główny. Aby uzyskać więcej informacji, zobacz sekcję "XAML 2009" [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 obsługuje składnię do określania ograniczenie typu ogólnego w znacznikach. To mogą być używane przez `x:TypeArguments`, `x:Type`, lub obu tych funkcji w połączeniu.  
  
-   Implementacja WPF XAML podczas przetwarzania XAML 2009 dla obciążenia dodaje również tej możliwości do zachowania konwersji niejawnego typu określone we właściwościach framework, które używają typu <xref:System.Type>.  
  
 W środowisku WPF można użyć funkcji XAML 2009, ale tylko dla luźne XAML (XAML, która nie jest kompilowana do znaczników). XAML kompilowana do znaczników dla platformy WPF i formularz BAML XAML aktualnie nie obsługują tych funkcji i słowa kluczowe XAML 2009.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Style>  
 [Tworzenie szablonów i stylów](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
