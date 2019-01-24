---
title: Typy ogólne w XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: ddd094d5acb1eea5bf45984c27df93d1de3d53fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491314"
---
# <a name="generics-in-xaml"></a>Typy ogólne w XAML
.NET Framework XAML Services zaimplementowanego w System.Xaml zapewnia obsługę za pomocą typów ogólnych CLR. Ta obsługa obejmuje określenie ograniczenia typów ogólnych jako argument typu i wymuszanie ograniczenia przez wywołanie odpowiedniej `Add` metodę w przypadku kolekcji ogólnej. W tym temacie opisano aspekty przy użyciu i odwoływanie się do typów ogólnych w XAML.  
  
## <a name="xtypearguments"></a>x: typearguments —  
 `x:TypeArguments` dyrektywy zdefiniowano w języku XAML. Gdy jest używany jako członek typu XAML, która jest wspierana przez typ ogólny, `x:TypeArguments` przebiegów, ograniczając wpisz argumenty ogólne do konstruktora zapasowy. Składnia odwołania, które odnoszą się do usług programu .NET Framework XAML użytku z `x:TypeArguments`, który zawiera przykłady składni, zobacz [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Ponieważ `x:TypeArguments` przyjmuje ciąg, a ma zapasowy konwertera typu, zwykle jest ona zadeklarowana w XAML użycia jako atrybut.  
  
 W strumień węzłów XAML, informacje zgłoszone przez `x:TypeArguments` można otrzymać od <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> na `StartObject` pozycji w strumieniu węzła. Wartość zwracana przez <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> znajduje się lista <xref:System.Xaml.XamlType> wartości. Określenie tego, czy typ XAML reprezentuje typ ogólny jest możliwe, wywołując <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Reguły i Konwencji składni typy ogólne w XAML  
 W XAML typ ogólny zawsze musi być reprezentowany jako ograniczone ogólny; nieograniczone ogólny nigdy nie jest obecny w systemie typu XAML lub strumień węzłów XAML i nie może być przedstawiony w znaczniku XAML. Ogólny może być przywoływany w składni atrybutów XAML, w przypadkach, gdy jest ograniczenie zagnieżdżony typ ogólny, do którego nastąpiło odwołanie `x:TypeArguments`, lub w przypadku, gdy `x:Type` dostarcza odwołanie do typu CLR dla typu ogólnego. Jest to obsługiwane za pośrednictwem <xref:System.Xaml.Schema.XamlTypeTypeConverter> klasy zdefiniowane przez .NET Framework XAML Services.  
  
 XAML atrybutu forma składni włączane przez <xref:System.Xaml.Schema.XamlTypeTypeConverter> zmienia typowe MSIL / CLR Konwencji składni, która używa kąt nawiasy kwadratowe dla typów i ograniczenia typów ogólnych i zamiast tego zastępuje nawiasy dla kontenera ograniczenia. Aby uzyskać przykład, zobacz [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Typy ogólne i XAML 2009 — funkcje  
 Jeśli używasz XAML 2009 zamiast mapowania środowiska CLR typy uzyskać typy XAML dla wspólnych elementów podstawowych języka podstawowe, możesz użyć [typy wbudowane XAML 2009](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako elementy informacji w programie `x:TypeArguments`. Na przykład, można zadeklarować następujące (prefiks mapowania nie jest wyświetlane, ale `x` jest przestrzeń nazw XAML języka XAML dla XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Obsługa typów ogólnych w WPF i innych platform 3.5  
 Użycie XAML 2006, podczas których celem jest WPF [x: Class](../../../docs/framework/xaml-services/x-class-directive.md) również musi być podana w tym samym elemencie jako `x:TypeArguments`, a ten element musi być elementem głównym w dokumencie XAML. Element główny musi być mapowane z co najmniej jeden typ argumentu typu ogólnego. Może to być na przykład <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Możliwe rozwiązania do obsługi ogólnego użycia obejmują definiowanie rozszerzenie niestandardowych znaczników, które może zwracać typów ogólnych albo udostępniające opakowywania klas definition, która pochodzi od typu ogólnego, ale spłaszcza ograniczenie generyczne w definicji klasy.  
  
 W WPF i ustawianie elementów docelowych [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], można użyć XAML 2009 — funkcje wraz z `x:TypeArguments`, lecz tylko w przypadku luźne XAML (XAML, która nie jest kompilowana do znaczników). XAML kompilowana do znaczników dla platformy WPF i formularz BAML XAML aktualnie nie obsługują tych funkcji i słowa kluczowe XAML 2009.  
  
 Niestandardowe przepływy pracy w programie Windows Workflow Foundation dla [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] nie obsługują ogólnego użycia XAML.  
  
## <a name="see-also"></a>Zobacz także
- [x:TypeArguments, dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md)
- [x:Class, dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)
- [Typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
