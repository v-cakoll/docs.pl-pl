---
title: Unicode
ms.date: 07/20/2015
f1_keywords:
- vb.Unicode
helpviewer_keywords:
- Unicode, external references
- Declare statement [Visual Basic], marshaling strings
- Unicode keyword [Visual Basic]
- Unicode, marshaling strings
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
ms.openlocfilehash: c4286ed9e9d5fd768ae29b7050b3d1505ccca9dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344222"
---
# <a name="unicode-visual-basic"></a><span data-ttu-id="7b632-102">Unicode (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b632-102">Unicode (Visual Basic)</span></span>
<span data-ttu-id="7b632-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span><span class="sxs-lookup"><span data-stu-id="7b632-103">Specifies that Visual Basic should marshal all strings to Unicode values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="7b632-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span><span class="sxs-lookup"><span data-stu-id="7b632-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have in order to call the procedure correctly.</span></span> <span data-ttu-id="7b632-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span><span class="sxs-lookup"><span data-stu-id="7b632-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="7b632-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span><span class="sxs-lookup"><span data-stu-id="7b632-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="7b632-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span><span class="sxs-lookup"><span data-stu-id="7b632-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information to marshal strings during a call to the external procedure.</span></span> <span data-ttu-id="7b632-108">It also affects how Visual Basic searches the external file for the external procedure name.</span><span class="sxs-lookup"><span data-stu-id="7b632-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="7b632-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span><span class="sxs-lookup"><span data-stu-id="7b632-109">The `Unicode` modifier specifies that Visual Basic should marshal all strings to Unicode values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="7b632-110">If no character set modifier is specified, `Ansi` is the default.</span><span class="sxs-lookup"><span data-stu-id="7b632-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b632-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b632-111">Remarks</span></span>  
 <span data-ttu-id="7b632-112">The `Unicode` modifier can be used in this context:</span><span class="sxs-lookup"><span data-stu-id="7b632-112">The `Unicode` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7b632-113">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7b632-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="7b632-114">Uwagi dla deweloperów inteligentnych urządzeń</span><span class="sxs-lookup"><span data-stu-id="7b632-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="7b632-115">This keyword is not supported.</span><span class="sxs-lookup"><span data-stu-id="7b632-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b632-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b632-116">See also</span></span>

- [<span data-ttu-id="7b632-117">Ansi</span><span class="sxs-lookup"><span data-stu-id="7b632-117">Ansi</span></span>](../../../visual-basic/language-reference/modifiers/ansi.md)
- [<span data-ttu-id="7b632-118">Auto</span><span class="sxs-lookup"><span data-stu-id="7b632-118">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)
- [<span data-ttu-id="7b632-119">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="7b632-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
