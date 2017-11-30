---
title: "x:Code — Typ funkcji XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
caps.latest.revision: "19"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: d1b21e2a654b18547c8da7da724c87946724f71f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code — Typ funkcji XAML
Umożliwia umieszczanie kod w produkcji XAML. Taki kod albo mogą być kompilowane przez kompilowany XAML, lub do lewej w środowisku produkcyjnym XAML dla nowszej zastosowań, takich jak interpretacji przez środowisko uruchomieniowe implementacji procesora XAML.  
  
## <a name="xaml-object-element-usage"></a>Użycie elementu obiektu języka XAML  
  
```  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod w `x:Code` element dyrektywy XAML jest nadal interpretowana w głównej przestrzeni nazw XML i przestrzeni nazw XAML, pod warunkiem. W związku z tym jest zazwyczaj konieczne do kod używany do `x:Code` wewnątrz `CDATA` segmentu.  
  
 `x:Code`nie jest dozwolona dla wszystkich mechanizmów wdrażania produkcji XAML. W określonych platform (na przykład WPF) musi być skompilowany kod. W innych platform `x:Code` obciążenie może być zwykle niedozwolone.  
  
 Dla struktur, pozwalające zarządzanych `x:Code` zawartości kompilatora właściwy język do użycia na potrzeby `x:Code` zawartości jest określany przez ustawienia i elementy docelowe projektu zawierającego, która jest używana do kompilowania aplikacji.  
  
## <a name="wpf-usage-notes"></a>Uwagi dotyczące użycia WPF  
 Kod zadeklarowana wewnątrz `x:Code` WPF ma kilka istotnych ograniczenia:  
  
-   `x:Code` Dyrektywy element musi być elementem podrzędnym natychmiastowego elementu głównego XAML produkcji.  
  
-   [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md) należy podać dla nadrzędnego elementu głównego.  
  
-   Kod umieszczony `x:Code` , będą traktowane w kompilacji muszą mieścić się w zakresie częściowej klasy, która została właśnie utworzona dla tej strony XAML. W związku z tym całego kodu, który należy zdefiniować musi być elementów członkowskich lub zmienne dla tej klasy częściowej.  
  
-   Nie można zdefiniować dodatkowe klasy, innych niż zagnieżdżanie klasy wewnątrz klasy częściowej (zagnieżdżanie jest dozwolone, ale nie jest typowe ponieważ zagnieżdżonych klas nie może być przywoływany w języku XAML). Przestrzenie nazw CLR innych niż przestrzeni nazw, która jest używana dla istniejącej klasy częściowe nie może być zdefiniowany ani dodawane do.  
  
-   Odwołania do jednostek kodu poza przestrzeń nazw środowiska CLR klasy częściowej muszą być wszystkie FQDN. Elementy członkowskie został zadeklarowany w przypadku zastąpienia do klasy częściowej członków możliwym do zastąpienia, to należy określić przy użyciu słowa kluczowego override specyficzny dla języka. Elementy członkowskie zadeklarowana w `x:Code` zakresu powodują konflikt z członkami klasy częściowej utworzony poza XAML, w taki sposób, że kompilator zgłasza konfliktu, plik XAML nie można skompilować lub obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [x: Class — dyrektywa](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Związane z kodem i języka XAML w WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)  
 [Omówienie XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
