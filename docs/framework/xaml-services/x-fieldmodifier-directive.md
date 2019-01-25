---
title: x:FieldModifier — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 0ce219ca5477c5714225cfc86fe29334bea30a88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611205"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML, tak aby pola dla odwołania do obiektu o nazwie są definiowane za pomocą <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> dostępu zamiast <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> zachowanie domyślne.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*Public*|Dokładnie taki ciąg znaków można przekazać do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> różni się w zależności od tego, jest używany język programowania związane z kodem. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 Jeśli korzysta z produkcji XAML `x:FieldModifier` w dowolnym miejscu, należy zadeklarować element główny produkcji XAML [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md).  
  
## <a name="remarks"></a>Uwagi  
 `x:FieldModifier` nie jest odpowiednia do deklarowania poziom dostępu ogólne klasy lub jej elementów członkowskich. Może to być istotne tylko w przypadku przetwarzania XAML zachowanie, gdy określonego obiektu XAML, który jest częścią produkcji XAML jest przetwarzane i staje się obiektem potencjalnie dostępnym na grafie obiektu aplikacji. Domyślnie odwołania pola dla takiego obiektu jest przechowywany prywatny, który uniemożliwia modyfikowanie wykresu obiektu bezpośrednio przez konsumentów kontroli. Zamiast tego kontroli odbiorcy oczekują, aby zmodyfikować wykres obiektu za pomocą standardowych wzorców, które są włączone, modele programowania, takich jak dzięki uzyskaniu głównym obiektem układu elementu podrzędnego elementu kolekcji, dedykowanych właściwości publiczne i tak dalej.  
  
 Wartość `x:FieldModifier` atrybutu zależy od języka programowania, a jej celem może różnić się w określonej struktury. Parametry do użycia zależy od tego, jak każdy język implementuje jego <xref:System.CodeDom.Compiler.CodeDomProvider> i konwertery typu, zwraca go do zdefiniowania znaczenie dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, i czy ten język jest uwzględniana wielkość liter.  
  
-   Dla języka C#, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest `public`.  
  
-   Dla programu Microsoft Visual Basic .NET, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest `Public`.  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], żadnych elementów docelowych dla XAML obecnie istnieje; dlatego parametry do przekazania jest niezdefiniowana.  
  
 Można również określić <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` w C#, `Friend` w języku Visual Basic) ale określanie <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> nietypowego ponieważ `NotPublic` zgodnie z zachowaniem już jest ustawieniem domyślnym.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest to zachowanie domyślne, ponieważ jest rzadkie, że kodu spoza zestawu, który skompilowany XAML wymaga dostępu do elementu utworzone XAML. Architektura zabezpieczeń WPF wraz z zachowanie kompilacji XAML nie uzna pola, które przechowują wystąpienia elementu jako publiczne, chyba że specjalnie `x:FieldModifier` aby pozwolić na publiczny dostęp.  
  
 `x:FieldModifier` dotyczy tylko elementów o [x: Name — dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md) , ponieważ ta nazwa będzie używana do odwołanie do pola, gdy jest on publiczny.  
  
 Domyślnie jest publiczna; częściowe klasy dla elementu głównego Jednakże, możesz przekształcić ją w niepublicznych przy użyciu [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md). [X: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md) wpływa również na poziom dostępu do wystąpienia klasy elementu głównego. Możesz umieścić zarówno `x:Name` i `x:FieldModifier` w katalogu głównym elementu, ale tylko sprawia, że pole publiczne kopię element główny z głównego true element klasy poziomem dostępu, nadal kontrolowane przez [x: classmodifier — dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Zobacz także
- [Klasy XAML i niestandardowe dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Plik codebehind i XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name, dyrektywa](../../../docs/framework/xaml-services/x-name-directive.md)
- [Kompilowanie aplikacji WPF (WPF)](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier, dyrektywa](../../../docs/framework/xaml-services/x-classmodifier-directive.md)
