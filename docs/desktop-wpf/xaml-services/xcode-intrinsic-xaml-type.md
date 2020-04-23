---
title: x:Code — Typ funkcji XAML
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071557"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code — Typ funkcji XAML
Umożliwia umieszczenie kodu w środowisku produkcyjnym XAML. Taki kod może być skompilowany przez dowolną implementację procesora XAML, który kompiluje XAML, lub pozostawiony w produkcji XAML do późniejszych zastosowań, takich jak interpretacja przez środowisko wykonawcze.

## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>Uwagi

Kod w `x:Code` elemencie dyrektywy XAML jest nadal interpretowany w ogólnej przestrzeni nazw XML i dostarczonych przestrzeniach nazw XAML. W związku z tym zwykle konieczne jest `x:Code` ująć kod używany do wewnątrz segmentu. `CDATA`

`x:Code`nie jest dozwolone dla wszystkich możliwych mechanizmów wdrażania produkcji XAML. W określonych ramach (na przykład WPF) kod musi być skompilowany. W innych ramach `x:Code` użycie może być ogólnie niedozwolone.

Dla struktur, które `x:Code` zezwalają na zawartość zarządzaną kompilatora poprawnego języka do użycia dla `x:Code` zawartości jest określana przez ustawienia i obiekty docelowe zawierającego projektu, który jest używany do kompilowania aplikacji.

## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF

Kod zadeklarowany w ramach `x:Code` WPF ma kilka znaczących ograniczeń:

- Element `x:Code` dyrektywy musi być bezpośrednim elementem podrzędnym elementu głównego produkcji XAML.

- [x:Dyrektywa klasy](xclass-directive.md) musi być podana w nadrzędnym elemencie głównym.

- Kod umieszczony `x:Code` w zostaną potraktowane przez kompilację, aby mieszcząć się w zakresie klasy częściowej, która jest już tworzona dla tej strony XAML. W związku z tym cały kod, który definiujesz musi być członkami lub zmienne tej klasy częściowej.

- Nie można zdefiniować dodatkowych klas, innych niż zagnieżdżanie klasy wewnątrz klasy częściowej (zagnieżdżanie jest dozwolone, ale nie jest typowe, ponieważ nie można odwoływać się do klas zagnieżdżonych w XAML). Nie można zdefiniować ani dodać do innych obszarów nazw clr innych niż obszar nazw używany dla istniejącej klasy częściowej.

- Odwołania do jednostek kodu poza obszarem nazw klasy częściowej CLR muszą być w pełni kwalifikowane. Jeśli elementy członkowskie są zadeklarowane są zastąpienia częściowej klasy nadrzędnych elementów członkowskich, to musi być określona za pomocą słowa kluczowego zastąpienia specyficzne dla języka. Jeśli elementy `x:Code` członkowskie zadeklarowane w zakresie są w konflikcie z członkami klasy częściowej utworzonej z XAML, w taki sposób, że kompilator zgłasza konflikt, plik XAML nie może skompilować ani załadować.

## <a name="see-also"></a>Zobacz też

- [x:Class — dyrektywa](xclass-directive.md)
- [Związane z kodem i XAML w WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Omówienie XAML (WPF)](../fundamentals/xaml.md)
