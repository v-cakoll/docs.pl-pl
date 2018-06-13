---
title: '&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587322"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="c6e35-102">&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji</span><span class="sxs-lookup"><span data-stu-id="c6e35-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="c6e35-103">Jedynym sposobem rozszerzenia typu danych w języku Visual Basic jest określenie metody rozszerzenia wewnątrz standardowy moduł.</span><span class="sxs-lookup"><span data-stu-id="c6e35-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="c6e35-104">Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="c6e35-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="c6e35-105">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c6e35-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c6e35-106">Opcjonalnie moduł, który zawiera metody rozszerzenia mogą być oznaczone w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="c6e35-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="c6e35-107">Nie użycie atrybutu rozszerzenia jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="c6e35-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="c6e35-108">**Identyfikator błędu:** BC36550</span><span class="sxs-lookup"><span data-stu-id="c6e35-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6e35-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c6e35-109">To correct this error</span></span>  
  
-   <span data-ttu-id="c6e35-110">Usuń atrybut rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c6e35-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="c6e35-111">Zmodyfikowanie rozszerzenie metodą zdefiniowanego w module otaczającej.</span><span class="sxs-lookup"><span data-stu-id="c6e35-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6e35-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6e35-112">Example</span></span>  
 <span data-ttu-id="c6e35-113">W poniższym przykładzie zdefiniowano `Print` metodę `String` typu danych.</span><span class="sxs-lookup"><span data-stu-id="c6e35-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6e35-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6e35-114">See Also</span></span>  
 [<span data-ttu-id="c6e35-115">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="c6e35-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="c6e35-116">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="c6e35-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="c6e35-117">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c6e35-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
