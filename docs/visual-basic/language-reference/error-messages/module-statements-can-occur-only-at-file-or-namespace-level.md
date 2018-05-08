---
title: '&#39;Moduł&#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw'
ms.date: 07/20/2015
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords:
- BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
ms.openlocfilehash: 53199c2d7081445dc5490d5c54c98f93ee7522eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a>&#39;Moduł&#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw
`Module` Instrukcje muszą występować na początku pliku źródłowego natychmiast po `Option` i `Imports` instrukcje, atrybutami globalnymi i deklaracje przestrzeni nazw, ale przed wszystkimi innymi deklaracjami.  
  
 **Identyfikator błędu:** BC30617  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś `Module` instrukcji na początku pliku deklaracji ani źródła przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)
