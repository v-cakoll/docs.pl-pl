---
title: AddressOf — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 098ca95687d8b0e9f4ac90d5c7e0df9a9a0ad950
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760377"
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="c307a-102">AddressOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c307a-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="c307a-103">Tworzy wystąpienie delegata, który odwołuje się do określonej procedury.</span><span class="sxs-lookup"><span data-stu-id="c307a-103">Creates a delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c307a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c307a-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="c307a-105">Części</span><span class="sxs-lookup"><span data-stu-id="c307a-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="c307a-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="c307a-106">Required.</span></span> <span data-ttu-id="c307a-107">Określa procedurę, aby odwoływać się do nowo utworzonego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="c307a-107">Specifies the procedure to be referenced by the newly created delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c307a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c307a-108">Remarks</span></span>  
 <span data-ttu-id="c307a-109">`AddressOf` Operatora, tworzy delegata, który wskazuje na sub lub funkcji określonej przez `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="c307a-109">The `AddressOf` operator creates a delegate that points to the sub or function specified by `procedurename`.</span></span> <span data-ttu-id="c307a-110">Gdy określonej procedury jest metodą wystąpienia następnie delegata odwołuje się do wystąpienia i metody.</span><span class="sxs-lookup"><span data-stu-id="c307a-110">When the specified procedure is an instance method then the delegate refers to both the instance and the method.</span></span> <span data-ttu-id="c307a-111">Następnie gdy obiekt delegowany jest wywoływany określonej metody określone wystąpienie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c307a-111">Then, when the  delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="c307a-112">`AddressOf` Operator może służyć jako argument konstruktora delegata lub mogą być używane w kontekście, w którym można określić typ delegata przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="c307a-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c307a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c307a-113">Example</span></span>  
 <span data-ttu-id="c307a-114">W tym przykładzie użyto `AddressOf` operatora, aby wyznaczyć delegata do obsługi `Click` zdarzenia przycisku.</span><span class="sxs-lookup"><span data-stu-id="c307a-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="c307a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c307a-115">Example</span></span>  
 <span data-ttu-id="c307a-116">W poniższym przykładzie użyto `AddressOf` operatora, aby wyznaczyć funkcji uruchamiania wątku.</span><span class="sxs-lookup"><span data-stu-id="c307a-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c307a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c307a-117">See also</span></span>

- [<span data-ttu-id="c307a-118">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c307a-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="c307a-119">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c307a-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c307a-120">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c307a-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c307a-121">Delegaty</span><span class="sxs-lookup"><span data-stu-id="c307a-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
