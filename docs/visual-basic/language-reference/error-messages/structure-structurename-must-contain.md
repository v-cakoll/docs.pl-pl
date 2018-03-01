---
title: "Struktura &#39; &lt;structurename&gt;&#39; musi zawierać co najmniej jedno wystąpienie zmiennej członkowskiej lub co najmniej jedno wystąpienie deklaracja zdarzenia nie jest oznaczony &#39; Niestandardowe &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Struktura &#39; &lt;structurename&gt;&#39; musi zawierać co najmniej jedno wystąpienie zmiennej członkowskiej lub co najmniej jedno wystąpienie deklaracja zdarzenia nie jest oznaczony &#39; Niestandardowe &#39;
Definicji struktury nie zawiera żadnych zmiennych udostępniana lub udostępniana standardowych zdarzeń.  
  
 Co struktura musi mieć zmiennej lub zdarzenie, które ma zastosowanie do każdego wystąpienia określonych (udostępniana), a nie do wszystkich wystąpień zbiorczo ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)). Stałe udostępniana, właściwości i procedury nie spełniają to wymaganie. Ponadto, jeśli istnieją żadnych udostępniana zmiennych i tylko jedno zdarzenie udostępniana, zdarzenie nie może być `Custom` zdarzeń.  
  
 **Identyfikator błędu:** BC30941  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zdefiniuj co najmniej jedną zmienną lub zdarzenie, które nie jest `Shared`. Po zdefiniowaniu tylko jedno zdarzenie musi być standardowych, jak również udostępniana.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Porady: deklarowanie struktury](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)
