---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: c45559042231b72ef1ba892cabbead03797df8e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642518"
---
# <a name="overflow-visual-basic-run-time-error"></a>Przepełnienie (błąd czasu wykonywania w Visual Basic)
Przepełnienie powoduje podczas próby przypisania przekracza limit przydziału docelowego.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wyniki typu przypisania, obliczeń i danych konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisać wartość do zmiennej typu może przechowywać w większym zakresie wartości , jeśli to konieczne.  
  
2.  Upewnij się, że właściwości dopasowana do zakresu właściwości, do którego zostały wprowadzone.  
  
3.  Upewnij się, że numerów używanych w obliczeniach, są zmuszone do liczb całkowitych, które nie mają wyniki większy niż liczb całkowitych.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Int32.MaxValue?displayProperty=nameWithType>
- <xref:System.Double.MaxValue?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
