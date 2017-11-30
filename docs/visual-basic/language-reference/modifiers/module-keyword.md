---
title: "Moduł &lt;— słowo kluczowe&gt; (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1d35ad332229785f8cac76bd8099bccc85c3d3cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="module-ltkeywordgt-visual-basic"></a><span data-ttu-id="17d62-102">Moduł &lt;— słowo kluczowe&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17d62-102">Module &lt;keyword&gt; (Visual Basic)</span></span>
<span data-ttu-id="17d62-103">Określa, że atrybut znajdujący się na początku pliku źródłowego dotyczy bieżącego modułu zestawu.</span><span class="sxs-lookup"><span data-stu-id="17d62-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d62-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17d62-104">Remarks</span></span>  
 <span data-ttu-id="17d62-105">Wiele atrybutów odnoszą się do pojedynczego elementu programistycznego, takiego jak klasa lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="17d62-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="17d62-106">Zastosuj takiego atrybutu dołączając bloku atrybutów w nawiasy (`< >`), bezpośrednio do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="17d62-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="17d62-107">Jeśli atrybut dotyczy nie tylko do następującego elementu, ale do bieżącego zestawu modułu, umieść bloku attribute na początku pliku źródłowego i określenie atrybutu o `Module` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="17d62-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="17d62-108">Jeśli ma to zastosowanie do całego zestawu, użyj [zestawu](../../../visual-basic/language-reference/modifiers/assembly.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="17d62-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="17d62-109">`Module` Modyfikator nie jest taka sama jak [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="17d62-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17d62-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="17d62-110">See Also</span></span>  
 [<span data-ttu-id="17d62-111">Zestawu</span><span class="sxs-lookup"><span data-stu-id="17d62-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)  
 [<span data-ttu-id="17d62-112">Module — instrukcja</span><span class="sxs-lookup"><span data-stu-id="17d62-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="17d62-113">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="17d62-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

