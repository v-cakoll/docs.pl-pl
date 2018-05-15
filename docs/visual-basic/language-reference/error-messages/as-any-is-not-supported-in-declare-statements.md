---
title: '&#39;Jako&#39; nie jest obsługiwany w &#39;Declare&#39; — instrukcje'
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 34beaeb7178645d5a167d1b7b969bb3e4f500e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="344ef-102">&#39;Jako&#39; nie jest obsługiwany w &#39;Declare&#39; — instrukcje</span><span class="sxs-lookup"><span data-stu-id="344ef-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="344ef-103">`Any` — Typ danych została użyta z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na stosowanie argumentów zawierających dane dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="344ef-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="344ef-104">Przeładowanie, jednak obsługuje Visual Basic i tak powoduje, że `Any` przestarzałe typu danych.</span><span class="sxs-lookup"><span data-stu-id="344ef-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="344ef-105">**Identyfikator błędu:** BC30828</span><span class="sxs-lookup"><span data-stu-id="344ef-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="344ef-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="344ef-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="344ef-107">Deklarowanie parametrów określonego typu, który ma zostać użyty. na przykład.</span><span class="sxs-lookup"><span data-stu-id="344ef-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="344ef-108">Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` jest oczekiwane przez procedury wywoływanej.</span><span class="sxs-lookup"><span data-stu-id="344ef-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="344ef-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="344ef-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="344ef-110">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="344ef-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="344ef-111">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="344ef-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="344ef-112">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="344ef-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
