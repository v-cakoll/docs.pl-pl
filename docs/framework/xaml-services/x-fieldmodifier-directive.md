---
title: x:FieldModifier — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484724"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML, aby pola dla odwołań do nazwanych obiektów <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> były zdefiniowane z dostępem <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> zamiast zachowania domyślnego.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*Public*|Dokładny ciąg, który można określić <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> w zależności od używanego języka programowania związanego z kodem. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 Jeśli produkcja XAML używa `x:FieldModifier` dowolnego miejsca, element główny tej produkcji XAML musi deklarować [dyrektywę x:class](x-class-directive.md).  
  
## <a name="remarks"></a>Uwagi  
 `x:FieldModifier`nie ma znaczenia w przypadku deklarowania ogólnego poziomu dostępu klasy lub jej elementów członkowskich. Jest to istotne tylko w przypadku przetwarzania kodu XAML, gdy określony obiekt XAML będący częścią produkcji XAML jest przetwarzany i stanie się obiektem, który jest potencjalnie dostępny na grafie obiektów aplikacji. Domyślnie odwołanie do pola dla takiego obiektu jest przechowywane jako prywatne, co uniemożliwia konsumentom kontroli bezpośrednie modyfikowanie grafu obiektów. Zamiast tego użytkownicy kontroli powinni zmodyfikować Graf obiektów przy użyciu standardowych wzorców włączonych przez modele programowania, takich jak Uzyskiwanie głównego układu, kolekcje elementów podrzędnych, dedykowane właściwości publiczne itd.  
  
 Wartość `x:FieldModifier` atrybutu różni się w zależności od języka programowania, a jego cel może się różnić w określonych strukturach. Ciąg, który ma być używany, zależy od tego, w <xref:System.CodeDom.Compiler.CodeDomProvider> jaki sposób każdy język implementuje swój i konwertery typów, które <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zwraca <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, aby zdefiniować znaczenie dla i, oraz czy w tym języku jest uwzględniana wielkość liter.  
  
- Dla C#, ciąg, który ma zostać przekazany <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> do `public`wyznaczenia.  
  
- W przypadku programu Microsoft Visual Basic .NET ciąg, który ma zostać <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> przekazany `Public`do wyznaczenia.  
  
- Dla C++/CLI nie istnieją żadne elementy docelowe dla języka XAML. w związku z tym ciąg do przekazania jest niezdefiniowany.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> Można również określić (`internal` w C#, w `Friend` Visual Basic), ale <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> określić, że jest `NotPublic` nietypowe, ponieważ zachowanie jest już domyślne.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>jest zachowaniem domyślnym, ponieważ jest rzadko, gdy kod poza zestawem, który skompilowany XAML, potrzebuje dostępu do elementu utworzonego w języku XAML. Architektura zabezpieczeń WPF wraz z zachowaniem kompilacji XAML nie deklaruje pól, które przechowują wystąpienia elementów jako publiczne, chyba że `x:FieldModifier` określono opcję zezwalania na dostęp publiczny.  
  
 `x:FieldModifier`ma zastosowanie tylko do elementów z [dyrektywą x:Name](x-name-directive.md) , ponieważ ta nazwa jest używana do odwoływania się do pola po jego publicznym.  
  
 Domyślnie Klasa częściowa elementu głównego jest publiczna; można jednak sprawić, aby był niepubliczny za pomocą [dyrektywy x:ClassModifier —](x-classmodifier-directive.md). [Dyrektywa x:ClassModifier —](x-classmodifier-directive.md) ma także wpływ na poziom dostępu wystąpienia klasy elementu głównego. Można umieścić zarówno `x:Name` element, `x:FieldModifier` jak i na elemencie głównym, ale tylko publiczną kopię pola elementu głównego z prawdziwym poziomem dostępu klasy elementu głównego, nadal kontrolowanym przez [dyrektywę x:ClassModifier —](x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Zobacz także

- [Klasy XAML i niestandardowe dla WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Plik codebehind i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name, dyrektywa](x-name-directive.md)
- [Kompilowanie aplikacji WPF (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier, dyrektywa](x-classmodifier-directive.md)
