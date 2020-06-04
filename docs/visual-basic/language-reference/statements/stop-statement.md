---
title: Stop, instrukcja
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
ms.openlocfilehash: 2ef1e2f9045e5509e11557c9fdaf3edd2786b72c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404229"
---
# <a name="stop-statement-visual-basic"></a>Stop — Instrukcja (Visual Basic)
Wstrzymuje wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `Stop` instrukcje w dowolnym miejscu procedury, aby wstrzymać wykonywanie. Użycie `Stop` instrukcji jest podobne do ustawiania punktu przerwania w kodzie.  
  
 `Stop`Instrukcja zawiesza wykonywanie, ale w przeciwieństwie do `End` siebie nie zamyka żadnych plików ani nie czyści żadnych zmiennych, chyba że występuje w skompilowanym pliku wykonywalnym (. exe).  
  
> [!NOTE]
> Jeśli `Stop` instrukcja jest napotkana w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), debuger jest wywoływany. Ta wartość jest prawdziwa niezależnie od tego, czy kod został skompilowany w trybie debugowania czy sprzedaży detalicznej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie używa `Stop` instrukcji, aby wstrzymać wykonywanie dla każdej iteracji za pośrednictwem `For...Next` pętli.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Zobacz też

- [End — instrukcja](end-statement.md)
