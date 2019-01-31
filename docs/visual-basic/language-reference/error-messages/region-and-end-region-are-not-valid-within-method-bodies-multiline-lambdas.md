---
title: Instrukcje "#Region" i "#End Region" nie są prawidłowe w metod treści wielowierszowych wyrażeń lambda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 2a2f5692518c6784dfc6e3be6302f1e8dcf2aaa7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265574"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>Instrukcje „#Region” i „#End Region” nie są prawidłowe w treści metod/wielowierszowych wyrażeń lambda
`#Region` Bloku musi być zadeklarowany na poziomie klasy, modułu lub przestrzeni nazw. Region zwijany może zawierać jedną lub kilkoma procedurami, ale go nie może rozpoczynać się ani kończyć się wewnątrz procedury.  
  
 **Identyfikator błędu:** BC32025  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że poprzedniej procedury prawidłowo jest kończony przy użyciu `End Function` lub `End Sub` instrukcji.  
  
2.  Upewnij się, że `#Region` i `#End Region` dyrektywy znajdują się w tym samym bloku kodu.  
  
## <a name="see-also"></a>Zobacz także
- [#Region, dyrektywa](../../../visual-basic/language-reference/directives/region-directive.md)
