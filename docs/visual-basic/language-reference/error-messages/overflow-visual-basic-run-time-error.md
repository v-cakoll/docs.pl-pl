---
title: Przepełnienie (błąd czasu wykonywania w Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
ms.openlocfilehash: 9db79071c4895d49680352bde2d0824a3756d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594178"
---
# <a name="overflow-visual-basic-run-time-error"></a>Przepełnienie (błąd czasu wykonywania w Visual Basic)
Przepełnienie powoduje przy próbie przypisanie przekracza limity przydziału docelowej.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że wyniki przypisania, obliczeń i danych typu konwersje nie są zbyt duże, aby mogły być reprezentowane w ramach zakresu dozwolonych dla tego typu wartości zmiennych i przypisuje wartość do zmiennej typu może przechowywać różnego rodzaju wartości , jeśli to konieczne.  
  
2.  Upewnij się, że właściwości mieści się zakresie właściwości, do którego zostały wprowadzone.  
  
3.  Upewnij się, że numery używany w obliczeniach, które są przekształcić na liczby całkowite nie jest większy niż liczb całkowitych wyników.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Int32.MaxValue?displayProperty=nameWithType>  
 <xref:System.Double.MaxValue?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Typy błędów](../../../visual-basic/programming-guide/language-features/error-types.md)
