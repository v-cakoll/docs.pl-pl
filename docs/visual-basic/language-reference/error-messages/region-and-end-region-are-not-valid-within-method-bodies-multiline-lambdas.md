---
title: Instrukcje "#Region" i "#End Region" nie są prawidłowe w metod treści wielowierszowych wyrażeń lambda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: deef3de645040d7c3d95b1a6c8a25fcf10de881b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842710"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Instrukcje „#Region” i „#End Region” nie są prawidłowe w treści metod/wielowierszowych wyrażeń lambda
`#Region` Bloku musi być zadeklarowany na poziomie klasy, modułu lub przestrzeni nazw. Region zwijany może zawierać jedną lub kilkoma procedurami, ale go nie może rozpoczynać się ani kończyć się wewnątrz procedury.  
  
 **Identyfikator błędu:** BC32025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że poprzedniej procedury prawidłowo jest kończony przy użyciu `End Function` lub `End Sub` instrukcji.  
  
2.  Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.  
  
## <a name="see-also"></a>Zobacz także

- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
