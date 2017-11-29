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
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="a7f6a-102">Instrukcja nie może kończyć bloku poza linię &#39; Jeśli &#39; — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="a7f6a-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="a7f6a-103">Jeden wiersz `If` instrukcji zawiera wiele instrukcji oddzielone dwukropkiem (:), z których jeden jest `End` instrukcji dla bloków sterowania poza jeden wiersz `If`.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="a7f6a-104">Jednowierszowe `If` nie należy używać instrukcji `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="a7f6a-105">**Identyfikator błędu:** BC32005</span><span class="sxs-lookup"><span data-stu-id="a7f6a-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7f6a-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a7f6a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="a7f6a-107">Przenieś jeden wiersz `If` instrukcji poza blokiem formant, który zawiera `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a7f6a-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7f6a-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7f6a-108">See Also</span></span>  
 [<span data-ttu-id="a7f6a-109">IF... Następnie... Else — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a7f6a-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
