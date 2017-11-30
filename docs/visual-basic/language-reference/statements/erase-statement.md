---
title: "Erase — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a>Erase — Instrukcja (Visual Basic)
Używane do zwalniania zmiennych tablicowych i cofnięcia przydzielenia pamięci używanej dla elementów.  
  
## <a name="syntax"></a>Składnia  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Części  
 `arraylist`  
 Wymagany. Lista zmiennych tablicowych usunięcie. Wiele zmiennych są oddzielone przecinkami.  
  
## <a name="remarks"></a>Uwagi  
 `Erase` Instrukcja może wystąpić tylko na poziomie procedury. Oznacza to, że można zwolnić tablice wewnątrz procedury, ale nie na poziomie klasę lub moduł.  
  
 `Erase` Instrukcja jest odpowiednikiem przypisywanie `Nothing` do każdej zmiennej tablicy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Erase` instrukcji, aby wyczyścić dwiema tablicami i zwolnić pamięć, ich (1000 i 100 elementów magazynu odpowiednio). `ReDim` Instrukcji następnie przypisuje nowego wystąpienia tablicy tablicą trójwymiarową.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [ReDim — instrukcja](../../../visual-basic/language-reference/statements/redim-statement.md)
