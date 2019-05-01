---
title: Module <keyword> (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: f6ded1184aedf1702f4b6e5eebb85709cf8e39f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920708"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="cc175-102">Moduł \<— słowo kluczowe > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc175-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="cc175-103">Określa, że atrybut znajdujący się na początku pliku źródłowego ma zastosowanie do bieżącego zestawu modułu.</span><span class="sxs-lookup"><span data-stu-id="cc175-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc175-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc175-104">Remarks</span></span>  
 <span data-ttu-id="cc175-105">Wiele atrybutów odnoszą się do pojedynczego elementu programistycznego, takiego jak klasa lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="cc175-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="cc175-106">Stosowanie takiego atrybutu, dołączając bloku atrybutów w nawiasach kątowych (`< >`), bezpośrednio do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="cc175-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="cc175-107">Jeśli atrybut dotyczy nie tylko następujący element, ale bieżącego zestawu modułu, można umieścić blok atrybut na początku pliku źródłowego i zidentyfikować atrybut o `Module` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cc175-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="cc175-108">Jeśli ma zastosowanie do całego zestawu, należy użyć [zestawu](../../../visual-basic/language-reference/modifiers/assembly.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="cc175-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="cc175-109">`Module` Modyfikator nie jest taka sama jak [Module — instrukcja](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc175-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc175-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc175-110">See also</span></span>

- [<span data-ttu-id="cc175-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="cc175-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="cc175-112">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="cc175-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="cc175-113">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc175-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
