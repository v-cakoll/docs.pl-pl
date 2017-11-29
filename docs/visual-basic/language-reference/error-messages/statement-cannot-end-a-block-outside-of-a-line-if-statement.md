---
title: "Instrukcja nie może kończyć bloku poza linię &#39; Jeśli &#39; — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords: BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73fe3eb44e904366db7d505bbe8c5fef461eb78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a>Instrukcja nie może kończyć bloku poza linię &#39; Jeśli &#39; — Instrukcja
Jeden wiersz `If` instrukcji zawiera wiele instrukcji oddzielone dwukropkiem (:), z których jeden jest `End` instrukcji dla bloków sterowania poza jeden wiersz `If`. Jednowierszowe `If` nie należy używać instrukcji `End If` instrukcji.  
  
 **Identyfikator błędu:** BC32005  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Przenieś jeden wiersz `If` instrukcji poza blokiem formant, który zawiera `End If` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [IF... Następnie... Else — instrukcja](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
