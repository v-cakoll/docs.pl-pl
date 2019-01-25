---
title: '&#39;Jako&#39; nie jest obsługiwana w &#39;Declare&#39; instrukcji'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 560ddc8674718f98f3e1a2f6d4facdb198f5e506
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709865"
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="9d419-102">&#39;Jako&#39; nie jest obsługiwana w &#39;Declare&#39; instrukcji</span><span class="sxs-lookup"><span data-stu-id="9d419-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="9d419-103">`Any` — Typ danych był używany z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na korzystanie z argumentów, które mogą zawierać dowolny typ danych.</span><span class="sxs-lookup"><span data-stu-id="9d419-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="9d419-104">Obsługa języka Visual Basic przeciążenia, jednak i sprawia, że tak `Any` przestarzały typ danych.</span><span class="sxs-lookup"><span data-stu-id="9d419-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="9d419-105">**Identyfikator błędu:** BC30828</span><span class="sxs-lookup"><span data-stu-id="9d419-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d419-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9d419-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9d419-107">Można deklarować parametrów określonego typu, którego chcesz użyć. na przykład.</span><span class="sxs-lookup"><span data-stu-id="9d419-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="9d419-108">Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` oczekuje przez tę procedurę, wywoływana.</span><span class="sxs-lookup"><span data-stu-id="9d419-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9d419-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d419-109">See also</span></span>
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="9d419-110">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9d419-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="9d419-111">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9d419-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="9d419-112">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="9d419-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
