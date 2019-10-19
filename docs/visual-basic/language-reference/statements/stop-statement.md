---
title: Stop — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: e9382ee34842fc3a3b4b23f71848bda602c99780
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583225"
---
# <a name="stop-statement-visual-basic"></a>Stop — Instrukcja (Visual Basic)
Wstrzymuje wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcje `Stop` można umieścić w dowolnym miejscu w procedurach, aby wstrzymać wykonywanie. Użycie instrukcji `Stop` jest podobne do ustawiania punktu przerwania w kodzie.  
  
 Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End`, nie zamyka żadnych plików ani nie czyści żadnych zmiennych, chyba że zostanie napotkana w skompilowanym pliku wykonywalnym (. exe).  
  
> [!NOTE]
> Jeśli instrukcja `Stop` występuje w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), debuger jest wywoływany. Ta wartość jest prawdziwa niezależnie od tego, czy kod został skompilowany w trybie debugowania czy sprzedaży detalicznej.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa instrukcji `Stop`, aby zawiesić wykonywanie dla każdej iteracji za pośrednictwem pętli `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Zobacz także

- [End, instrukcja](../../../visual-basic/language-reference/statements/end-statement.md)
