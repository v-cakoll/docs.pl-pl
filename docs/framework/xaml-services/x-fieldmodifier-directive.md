---
title: "x:FieldModifier — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 77745744c0da1e4b4425af6d8e4319faaf524908
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML, tak aby pól dla odwołania do nazwanych obiektów są zdefiniowane z <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> dostępu zamiast <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> zachowanie domyślne.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*Publiczna*|Dokładnie taki ciąg znaków, należy przekazać do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> może być różna w zależności od jest używany język programowania związane z kodem. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 Jeśli używa produkcji XAML `x:FieldModifier` wszędzie, musi mieć deklarację elementu głównego XAML produkcji [dyrektywy x: Class](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Uwagi  
 `x:FieldModifier`nie jest ważna deklarowania poziom dostępu ogólne klasy lub jego elementów członkowskich. Jest zastosowanie tylko w przypadku zachowania przetwarzania XAML podczas określonego obiektu XAML, który jest częścią sieci produkcyjnej XAML jest przetwarzane i staje się obiekt, który jest potencjalnie dostępny na wykresie obiektu aplikacji. Domyślnie odwołania pola dla takiego obiektu polega ochrona poufności, który uniemożliwia bezpośrednie modyfikowanie wykres obiektu przez konsumentów kontroli. Zamiast tego formantu konsumentów powinny modyfikowanie wykres obiektu przy użyciu standardowych wzorców, które są włączane przez modele programowania, takich jak, uzyskując główny układu elementu podrzędnego elementu kolekcji, dedykowane właściwości publiczne i tak dalej.  
  
 Wartość `x:FieldModifier` atrybutu zależy od języka programowania, a jej celem może różnić się w określonej struktury. Ciąg do użycia zależy od tego, jak implementuje każdego języka jego <xref:System.CodeDom.Compiler.CodeDomProvider> i konwertery typu zwraca do definiowania znaczenie dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, oraz czy ten język jest uwzględniana wielkość liter.  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest `public`.  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)], parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest `Public`.  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], obecnie istnieje elementów docelowych dla XAML; dlatego parametry do przekazania jest niezdefiniowany.  
  
 Można również określić <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` w [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)], `Friend` w [!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)]) ale określania <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> rzadko ponieważ `NotPublic` jako zachowanie jest już domyślnie.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>jest zachowanie domyślne, ponieważ jest rzadko, że kod spoza zestawu, który skompilowany XAML musi mieć dostęp do elementu utworzonych w języku XAML. Architektura zabezpieczeń WPF wraz z zachowaniem kompilacji XAML nie deklaruje pola, które przechowują wystąpienia elementu jako public, chyba że użytkownik `x:FieldModifier` umożliwiających dostęp do publicznego.  
  
 `x:FieldModifier`dotyczy tylko elementów z [x: Name — dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md) ponieważ ta nazwa jest używana do odwołanie do pola po nie jest publiczny.  
  
 Domyślnie jest publiczny; częściowej klasy dla elementu głównego jednak można tworzyć niepubliczne przy użyciu [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md). [X: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md) również wpływa na poziom dostępu do wystąpienia klasy głównym elementu. Możesz też zaznaczyć oba `x:Name` i `x:FieldModifier` w katalogu głównym elementu, ale tylko sprawia, że pole publiczne kopię element główny z głównego true element klasy poziom dostępu nadal kontrolowane przez [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Zobacz też  
 [XAML oraz klas niestandardowych dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Związane z kodem i języka XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x: Name — dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md)  
 [Tworzenie aplikacji WPF (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
