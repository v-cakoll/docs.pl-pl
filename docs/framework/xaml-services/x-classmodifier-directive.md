---
title: x:ClassModifier — dyrektywa
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- xClassModifier
- x:ClassModifier
- ClassModifier
helpviewer_keywords:
- XAML [XAML Services], x:ClassModifier attribute
- x:ClassModifier attribute [XAML Services]
- ClassModifier attribute in XAML [XAML Services]
ms.assetid: ef30ab78-d334-4668-917d-c9f66c3b6aea
caps.latest.revision: 22
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ab6036ecb37bb80588a59b581af0b88fc83230a4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="xclassmodifier-directive"></a>x:ClassModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML podczas `x:Class` jest również udostępniany. W szczególności, zamiast tworzyć częściowym `class` mający `Public` (ustawienie domyślne), poziom dostępu dostarczonego `x:Class` jest tworzony z `NotPublic` poziom dostępu. Dotyczy to poziom dostępu dla tej klasy w wygenerowanych zestawów.  
  
## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML  
  
```  
<object x:Class="namespace.classname" x:ClassModifier="NotPublic">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>Wartości XAML  
  
|||  
|-|-|  
|*NotPublic*|Dokładnie taki ciąg znaków do przekazania do określenia <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> może być różna w zależności od używanej język programowania związane z kodem. Zobacz uwagi.|  
  
## <a name="dependencies"></a>Zależności  
 [x: Class](../../../docs/framework/xaml-services/x-class-directive.md) należy dostarczyć także w tym samym elemencie, a ten element musi być elementem głównym na stronie. Aby uzyskać więcej informacji, zobacz [ \[MS XAML\] sekcji 4.3.1.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Uwagi  
 Wartość `x:ClassModifier` w usługach programu .NET Framework XAML użycia zależy od języka programowania. Ciąg do użycia zależy od tego, jak implementuje każdego języka jego <xref:System.CodeDom.Compiler.CodeDomProvider> i konwertery typu zwraca do definiowania znaczenie dla <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> i <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, oraz czy ten język jest uwzględniana wielkość liter.  
  
-   Język C#, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `internal`.  
  
-   Dla programu Microsoft Visual Basic .NET, parametry do przekazania do wyznaczenia <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> jest `Friend`.  
  
-   Aby uzyskać [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], żadne obiekty docelowe istnieje obsługujące kompilacji XAML; w związku z tym wartość do przekazania jest nieokreślony.  
  
 Można również określić <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> (`public` w języku C# `Public` w języku Visual Basic), jednak określenie <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> rzadko jest wykonywana, ponieważ <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> już jest zachowaniem domyślnym.  
  
 Inne wartości z kodu użytkownika równoważne poziomu dostępu do ograniczenia, takie jak `private` w języku C# nie są istotne dla `x:ClassModifier` odwołania zagnieżdżona klasa nie są obsługiwane w języku XAML i w związku z tym <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> modyfikator działa tak samo.  
  
## <a name="security-notes"></a>Uwagi dotyczące zabezpieczeń  
 Poziom dostępu, zgodnie z deklaracją w `x:ClassModifier` nadal podlega interpretacji przez konkretnego struktur i ich funkcji. WPF zawiera funkcje do ładowania i utworzyć wystąpienia typów gdzie `x:ClassModifier` jest `internal`, jeśli z za pomocą pakietu odwołanie do identyfikatora URI zasobu WPF odwołuje się do tej klasy. W wyniku tego przypadku i potencjalnie innych podoba Ci się implementowane przez innych platform, nie należy polegać wyłącznie na `x:ClassModifier` Aby zablokować wszystkie możliwe podczas tworzenia wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [x:Class, dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Plik codebehind i XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [x:FieldModifier, dyrektywa](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md)  
 [Zabezpieczenia (WPF)](../../../docs/framework/wpf/security-wpf.md)  
 [Typy migrowane z WPF do System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
