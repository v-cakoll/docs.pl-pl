---
title: Element „As Any” nie jest obsługiwany w instrukcjach „Declare”
ms.date: 07/20/2015
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
ms.openlocfilehash: 3593f238c72cbcce911c72e42552d6a75188b628
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310697"
---
# <a name="as-any-is-not-supported-in-declare-statements"></a><span data-ttu-id="40081-102">Element „As Any” nie jest obsługiwany w instrukcjach „Declare”</span><span class="sxs-lookup"><span data-stu-id="40081-102">'As Any' is not supported in 'Declare' statements</span></span>
<span data-ttu-id="40081-103">`Any` — Typ danych był używany z `Declare` instrukcje w Visual Basic 6.0 i starszych wersji, aby zezwolić na korzystanie z argumentów, które mogą zawierać dowolny typ danych.</span><span class="sxs-lookup"><span data-stu-id="40081-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> <span data-ttu-id="40081-104">Obsługa języka Visual Basic przeciążenia, jednak i sprawia, że tak `Any` przestarzały typ danych.</span><span class="sxs-lookup"><span data-stu-id="40081-104">Visual Basic supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="40081-105">**Identyfikator błędu:** BC30828</span><span class="sxs-lookup"><span data-stu-id="40081-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40081-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="40081-106">To correct this error</span></span>  
  
1. <span data-ttu-id="40081-107">Można deklarować parametrów określonego typu, którego chcesz użyć. na przykład.</span><span class="sxs-lookup"><span data-stu-id="40081-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#95)]  
  
2. <span data-ttu-id="40081-108">Użyj <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić `As Any` podczas `Void*` oczekuje przez tę procedurę, wywoływana.</span><span class="sxs-lookup"><span data-stu-id="40081-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class5.vb#96)]  
  
## <a name="see-also"></a><span data-ttu-id="40081-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40081-109">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="40081-110">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="40081-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="40081-111">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40081-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="40081-112">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="40081-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
