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
ms.openlocfilehash: a24277a4d5fbc4870157b6c8ba00ba71ba61e656
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837236"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML, gdy podano również `x:Class`. W przeciwieństwie do tworzenia częściowej `class`, która ma `Public` dostępu (wartość domyślna), udostępniony `x:Class` jest tworzony z poziomu dostępu `NotPublic`. To zachowanie ma wpływ na poziom dostępu dla klasy w wygenerowanych zestawach.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```xaml  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*NotPublic*|Dokładny ciąg, który ma zostać przekazany do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType>, a <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> różni się w zależności od używanego języka programowania związanego z kodem. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 [x:Class](x-class-directive.md) musi również znajdować się na tym samym elemencie, a element musi być elementem głównym na stronie. Aby uzyskać więcej informacji, zobacz [sekcję\[MS-XAML\] sekcji 4.3.1.8](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Uwagi  
 Wartość `x:ClassModifier` w .NET Framework użyciu usług XAML różni się w zależności od języka programowania. Ciąg, który ma być używany, zależy od tego, w jaki sposób każdy język implementuje swoją <xref:System.CodeDom.Compiler.CodeDomProvider>, i konwertery typów, które zwraca, aby zdefiniować znaczenia dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>oraz czy w tym języku jest uwzględniana wielkość liter.  
  
- Dla C#, ciąg, który ma zostać przekazany do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `internal`.  
  
- W przypadku programu Microsoft Visual Basic .NET ciąg, który ma zostać przekazany do wyznaczania <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `Friend`.  
  
- Dla C++/CLI nie istnieją żadne elementy docelowe, które obsługują kompilowanie kodu XAML; w związku z tym wartość do przekazania nie została określona.  
  
 Możesz również określić <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` w C#, `Public` w Visual Basic). jednak Określanie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest rzadko wykonywane, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest już zachowaniem domyślnym.  
  
 Inne wartości mające równoważne ograniczenia poziomu dostępu do kodu użytkownika, takie jak `private` C#w, nie są istotne dla `x:ClassModifier`, ponieważ odwołania do klas zagnieżdżonych nie są obsługiwane w języku XAML i w związku z tym modyfikator <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ma ten sam efekt.  
  
## <a name="security-notes"></a>Uwagi dotyczące zabezpieczeń  
 Poziom dostępu zadeklarowany w `x:ClassModifier` nadal podlega interpretacji przez poszczególne struktury i ich możliwości. WPF obejmuje możliwości ładowania i tworzenia wystąpienia typów, w których `x:ClassModifier` jest `internal`, jeśli ta klasa jest przywoływana z zasobu WPF za pomocą odwołania do identyfikatora URI pakietu. W związku z tym w tym przypadku i potencjalnie innym, podobnym do wdrożonym przez inne struktury, nie należy polegać wyłącznie na `x:ClassModifier`, aby zablokować wszystkie możliwe próby utworzenia wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- [x:Class, dyrektywa](x-class-directive.md)
- [Plik codebehind i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier, dyrektywa](x-fieldmodifier-directive.md)
- [Zabezpieczenia (WPF)](../wpf/security-wpf.md)
- [Typy migrowane z WPF do System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
