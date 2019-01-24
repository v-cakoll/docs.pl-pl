---
title: Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 78fe136acbd09e202b1daeb16dd540cf42ada390
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574719"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja
Jeden wiersz `If` instrukcja zawiera kilka instrukcji oddzielone dwukropkiem (:), z których jedna jest `End` instrukcji w bloku kontroli, poza jednym wierszem `If`. Jeden wiersz `If` nie należy używać instrukcji `End If` instrukcji.  
  
 **Identyfikator błędu:** BC32005  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś jeden wiersz `If` instrukcji poza blok sterowania, który zawiera `End If` instrukcji.  
  
## <a name="see-also"></a>Zobacz także
- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
