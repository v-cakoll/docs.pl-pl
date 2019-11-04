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
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459588"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code — Typ funkcji XAML
Umożliwia umieszczanie kodu w środowisku produkcyjnym XAML. Taki kod może być kompilowany przez dowolną implementację procesora XAML, która kompiluje kod XAML lub pozostawioną w środowisku produkcyjnym XAML w celu późniejszego użycia, na przykład interpretacji przez środowisko uruchomieniowe.  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod w `x:Code` elemencie dyrektywy XAML jest nadal interpretowany w ogólnej przestrzeni nazw XML i udostępnionych przestrzeniach nazw XAML. W związku z tym zazwyczaj konieczne jest zawrzeć kod używany do `x:Code` wewnątrz segmentu `CDATA`.  
  
 `x:Code` nie jest dozwolony dla wszystkich możliwych mechanizmów wdrażania w środowisku produkcyjnym XAML. W określonych strukturach (na przykład WPF) kod musi być skompilowany. W innych strukturach użycie `x:Code` może być ogólnie niedozwolone.  
  
 W przypadku struktur, które zezwalają na zawartość zarządzaną `x:Code`, prawidłowy kompilator języka do użycia dla `x:Code` zawartości jest określany przez ustawienia i cele zawierającego projekt, który jest używany do kompilowania aplikacji.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Kod zadeklarowany w `x:Code` dla WPF ma kilka istotnych ograniczeń:  
  
- Element dyrektywy `x:Code` musi być bezpośrednim elementem podrzędnym elementu głównego w środowisku produkcyjnym XAML.  
  
- dla nadrzędnego elementu głównego musi być podana [dyrektywa x:Class](x-class-directive.md) .  
  
- Kod umieszczony w `x:Code` będzie traktowany przez kompilację, aby znajdować się w zakresie klasy częściowej, która jest już utworzona dla tej strony XAML. W związku z tym wszystkie zdefiniowane kody muszą być elementami członkowskimi lub zmiennymi tej klasy częściowej.  
  
- Nie można definiować dodatkowych klas, innych niż zagnieżdżanie klasy wewnątrz klasy częściowej (zagnieżdżanie jest dozwolone, ale nie jest typowe, ponieważ nie można odwoływać się do klas zagnieżdżonych w języku XAML). Przestrzenie nazw CLR inne niż przestrzeń nazw, która jest używana dla istniejącej klasy częściowej, nie mogą być zdefiniowane ani dodawane do.  
  
- Odwołania do jednostek kodu spoza przestrzeni nazw CLR klasy częściowej muszą być w pełni kwalifikowane. Jeśli deklarowane składowe są zastąpienia do składowych klasy częściowej, należy określić za pomocą słowa kluczowego override określonego dla języka. Jeśli elementy członkowskie zadeklarowane w zakresie `x:Code` powodują konflikt z elementami członkowskimi częściowej klasy utworzonej poza XAML, w taki sposób, aby kompilator zgłaszał konflikt, plik XAML nie może kompilować ani ładować.  
  
## <a name="see-also"></a>Zobacz także

- [x:Class, dyrektywa](x-class-directive.md)
- [Plik codebehind i XAML w WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Przegląd XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
