---
title: "Stop — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
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
 [End — instrukcja](../../../visual-basic/language-reference/statements/end-statement.md)
