---
title: Instrukcja nie może kończyć bloku poza instrukcją „If” wiersza
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 0e645ccf17d0aba702a576791622aa4e9b3dd5e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593267"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Instrukcja nie może kończyć bloku poza instrukcją „If” wiersza
Jeden wiersz `If` instrukcja zawiera kilka instrukcji oddzielone dwukropkiem (:), z których jedna jest `End` instrukcji w bloku kontroli, poza jednym wierszem `If`. Jeden wiersz `If` nie należy używać instrukcji `End If` instrukcji.  
  
 **Identyfikator błędu:** BC32005  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Przenieś jeden wiersz `If` instrukcji poza blok sterowania, który zawiera `End If` instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- [Dyrektywa #If...Then...#Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
