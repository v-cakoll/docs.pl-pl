---
title: "&#39; Moduł &#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30617
- vbc30617
helpviewer_keywords: BC30617
ms.assetid: 5e9de8e5-d26b-4fb2-9e28-814413fe9cef
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 61fe12fbd7d20e6cd2b6bc464e7fc3293150213b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39module39-statements-can-occur-only-at-file-or-namespace-level"></a><span data-ttu-id="8cf81-102">&#39; Moduł &#39; instrukcje mogą wystąpić tylko na poziomie pliku lub przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="8cf81-102">&#39;Module&#39; statements can occur only at file or namespace level</span></span>
<span data-ttu-id="8cf81-103">`Module`Instrukcje muszą występować na początku pliku źródłowego natychmiast po `Option` i `Imports` instrukcje, atrybutami globalnymi i deklaracje przestrzeni nazw, ale przed wszystkimi innymi deklaracjami.</span><span class="sxs-lookup"><span data-stu-id="8cf81-103">`Module` statements must appear at the top of your source file immediately after `Option` and `Imports` statements, global attributes, and namespace declarations, but before all other declarations.</span></span>  
  
 <span data-ttu-id="8cf81-104">**Identyfikator błędu:** BC30617</span><span class="sxs-lookup"><span data-stu-id="8cf81-104">**Error ID:** BC30617</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8cf81-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8cf81-105">To correct this error</span></span>  
  
-   <span data-ttu-id="8cf81-106">Przenieś `Module` instrukcji na początku pliku deklaracji ani źródła przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8cf81-106">Move the `Module` statement to the top of your namespace declaration or source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf81-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cf81-107">See Also</span></span>  
 [<span data-ttu-id="8cf81-108">Module — instrukcja</span><span class="sxs-lookup"><span data-stu-id="8cf81-108">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
