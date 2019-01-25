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
ms.openlocfilehash: 74fcc158c0556b85ac5175584fa4948513c69053
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641112"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code — Typ funkcji XAML
Umożliwia umieszczanie kodu w ramach produkcji XAML. Taki kod może być kompilowane albo przez dowolnego implementacji procesora XAML, który kompiluje XAML lub po lewej stronie w środowisku produkcyjnym XAML do nowszych zastosowań, takich jak interpretacji przez środowisko uruchomieniowe.  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod w `x:Code` element dyrektywy XAML jest nadal interpretowany w głównej przestrzeni nazw XML i przestrzenie nazw XAML, pod warunkiem. Dlatego jest zazwyczaj konieczne dołączyć kod umożliwiający `x:Code` wewnątrz `CDATA` segmentu.  
  
 `x:Code` nie jest dozwolony dla wszystkich mechanizmów możliwe wdrożenie produkcyjne XAML. W określonych platform (na przykład WPF) musi zostać skompilowany kod. W innych platform tworzenia `x:Code` użycia może być zwykle niedozwolone.  
  
 Dla platform zezwalające na zarządzanych `x:Code` zawartości kompilatora języka do użycia dla `x:Code` zawartość jest określana przez ustawienia i elementy docelowe projektu zawierającego, który służy do kompilowania aplikacji.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użytkowania WPF  
 Kod zadeklarowane wewnątrz `x:Code` WPF ma kilka znaczące ograniczenia:  
  
-   `x:Code` Dyrektywy element musi być natychmiastowe podrzędnym elementem głównym elementem produkcji XAML.  
  
-   [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md) musi być podana w elemencie głównym nadrzędnej.  
  
-   Kod umieszczony w `x:Code` są traktowani kompilacji w zakresie częściową klasą, która jest już utworzony dla tej strony XAML. W związku z tym cały kod, który zdefiniujesz musi być członków lub zmiennych tej klasy częściowej.  
  
-   Nie można zdefiniować dodatkowe klasy, inne niż przez zagnieżdżanie klasy wewnątrz klasy częściowe (zagnieżdżanie jest dozwolone, ale nie jest typowym ponieważ klasy zagnieżdżone nie może być przywoływany w XAML). Przestrzeni nazw CLR innych niż przestrzeń nazw, która jest używana dla istniejącej klasy częściowe nie może być zdefiniowany ani dodawane do.  
  
-   Odwołania do jednostek kodu poza przestrzeń nazw środowiska CLR klasy częściowej wszystkie muszą być w pełni kwalifikowana. Jeśli elementy członkowskie deklarowanej zastąpień do przesłonięcia elementów członkowskich klasy częściowej, to można określić za pomocą słowa kluczowego override specyficzny dla języka. W przypadku elementów członkowskich zadeklarowanych w `x:Code` zakres elementów członkowskich klasy częściowej utworzony poza XAML różne, w taki sposób, że kompilator zgłasza konfliktu, plik XAML nie można skompilować lub obciążenia.  
  
## <a name="see-also"></a>Zobacz także
- [x:Class, dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)
- [Plik codebehind i XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
