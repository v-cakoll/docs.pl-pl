---
title: Instrukcja nie może kończyć bloku poza instrukcją „If” wiersza
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400321"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a>Instrukcja nie może kończyć bloku poza instrukcją „If” wiersza
Jednowierszowa `If` instrukcja zawiera kilka instrukcji rozdzielonych średnikami (:), z których jedna jest `End` instrukcją dla bloku sterowania poza linią jednowierszową `If` . Instrukcje jednowierszowe `If` nie używają `End If` instrukcji.  
  
 **Identyfikator błędu:** BC32005  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Przenieś instrukcję jednowierszową `If` poza blok sterowania, który zawiera `End If` instrukcję.  
  
## <a name="see-also"></a>Zobacz też

- [If...Then...Else, instrukcja](../statements/if-then-else-statement.md)
