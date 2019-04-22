---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 819fa9cf1bd25e9426fb1e75925a269fcf7a71cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819258"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="bd1d5-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd1d5-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="bd1d5-103">Określa, że atrybut znajdujący się na początku pliku źródłowego dotyczy całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bd1d5-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd1d5-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd1d5-104">Remarks</span></span>  
 <span data-ttu-id="bd1d5-105">Wiele atrybutów odnoszą się do pojedynczego elementu programistycznego, takiego jak klasa lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="bd1d5-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="bd1d5-106">Stosowanie takiego atrybutu, dołączając bloku atrybutów w nawiasach kątowych (`< >`), bezpośrednio do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="bd1d5-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="bd1d5-107">Jeśli atrybut dotyczy nie tylko do następującego elementu, ale aby cały zespół, umieść bloku attribute na początku pliku źródłowego i określenie atrybutu o `Assembly` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="bd1d5-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="bd1d5-108">Jeśli ma zastosowanie do bieżącego zestawu modułu, należy użyć [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="bd1d5-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="bd1d5-109">Można również zastosować atrybut do zestawu w pliku AssemblyInfo.vb, w którym to przypadku nie trzeba użyć bloku atrybutów w pliku głównym kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="bd1d5-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1d5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd1d5-110">See also</span></span>

- [<span data-ttu-id="bd1d5-111">Module \<słowo kluczowe></span><span class="sxs-lookup"><span data-stu-id="bd1d5-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="bd1d5-112">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd1d5-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
