---
title: Instrukcje "#Region" i "#End Region" nie są prawidłowe w metod treści wielowierszowych wyrażeń lambda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: c41b95da7e3565ae7aaf332fe49361336e79f7c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303911"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Instrukcje „#Region” i „#End Region” nie są prawidłowe w treści metod/wielowierszowych wyrażeń lambda
`#Region` Bloku musi być zadeklarowany na poziomie klasy, modułu lub przestrzeni nazw. Region zwijany może zawierać jedną lub kilkoma procedurami, ale go nie może rozpoczynać się ani kończyć się wewnątrz procedury.  
  
 **Identyfikator błędu:** BC32025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że poprzedniej procedury prawidłowo jest kończony przy użyciu `End Function` lub `End Sub` instrukcji.  
  
2. Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.  
  
## <a name="see-also"></a>Zobacz także

- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
