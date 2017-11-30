---
title: "Typy ogólne w XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 05eaab4497949231d32ceab0ba696b9f252d67ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generics-in-xaml"></a>Typy ogólne w XAML
.NET Framework XAML usług zgodnie z implementacją w System.Xaml zapewnia obsługę przy użyciu ogólnych typów CLR. Ta obsługa obejmuje określenie ograniczenia ogólne jako argumentu typu i wymuszanie ograniczenia wywołując odpowiednie `Add` metody w przypadku kolekcji ogólnej. W tym temacie opisano aspekty przy użyciu i odwołuje się do typów ogólnych w języku XAML.  
  
## <a name="xtypearguments"></a>x: typearguments —  
 `x:TypeArguments`dyrektywa jest zdefiniowany w języku XAML. Gdy jest używany jako element członkowski typu XAML, który nie jest obsługiwana przez typu ogólnego, `x:TypeArguments` przekazuje ograniczający wpisz argumentów ogólnych do konstruktora zapasowego. Odwołanie składni, które odnoszą się do usług .NET Framework XAML użycie `x:TypeArguments`, który zawiera przykłady składni, zobacz [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Ponieważ `x:TypeArguments` ciąg znaków, a ma zapasowy konwertera typów, zazwyczaj jest zadeklarowany w XAML użycia jako atrybut.  
  
 W strumieniu węzłów XAML, informacje deklarowana przez `x:TypeArguments` można uzyskać od <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> na `StartObject` pozycji w strumieniu węzłów. Wartość zwracana <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> znajduje się lista <xref:System.Xaml.XamlType> wartości. Określenie, czy typ XAML reprezentuje typu ogólnego jest możliwe przez wywołanie metody <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Reguły i składnia Konwencji typy ogólne w XAML  
 W języku XAML typu ogólnego zawsze musi być reprezentowana jako zwykły ograniczonego; rodzajowa nieograniczonego nigdy nie znajduje się w systemie typów języka XAML lub strumień węzłów XAML i nie można przedstawić w kodzie XAML. Ogólnego może być przywoływany w składni atrybutu XAML, w przypadkach, gdy jest ograniczenie typu zagnieżdżonego ogólnego odwołuje `x:TypeArguments`, lub w przypadku, gdy `x:Type` zawiera odwołanie do typu CLR dla typu ogólnego. Ta funkcja jest obsługiwana przez <xref:System.Xaml.Schema.XamlTypeTypeConverter> klasy zdefiniowanej przez usług .NET Framework XAML.  
  
 Formularz składni włączane przez atrybut XAML <xref:System.Xaml.Schema.XamlTypeTypeConverter> zmienia typowe MSIL / Konwencja składni CLR, która używa kąt nawiasy dla typów i ograniczenia ogólne i zamiast tego zastępuje nawiasy dla kontenera ograniczenia. Na przykład zobacz [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Typy ogólne i XAML 2009 — funkcje  
 Jeśli używasz XAML 2009 zamiast mapowania CLR typy uzyskać dla wspólnych elementów podstawowych języka XAML typy podstawowe, możesz użyć [typy wbudowane XAML 2009](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) jako elementów informacji w `x:TypeArguments`. Na przykład można zadeklarować następujące (prefiksu mapowania nie są wyświetlane, ale `x` jest przestrzeni nazw XAML języka XAML dla XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Obsługa typów ogólnych w WPF i innych platform, w wersji 3.5  
 XAML 2006 użycia, gdy w szczególności WPF [x: Class](../../../docs/framework/xaml-services/x-class-directive.md) należy dostarczyć także w tym samym elemencie jako `x:TypeArguments`, oraz że element musi być główny element dokumentu XAML. Element główny musi być zamapowany przy użyciu co najmniej jeden typ argumentu typu ogólnego. Na przykład <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Możliwe rozwiązania do obsługi ogólnego użycia obejmują definiowanie rozszerzenia znaczników niestandardowych, które może zwracać typów ogólnych lub podając zawijania klasy definicji, która pochodzi z typu ogólnego, ale spłaszcza ogólne ograniczenia w definicji klasy.  
  
 WPF i przeznaczonych dla [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], można użyć XAML 2009 — funkcje razem z `x:TypeArguments`, ale tylko w przypadku utracić XAML (XAML, który nie jest kompilowany do znaczników). Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.  
  
 Niestandardowe przepływy pracy w [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] dla [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] nie obsługują ogólnego użycia języka XAML.  
  
## <a name="see-also"></a>Zobacz też  
 [x: typearguments — dyrektywa](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
