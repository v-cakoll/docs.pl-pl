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
ms.openlocfilehash: 436204774c2d59b43a77865c666aed702f7681db
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072033"
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier — dyrektywa
Modyfikuje zachowanie kompilacji `x:Class` XAML, gdy jest również podana. W szczególności zamiast tworzenia `class` częściowego, który `Public` ma poziom dostępu (domyślnie), dostarczone `x:Class` jest tworzony z poziomem `NotPublic` dostępu. To zachowanie wpływa na poziom dostępu dla klasy w wygenerowanych zestawów.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">
   ...
</object>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|*NotPublic*|Dokładny ciąg do przekazania <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> do określenia w porównaniu różni się, w zależności od języka programowania związane z kodem, którego używasz. Zobacz uwagi.|

## <a name="dependencies"></a>Zależności

[x:Klasa](xclass-directive.md) musi być również podana na tym samym elemencie, a ten element musi być elementem głównym na stronie. Aby uzyskać więcej informacji, zobacz [ \[rozdział 4.3.1.8 ms-XAML\] ](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Uwagi

Wartość `x:ClassModifier` użycia usług .NET XAML różni się w zależności od języka programowania. Ciąg do użycia zależy od tego, <xref:System.CodeDom.Compiler.CodeDomProvider> jak każdy język implementuje jego i <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>konwertery typów zwraca do definiowania znaczeń dla i , i czy w tym języku jest rozróżniana wielkość liter.

- W przypadku języka C#ciąg, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> który `internal`ma być przekazywalny, to .

- W przypadku programu Microsoft Visual Basic .NET <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `Friend`ciąg, który ma być przekazyny do wyznaczenia, to .

- W przypadku języka C++/CLI nie istnieją żadne obiekty docelowe obsługujące kompilację XAML; w związku z tym wartość do przekazania jest nieokreślony.

Można również <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> określić (`public` `Public` w języku C#, w języku Visual Basic); jednak określenie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest rzadko wykonywane, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> jest już domyślne zachowanie.

Inne wartości z równoważnych ograniczeń na poziomie `private` dostępu kodu użytkownika, `x:ClassModifier` takich jak w języku C#, nie są istotne dla <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> ponieważ odwołania do klasy zagnieżdżonej nie są obsługiwane w XAML i dlatego modyfikator ma ten sam efekt.

## <a name="security-notes"></a>Uwagi dotyczące zabezpieczeń

Poziom dostępu zadeklarowany `x:ClassModifier` w nadal podlega interpretacji przez określone ramy i ich możliwości. WPF WPF zawiera możliwości ładowania i `x:ClassModifier` `internal`tworzenia wystąpienia typów, gdzie jest , jeśli ta klasa odwołuje się z zasobu WPF za pośrednictwem odwołania identyfikatora URI pakietu. W konsekwencji tego przypadku i potencjalnie innych, takich jak on zaimplementowany przez inne struktury, nie polegać wyłącznie na `x:ClassModifier` zablokować wszystkie możliwe próby wystąpienia.

## <a name="see-also"></a>Zobacz też

- [x:Class — dyrektywa](xclass-directive.md)
- [Związane z kodem i XAML w WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:FieldModifier — dyrektywa](xfieldmodifier-directive.md)
- [Zabezpieczenia (WPF)](../../framework/wpf/security-wpf.md)
- [Typy migrowane z WPF do System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
