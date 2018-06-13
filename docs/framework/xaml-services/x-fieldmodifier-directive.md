---
title: x:FieldModifier — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 1c7cb10a8021189aaac0ab8cfe5cc04ff8e67905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565062"
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
|*Public*|Dokładnie taki ciąg znaków, należy przekazać do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> może być różna w zależności od jest używany język programowania związane z kodem. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 Jeśli używa produkcji XAML `x:FieldModifier` wszędzie, musi mieć deklarację elementu głównego XAML produkcji [dyrektywy x: Class](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Uwagi  
 `x:FieldModifier` nie jest ważna deklarowania poziom dostępu ogólne klasy lub jego elementów członkowskich. Jest zastosowanie tylko w przypadku zachowania przetwarzania XAML podczas określonego obiektu XAML, który jest częścią sieci produkcyjnej XAML jest przetwarzane i staje się obiekt, który jest potencjalnie dostępny na wykresie obiektu aplikacji. Domyślnie odwołania pola dla takiego obiektu polega ochrona poufności, który uniemożliwia bezpośrednie modyfikowanie wykres obiektu przez konsumentów kontroli. Zamiast tego formantu konsumentów powinny modyfikowanie wykres obiektu przy użyciu standardowych wzorców, które są włączane przez modele programowania, takich jak, uzyskując główny układu elementu podrzędnego elementu kolekcji, dedykowane właściwości publiczne i tak dalej.  
  
 Wartość `x:FieldModifier` atrybutu zależy od języka programowania, a jej celem może różnić się w określonej struktury. Ciąg do użycia zależy od tego, jak implementuje każdego języka jego <xref:System.CodeDom.Compiler.CodeDomProvider> i konwertery typu zwraca do definiowania znaczenie dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, oraz czy ten język jest uwzględniana wielkość liter.  
  
-   Język C#, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest `public`.  
  
-   Dla programu Microsoft Visual Basic .NET, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest `Public`.  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], obecnie istnieje elementów docelowych dla XAML; dlatego parametry do przekazania jest niezdefiniowany.  
  
 Można również określić <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` w języku C# `Friend` w języku Visual Basic) ale określania <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> rzadko ponieważ `NotPublic` jako zachowanie jest już domyślnie.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest zachowanie domyślne, ponieważ jest rzadko, że kod spoza zestawu, który skompilowany XAML musi mieć dostęp do elementu utworzonych w języku XAML. Architektura zabezpieczeń WPF wraz z zachowaniem kompilacji XAML nie deklaruje pola, które przechowują wystąpienia elementu jako public, chyba że użytkownik `x:FieldModifier` umożliwiających dostęp do publicznego.  
  
 `x:FieldModifier` dotyczy tylko elementów z [x: Name — dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md) ponieważ ta nazwa jest używana do odwołanie do pola po nie jest publiczny.  
  
 Domyślnie jest publiczny; częściowej klasy dla elementu głównego jednak można tworzyć niepubliczne przy użyciu [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md). [X: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md) również wpływa na poziom dostępu do wystąpienia klasy głównym elementu. Możesz też zaznaczyć oba `x:Name` i `x:FieldModifier` w katalogu głównym elementu, ale tylko sprawia, że pole publiczne kopię element główny z głównego true element klasy poziom dostępu nadal kontrolowane przez [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy XAML i niestandardowe dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [Plik codebehind i XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:Name, dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md)  
 [Tworzenie aplikacji WPF (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [x:ClassModifier, dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
