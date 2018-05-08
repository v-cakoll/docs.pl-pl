---
title: Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja
Jeden wiersz `If` instrukcji zawiera wiele instrukcji oddzielone dwukropkiem (:), z których jeden jest `End` instrukcji dla bloków sterowania poza jeden wiersz `If`. Jednowierszowe `If` nie należy używać instrukcji `End If` instrukcji.  
  
 **Identyfikator błędu:** BC32005  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś jeden wiersz `If` instrukcji poza blokiem formant, który zawiera `End If` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [If...Then...Else, instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
