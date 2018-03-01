---
title: "Przepełnienie (błąd czasu wykonywania w Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrERRID_Overflow
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1908ad576a499e79102aff23e3e2f11d7d99d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Error — typy](../../../visual-basic/programming-guide/language-features/error-types.md)
