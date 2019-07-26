---
title: x:ClassModifier — dyrektywa
ms.date: 03/30/2017
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
ms.openlocfilehash: c3c08f61b49a6367663cf02099dda86d1a692284
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484748"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML `x:Class` , gdy jest również udostępniane. W odróżnieniu od tworzenia części `class` , która `Public` ma poziom dostępu (wartość domyślna), `NotPublic` podano `x:Class` wartość z poziomu dostępu. To zachowanie ma wpływ na poziom dostępu dla klasy w wygenerowanych zestawach.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*NotPublic*|Dokładny ciąg, który ma zostać przekazany <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> do <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> określonych wartości, w zależności od języka programowania związanego z kodem, który jest używany. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 [x:Class](x-class-directive.md) musi również znajdować się na tym samym elemencie, a element musi być elementem głównym na stronie. Aby uzyskać więcej informacji, zobacz [ \[sekcję MS\] -XAML 4.3.1.8](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Uwagi  
 Wartość `x:ClassModifier` w .NET Framework użyciu usług XAML różni się w zależności od języka programowania. Ciąg, który ma być używany, zależy od tego, w <xref:System.CodeDom.Compiler.CodeDomProvider> jaki sposób każdy język implementuje swój i konwertery typów, które <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> zwraca <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, aby zdefiniować znaczenie dla i, oraz czy w tym języku jest uwzględniana wielkość liter.  
  
- Dla C#, ciąg, który ma zostać przekazany <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> do `internal`wyznaczenia.  
  
- W przypadku programu Microsoft Visual Basic .NET ciąg, który ma zostać <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> przekazany `Friend`do wyznaczenia.  
  
- Dla C++/CLI nie istnieją żadne elementy docelowe, które obsługują kompilowanie kodu XAML; w związku z tym wartość do przekazania nie została określona.  
  
 <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> Można również określić (`public` w C#, `Public` w Visual Basic), jednak Określanie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest nierzadko wykonywane, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest już zachowaniem domyślnym.  
  
 Inne wartości z równoważnymi ograniczeniami poziomu dostępu do kodu użytkownika, `private` na C#przykład w, nie są `x:ClassModifier` istotne dla, ponieważ zagnieżdżone odwołania do klas nie są obsługiwane <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> w języku XAML i w związku z tym modyfikator ma ten sam efekt .  
  
## <a name="security-notes"></a>Uwagi dotyczące zabezpieczeń  
 Poziom dostępu zadeklarowany w programie `x:ClassModifier` jest nadal objęty interpretacją przez poszczególne struktury i ich możliwości. WPF obejmuje możliwości ładowania i tworzenia wystąpienia typów, `x:ClassModifier` gdzie `internal`is, jeśli ta klasa jest przywoływana z zasobu WPF za pośrednictwem odwołania do identyfikatora URI pakietu. W związku z tym w tym przypadku i potencjalnie innym, podobnym do wdrożonym przez inne struktury, nie należy polegać wyłącznie na `x:ClassModifier` tym, aby zablokować wszystkie możliwe próby utworzenia wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- [x:Class, dyrektywa](x-class-directive.md)
- [Plik codebehind i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier, dyrektywa](x-fieldmodifier-directive.md)
- [Zabezpieczenia (WPF)](../wpf/security-wpf.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
