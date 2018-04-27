---
title: x:Type — Rozszerzenie znaczników
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db56c2bcdca14b87de320dfe19a6c364c76ecef7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
|`typeNameValue`|Wymagana. Nazwa typu rozpoznać bieżącej domyślnej XAML przestrzeni nazw; lub określony zamapować prefiksu Jeśli `prefix` podano.|  
  
## <a name="remarks"></a>Uwagi  
 `x:Type` — Rozszerzenie znaczników ma podobną funkcję do `typeof()` operatora w języku C# lub `GetType` operatora programu Microsoft Visual Basic.  
  
 `x:Type` — Rozszerzenie znaczników dostarcza zachowanie konwersję z ciągu dla właściwości, które przyjmują typ <xref:System.Type>. Dane wejściowe są typu XAML. Relacja między XAML typ danych wejściowych i wyjściowych CLR <xref:System.Type> jest to, że dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> danych wejściowych <xref:System.Xaml.XamlType>, po wyszukiwania niezbędnych <xref:System.Xaml.XamlType> na podstawie kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver>usługi udostępnia kontekst.  
  
 W programie .NET Framework XAML Services obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.TypeExtension> klasy.  
  
 W ramach określonej implementacji, niektóre właściwości, które wymagają <xref:System.Type> jako wartość może zaakceptować nazwę typu bezpośrednio (ciąg typu `Name`). Jednak implementacja to zachowanie jest złożonych scenariuszach. Przykłady można znaleźć w sekcji "Uwagi dotyczące użycia WPF".  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu po `x:Type` przypisany jako identyfikator ciągu <xref:System.Windows.Markup.TypeExtension.TypeName%2A> wartości podstawowych <xref:System.Windows.Markup.TypeExtension> rozszerzenie klasy. W obszarze domyślny kontekst schematu XAML dla usług .NET Framework XAML, które jest oparte na typy CLR, wartość tego atrybutu to <xref:System.Reflection.MemberInfo.Name%2A> odpowiedniego typu, lub które zawiera <xref:System.Reflection.MemberInfo.Name%2A> poprzedzone prefiksu dla przestrzeni nazw XAML innych niż domyślne mapowania.  
  
 `x:Type` — Rozszerzenie znaczników mogą być używane w składni elementu obiekt. W takim przypadku określającą wartość <xref:System.Windows.Markup.TypeExtension.TypeName%2A> jest wymagana właściwość, aby poprawnie zainicjować rozszerzenia.  
  
 `x:Type` — Rozszerzenie znaczników mogą służyć jako atrybut pełne; mimo to nie jest typowe: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Domyślne mapowanie typu i Namespace XAML  
 Większość typów XAML potrzebnych dla typowych scenariuszy XAML; zawiera domyślnej przestrzeni nazw XAML programowania WPF w związku z tym można często uniknąć prefiksy podczas odwoływania się do wartości typu XAML. Konieczne może być zamapować prefiksu, jeśli utworzono odwołanie do typu z niestandardowego zestawu lub dla typów, które istnieją w zestawie WPF, ale z przestrzeni nazw CLR, która nie została zmapowana na domyślnej przestrzeni nazw XAML. Aby uzyskać więcej informacji na temat prefiksy przestrzeni nazw XAML i mapowania nazw CLR, zobacz [przestrzeń nazw XAML i Namespace mapowanie dla WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Typ właściwości tej obsługi Typename jako ciągu  
 WPF obsługuje techniki, które umożliwiają określanie wartości niektórych właściwości typu <xref:System.Type> bez konieczności `x:Type` użycie rozszerzenia znaczników. Zamiast tego można określić wartość jako ciąg nazwy typu. Przykładami są <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> i <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Obsługa tego zachowania nie jest zapewniana za pomocą typy konwerterów i rozszerzenia znaczników. Zamiast tego jest to zachowanie odroczenia implementowane za pośrednictwem <xref:System.Windows.FrameworkElementFactory>.  
  
 Silverlight obsługuje podobne Konwencji. W rzeczywistości Silverlight nie obsługuje obecnie `{x:Type}` w jego obsługę języka XAML i nie akceptuje `{x:Type}` użycia poza w niektórych przypadkach, które są przeznaczone do obsługi migracji WPF Silverlight XAML. W związku z tym zachowanie typename jako parametry są wbudowane wszystkie oceny właściwości macierzystej Silverlight gdzie <xref:System.Type> jest wartość.  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 zapewnia obsługę dodatkowych rodzajowa typów i modyfikuje zachowanie funkcji `x:TypeArguments` i `x:Type` aby zapewnić obsługę tego.  
  
-   `x:TypeArguments` i elementu skojarzonego obiektu dla wystąpienia obiektu ogólny może być na elementów innych niż katalog główny. Aby uzyskać więcej informacji, zobacz sekcję "XAML 2009" [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
-   XAML 2009 obsługuje składnię służący do określania ograniczenie typu ogólnego w znaczniku. Może być używany przez `x:TypeArguments`, przez `x:Type`, lub obu tych funkcji w połączeniu.  
  
-   Implementacja WPF XAML podczas przetwarzania XAML 2009 dla obciążenia dodaje również tej możliwości do zachowanie konwersji typu niejawnego pewne właściwości framework, które używają typu <xref:System.Type>.  
  
 Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko w przypadku utracić XAML (XAML, który nie jest kompilowany do znaczników). Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Style>  
 [Tworzenie szablonów i stylów](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozszerzenia znaczników i WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
