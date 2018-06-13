---
title: Struktura &#39; &lt;structurename&gt; &#39; musi zawierać co najmniej jedno wystąpienie zmiennej członkowskiej lub co najmniej jedno wystąpienie deklaracja zdarzenia nie jest oznaczony &#39;niestandardowe&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594503"
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Struktura &#39; &lt;structurename&gt; &#39; musi zawierać co najmniej jedno wystąpienie zmiennej członkowskiej lub co najmniej jedno wystąpienie deklaracja zdarzenia nie jest oznaczony &#39;niestandardowe&#39;
Definicji struktury nie zawiera żadnych zmiennych udostępniana lub udostępniana standardowych zdarzeń.  
  
 Co struktura musi mieć zmiennej lub zdarzenie, które ma zastosowanie do każdego wystąpienia określonych (udostępniana), a nie do wszystkich wystąpień zbiorczo ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)). Stałe udostępniana, właściwości i procedury nie spełniają to wymaganie. Ponadto, jeśli istnieją żadnych udostępniana zmiennych i tylko jedno zdarzenie udostępniana, zdarzenie nie może być `Custom` zdarzeń.  
  
 **Identyfikator błędu:** BC30941  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdefiniuj co najmniej jedną zmienną lub zdarzenie, które nie jest `Shared`. Po zdefiniowaniu tylko jedno zdarzenie musi być standardowych, jak również udostępniana.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Instrukcje: deklarowanie struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
