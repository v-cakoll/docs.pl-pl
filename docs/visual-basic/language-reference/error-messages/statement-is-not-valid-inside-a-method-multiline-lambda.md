---
title: "Instrukcja nie jest prawidłowa wewnątrz metody wielowierszowego wyrażenia lambda"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords: BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80673fc7a1497b4148a6505d29581c6403115558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Instrukcja nie jest prawidłowa wewnątrz metody/wielowierszowego wyrażenia lambda
Instrukcja nie jest prawidłowy w ramach `Sub`, `Function`, właściwość `Get`, lub właściwości `Set` procedury. Niektóre instrukcji można umieścić na poziomie modułu lub klasy. Inne, takie jak `Option Strict`, musi znajdować się na poziomie przestrzeni nazw i poprzedzać wszystkie inne deklaracje.  
  
 **Identyfikator błędu:** BC30024  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Usuń instrukcji z procedury.  
  
## <a name="see-also"></a>Zobacz też  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Get — instrukcja](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set — instrukcja](../../../visual-basic/language-reference/statements/set-statement.md)
