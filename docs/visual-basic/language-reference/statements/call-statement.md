---
title: Call, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.Call
helpviewer_keywords:
- procedures [Visual Basic], Call statement
- Call statement [Visual Basic]
- procedures [Visual Basic], calling
ms.assetid: e5b31571-6867-406f-b8e7-a3f9aae4723a
ms.openlocfilehash: 7de194ea23827e08c49f4519c1000708a4bd91b4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350161"
---
# <a name="call-statement-visual-basic"></a><span data-ttu-id="85f89-102">Call — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85f89-102">Call Statement (Visual Basic)</span></span>

<span data-ttu-id="85f89-103">Przenosi formant do procedury `Function`, `Sub`lub biblioteki dołączanej dynamicznie (DLL).</span><span class="sxs-lookup"><span data-stu-id="85f89-103">Transfers control to a `Function`, `Sub`, or dynamic-link library (DLL) procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85f89-104">Syntax</span></span>  
  
```vb  
[ Call ] procedureName [ (argumentList) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="85f89-105">Części</span><span class="sxs-lookup"><span data-stu-id="85f89-105">Parts</span></span>  

|||
|---|---|
|`procedureName`|<span data-ttu-id="85f89-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="85f89-106">Required.</span></span> <span data-ttu-id="85f89-107">Nazwa procedury do wywołania.</span><span class="sxs-lookup"><span data-stu-id="85f89-107">Name of the procedure to call.</span></span>|
|`argumentList`|<span data-ttu-id="85f89-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="85f89-108">Optional.</span></span> <span data-ttu-id="85f89-109">Lista zmiennych lub wyrażeń reprezentujących argumenty, które są przekazane do procedury po wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="85f89-109">List of variables or expressions representing arguments that are passed to the procedure when it is called.</span></span> <span data-ttu-id="85f89-110">Wiele argumentów jest oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="85f89-110">Multiple arguments are separated by commas.</span></span> <span data-ttu-id="85f89-111">Jeśli dołączysz `argumentList`, musisz ująć ją w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="85f89-111">If you include `argumentList`, you must enclose it in parentheses.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="85f89-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85f89-112">Remarks</span></span>

 <span data-ttu-id="85f89-113">Po wywołaniu procedury można użyć słowa kluczowego `Call`.</span><span class="sxs-lookup"><span data-stu-id="85f89-113">You can use the `Call` keyword when you call a procedure.</span></span> <span data-ttu-id="85f89-114">W większości wywołań procedur użycie tego słowa kluczowego nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="85f89-114">For most procedure calls, you aren’t required to use this  keyword.</span></span>

 <span data-ttu-id="85f89-115">Zwykle używasz słowa kluczowego `Call`, gdy wywoływane wyrażenie nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="85f89-115">You typically use the `Call` keyword when the called expression doesn’t start with an identifier.</span></span> <span data-ttu-id="85f89-116">Użycie słowa kluczowego `Call` do innych celów nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="85f89-116">Use of the `Call` keyword for other uses isn't recommended.</span></span>

 <span data-ttu-id="85f89-117">Jeśli procedura zwróci wartość, instrukcja `Call` odrzuca ją.</span><span class="sxs-lookup"><span data-stu-id="85f89-117">If the procedure returns a value, the `Call` statement discards it.</span></span>

## <a name="example"></a><span data-ttu-id="85f89-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="85f89-118">Example</span></span>

 <span data-ttu-id="85f89-119">Poniższy kod przedstawia dwa przykłady, w których słowo kluczowe `Call` jest niezbędne do wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="85f89-119">The following code shows two examples where the `Call` keyword is necessary to call a procedure.</span></span> <span data-ttu-id="85f89-120">W obu przykładach wywoływane wyrażenie nie zaczyna się od identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="85f89-120">In both examples, the called expression doesn't start with an identifier.</span></span>

 [!code-vb[VbVbalrStatements#97](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#97)]  
  
## <a name="see-also"></a><span data-ttu-id="85f89-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85f89-121">See also</span></span>

- [<span data-ttu-id="85f89-122">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="85f89-122">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="85f89-123">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="85f89-123">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="85f89-124">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="85f89-124">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="85f89-125">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="85f89-125">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
