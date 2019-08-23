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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957620"
---
# <a name="stop-statement-visual-basic"></a>Stop — Instrukcja (Visual Basic)
Wstrzymuje wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Uwagi  
 Instrukcję `Stop` można umieścić w dowolnym miejscu procedur, aby wstrzymać ich wykonanie. Użycie instrukcji `Stop` przypomina ustawienie punktu przerwania w kodzie.  
  
 Instrukcja `Stop` wstrzymuje wykonywanie, ale w przeciwieństwie do `End` nie zamyka żadnych plików ani nie czyści żadnych zmiennych — chyba że występuje w skompilowanym pliku wykonywalnym (.exe).  
  
> [!NOTE]
> Jeśli instrukcja `Stop` występuje w kodzie, który działa poza zintegrowanym środowiskiem programistycznym (IDE), wywoływany jest debuger. Stanie się tak niezależnie od tego, czy kod został skompilowany w trybie debugowania, czy wersji wdrożeniowej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto instrukcji `Stop`, aby wstrzymać wykonanie każdej iteracji w pętli `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcja End](../../../visual-basic/language-reference/statements/end-statement.md)
