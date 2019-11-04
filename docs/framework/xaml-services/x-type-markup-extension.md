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
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459912"
---
# <a name="xtype-markup-extension"></a>x:Type — Rozszerzenie znaczników
Dostarcza obiekt CLR <xref:System.Type>, który jest typem podstawowym dla określonego typu XAML.  
  
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
|`prefix`|Opcjonalny. Prefiks, który mapuje niedomyślną przestrzeń nazw XAML. Określanie prefiksu jest często niepotrzebne. Zobacz uwagi.|  
|`typeNameValue`|Wymagany. Nazwa typu rozpoznawana jako bieżąca domyślna przestrzeń nazw XAML; lub określony zamapowany prefiks, jeśli podano `prefix`.|  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenie znacznika `x:Type` ma podobną funkcję do operatora `typeof()` w C# lub operatora `GetType` w programie Microsoft Visual Basic.  
  
 Rozszerzenie znaczników `x:Type` zawiera zachowanie konwersji ciągów dla właściwości, które przyjmują typ <xref:System.Type>. Dane wejściowe są typu XAML. Relacja między wejściowym typem XAML i wyjściowym środowiskiem CLR <xref:System.Type> polega na tym, że <xref:System.Type> wyjściowy jest <xref:System.Xaml.XamlType.UnderlyingType%2A>em <xref:System.Xaml.XamlType>danych wejściowych, po wyszukaniu niezbędnych <xref:System.Xaml.XamlType> na podstawie kontekstu schematu XAML i usługi <xref:System.Windows.Markup.IXamlTypeResolver>.  
  
 W .NET Framework usługach XAML obsługa tego rozszerzenia znacznika jest definiowana przez klasę <xref:System.Windows.Markup.TypeExtension>.  
  
 W określonych implementacjach platformy niektóre właściwości, które przyjmują <xref:System.Type> jako wartość mogą akceptować nazwę typu bezpośrednio (wartość ciągu typu `Name`). Jednak wdrożenie tego zachowania jest złożonym scenariuszem. Aby zapoznać się z przykładami, zobacz sekcję "uwagi dotyczące użycia platformy WPF" poniżej.  
  
 Składnią atrybutu jest składnia najczęściej używana z tym rozszerzeniem znacznika. Token ciągu podany po ciągu identyfikatora `x:Type` jest przypisywany jako wartość <xref:System.Windows.Markup.TypeExtension.TypeName%2A> źródłowej klasy rozszerzenia <xref:System.Windows.Markup.TypeExtension>. W ramach domyślnego kontekstu schematu XAML dla .NET Framework usług XAML, który jest oparty na typach CLR, wartość tego atrybutu jest <xref:System.Reflection.MemberInfo.Name%2A> żądanego typu lub zawiera <xref:System.Reflection.MemberInfo.Name%2A> poprzedzony prefiksem dla mapowania przestrzeni nazw w języku XAML innym niż domyślne.  
  
 Rozszerzenia znaczników `x:Type` można używać w składni elementu obiektu. W takim przypadku określenie wartości właściwości <xref:System.Windows.Markup.TypeExtension.TypeName%2A> jest wymagane do prawidłowego zainicjowania rozszerzenia.  
  
 Rozszerzenia znaczników `x:Type` można także użyć jako atrybutu pełnego; Jednak to użycie nie jest typowe: `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>Domyślna przestrzeń nazw XAML i mapowanie typu  
 Domyślna przestrzeń nazw XAML dla programowania WPF zawiera większość typów XAML potrzebnych dla typowych scenariuszy języka XAML; w związku z tym, można często unikać prefiksów podczas odwoływania się do wartości typu XAML. Może być konieczne zamapowanie prefiksu, jeśli odwołujesz się do typu z niestandardowego zestawu lub dla typów, które istnieją w zestawie WPF, ale pochodzą z przestrzeni nazw CLR, która nie została zmapowana do domyślnej przestrzeni nazw XAML. Aby uzyskać więcej informacji na temat prefiksów, przestrzeni nazw XAML i mapowania przestrzeni nazw środowiska CLR, zobacz [przestrzenie nazw XAML i mapowanie przestrzeni nazw dla języka XAML WPF](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
### <a name="type-properties-that-support-typename-as-string"></a>Właściwości typu, które obsługują atrybut TypeName as  
 WPF obsługuje techniki, które umożliwiają określanie wartości niektórych właściwości typu <xref:System.Type> bez konieczności używania rozszerzenia `x:Type` znaczników. Zamiast tego można określić wartość jako ciąg, który określa nazwę typu. Przykłady <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> i <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>. Obsługa tego zachowania nie jest zapewniana za pomocą konwerterów typów ani rozszerzeń znaczników. Zamiast tego jest to zachowanie odroczenia implementowane za pomocą <xref:System.Windows.FrameworkElementFactory>.  
  
 Program Silverlight obsługuje podobną Konwencję. W rzeczywistości Technologia Silverlight obecnie nie obsługuje `{x:Type}` w jej obsłudze języka XAML i nie akceptuje `{x:Type}` użycia poza kilka okoliczności, które są przeznaczone do obsługi migracji XAML programu Silverlight. W związku z tym, zachowanie typu "typename" jest wbudowane we wszystkich obliczeniach natywnych właściwości Silverlight, gdzie <xref:System.Type> jest wartością.  
  
## <a name="xaml-2009"></a>XAML 2009  
 Język XAML 2009 zapewnia dodatkową pomoc techniczną dla typów ogólnych i modyfikuje zachowanie funkcji `x:TypeArguments` i `x:Type` w celu zapewnienia tej pomocy technicznej.  
  
- `x:TypeArguments` i element skojarzonego obiektu dla tworzenia wystąpienia obiektu ogólnego mogą znajdować się w elementach innych niż główny. Aby uzyskać więcej informacji, zobacz sekcję "XAML 2009" w [dyrektywie x:TypeArguments —](x-typearguments-directive.md).  
  
- XAML 2009 obsługuje składnię do określania ograniczenia typu ogólnego w znaczniku. Może to być używane przez `x:TypeArguments`, przez `x:Type`lub przez dwie funkcje.  
  
- Implementacja języka XAML WPF podczas przetwarzania kodu XAML 2009 do załadowania również dodaje tę możliwość do zachowania niejawnej konwersji typów dla niektórych właściwości platformy, które używają typu <xref:System.Type>.  
  
 W programie WPF można używać funkcji języka XAML 2009, ale tylko w przypadku swobodnego języka XAML (XAML, który nie jest skompilowany do adiustacji). Skompilowane znaczniki XAML dla WPF i forma BAML języka XAML nie obsługują obecnie słów kluczowych i funkcji języka XAML 2009.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Style>
- [Tworzenie szablonów i stylów](../wpf/controls/styling-and-templating.md)
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [Rozszerzenia znaczników i WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
