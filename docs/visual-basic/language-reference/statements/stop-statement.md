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
ms.openlocfilehash: 955a3b6a2f7dc1d0e9823ed6d500ab7f7f9fe5b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599138"
---
# <a name="stop-statement-visual-basic"></a>Stop — Instrukcja (Visual Basic)
Wstrzymuje wykonywanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Uwagi  
 Możesz umieścić `Stop` instrukcje w dowolnym miejscu procedury, aby wstrzymać wykonywania. Przy użyciu `Stop` instrukcji jest podobne do punktu przerwania w kodzie.  
  
 `Stop` Instrukcji wstrzymuje wykonywanie, lecz w przeciwieństwie do `End`, zamknij wszystkie pliki lub nie wyczyść wszystkie zmienne, chyba że jest wystąpił w pliku skompilowanego pliku wykonywalnego (.exe).  
  
> [!NOTE]
>  Jeśli `Stop` napotkano instrukcji w kodzie, który działa poza zintegrowane środowisko programistyczne (IDE), Debuger jest wywoływany. Dotyczy to niezależnie od tego, czy kod został skompilowany w trybie debugowania lub wersji detalicznej.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto `Stop` instrukcji, aby wstrzymać wykonywania dla każdej iteracji za pośrednictwem `For...Next` pętli.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [End Statement](../../../visual-basic/language-reference/statements/end-statement.md)
