---
title: Zestaw
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
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351647"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="fa6af-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa6af-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="fa6af-103">Określa, że atrybut na początku pliku źródłowego dotyczy całego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fa6af-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa6af-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa6af-104">Remarks</span></span>  
 <span data-ttu-id="fa6af-105">Wiele atrybutów odnosi się do pojedynczego elementu programistycznego, takiego jak Klasa lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="fa6af-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="fa6af-106">Ten atrybut jest stosowany przez dołączenie bloku atrybutu w nawiasach kątowych (`< >`) bezpośrednio do instrukcji deklaracji.</span><span class="sxs-lookup"><span data-stu-id="fa6af-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="fa6af-107">Jeśli atrybut dotyczy nie tylko następującego elementu, ale do całego zestawu, umieścisz blok atrybutu na początku pliku źródłowego i zidentyfikujesz atrybut za pomocą słowa kluczowego `Assembly`.</span><span class="sxs-lookup"><span data-stu-id="fa6af-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="fa6af-108">Jeśli dotyczy bieżącego modułu zestawu, należy użyć słowa kluczowego [modułu](../../../visual-basic/language-reference/modifiers/module-keyword.md) .</span><span class="sxs-lookup"><span data-stu-id="fa6af-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="fa6af-109">Można również zastosować atrybut do zestawu w pliku AssemblyInfo. vb, w tym przypadku nie trzeba używać bloku atrybutu w głównym pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="fa6af-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6af-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa6af-110">See also</span></span>

- [<span data-ttu-id="fa6af-111">> \<modułu</span><span class="sxs-lookup"><span data-stu-id="fa6af-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="fa6af-112">Przegląd atrybutów</span><span class="sxs-lookup"><span data-stu-id="fa6af-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
