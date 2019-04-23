---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 63223a815e1c4ff8d4e0afbb6c732fff90aad465
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345550"
---
# <a name="overflow-visual-basic-run-time-error"></a>Przepełnienie (błąd czasu wykonywania w Visual Basic)
Przepełnienie powoduje podczas próby przypisania przekracza limit przydziału docelowego.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Upewnij się, że wyniki typu przypisania, obliczeń i danych konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisać wartość do zmiennej typu może przechowywać w większym zakresie wartości , jeśli to konieczne.  
  
2. Upewnij się, że właściwości dopasowana do zakresu właściwości, do którego zostały wprowadzone.  
  
3. Upewnij się, że numerów używanych w obliczeniach, są zmuszone do liczb całkowitych, które nie mają wyniki większy niż liczb całkowitych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
