---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="2bf38-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bf38-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="2bf38-103">Określa, że atrybut znajdujący się na początku pliku źródłowego dotyczy całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bf38-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bf38-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2bf38-104">Remarks</span></span>  
 <span data-ttu-id="2bf38-105">Wiele atrybutów odnoszą się do pojedynczego elementu programistycznego, takiego jak klasa lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="2bf38-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="2bf38-106">Zastosuj takiego atrybutu dołączając bloku atrybutów w nawiasy (`< >`), bezpośrednio do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="2bf38-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="2bf38-107">Jeśli atrybut dotyczy nie tylko do następującego elementu, ale do całego zestawu, umieść bloku attribute na początku pliku źródłowego i określenie atrybutu o `Assembly` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2bf38-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="2bf38-108">Jeśli ma to zastosowanie do bieżącego zestawu modułu, użyj [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2bf38-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="2bf38-109">Można również zastosować atrybut do zestawu w pliku AssemblyInfo.vb w takim przypadku nie trzeba w pliku głównym kodu źródłowego przy użyciu bloku atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2bf38-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf38-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bf38-110">See Also</span></span>  
 [<span data-ttu-id="2bf38-111">Moduł \<— słowo kluczowe ></span><span class="sxs-lookup"><span data-stu-id="2bf38-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="2bf38-112">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="2bf38-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

