---
title: x:FieldModifier — dyrektywa
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 3e104b4c464d545e048f29901701c1c3dbb68229
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071529"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier — dyrektywa
Modyfikuje zachowanie kompilacji XAML, dzięki czemu pola <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> dla odwołań <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> do nazwanych obiektów są definiowane z dostępem zamiast domyślnego zachowania.

## <a name="xaml-attribute-usage"></a>Użycie atrybutu języka XAML

```xaml
<object x:FieldModifier="Public".../>
```

## <a name="xaml-values"></a>Wartości XAML

|||
|-|-|
|*Publicznego*|Dokładny ciąg, który <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> przekazujesz do określenia w porównaniu <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> różni się, w zależności od języka programowania związane z kodem, który jest używany. Zobacz uwagi.|

## <a name="dependencies"></a>Zależności

 Jeśli produkcja XAML `x:FieldModifier` używa w dowolnym miejscu, główny element tej produkcji XAML musi zadeklarować [x:Class Directive](xclass-directive.md).

## <a name="remarks"></a>Uwagi

`x:FieldModifier`nie jest istotne dla deklarowania ogólnego poziomu dostępu klasy lub jej członków. Jest to istotne tylko dla zachowania przetwarzania XAML, gdy określony obiekt XAML, który jest częścią produkcji XAML jest przetwarzany i staje się obiektem, który jest potencjalnie dostępny na wykresie obiektu aplikacji. Domyślnie odwołanie do pola dla takiego obiektu jest utrzymywane jako prywatne, co uniemożliwia konsumentom kontroli bezpośrednie modyfikowanie wykresu obiektu. Zamiast tego oczekuje się, że konsumenci kontroli zmodyfikują wykres obiektów przy użyciu standardowych wzorców, które są włączone przez modele programowania, takie jak uzyskanie katalogu głównego układu, kolekcji elementów podrzędnych, dedykowanych właściwości publicznych i tak dalej.

Wartość atrybutu `x:FieldModifier` różni się w zależności od języka programowania, a jego przeznaczenie może się różnić w określonych ramach. Ciąg do użycia zależy od tego, <xref:System.CodeDom.Compiler.CodeDomProvider> jak każdy język implementuje jego i <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>konwertery typów zwraca do definiowania znaczeń dla i , i czy w tym języku jest rozróżniana wielkość liter.

- W przypadku języka C#ciąg, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> który `public`ma być przekazywalny, to .

- W przypadku programu Microsoft Visual Basic .NET <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public`ciąg, który ma być przekazyny do wyznaczenia, to .

- W przypadku języka C++/CLI nie istnieją obecnie żadne obiekty docelowe dla języka XAML; w związku z tym ciąg do przekazania jest niezdefiniowany.

Można również <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> określić (`internal` `Friend` w języku C#, <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> w języku Visual Basic), ale określenie jest nietypowe, ponieważ `NotPublic` zachowanie jest już domyślne.

<xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>jest zachowaniem domyślnym, ponieważ jest rzadkie, że kod poza zestawem, który skompilował XAML potrzebuje dostępu do elementu utworzonego przez XAML. Architektura zabezpieczeń WPF wraz z zachowaniem kompilacji XAML nie deklaruje pól, które `x:FieldModifier` przechowują wystąpienia elementu jako publiczne, chyba że specjalnie ustawić, aby umożliwić dostęp publiczny.

`x:FieldModifier`jest istotne tylko dla elementów z [x:Name Dyrektywy,](xname-directive.md) ponieważ ta nazwa jest używana do odwoływania się do pola po jego publicznych.

Domyślnie klasa częściowa dla elementu głównego jest publiczna; jednak można uczynić go niepubliczne przy użyciu [x:ClassModifier dyrektywy](xclassmodifier-directive.md). [X:ClassModifier Dyrektywy](xclassmodifier-directive.md) wpływa również na poziom dostępu wystąpienia klasy elementu głównego. Można umieścić `x:Name` zarówno `x:FieldModifier` i na element główny, ale to tylko sprawia, że publiczna kopia pola elementu głównego, z poziomem dostępu do klasy elementu głównego true nadal kontrolowane przez [x:ClassModifier dyrektywy](xclassmodifier-directive.md).

## <a name="see-also"></a>Zobacz też

- [Klasy XAML i niestandardowe dla WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Związane z kodem i XAML w WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name — dyrektywa](xname-directive.md)
- [Kompilowanie aplikacji WPF (WPF)](../../framework/wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier — dyrektywa](xclassmodifier-directive.md)
