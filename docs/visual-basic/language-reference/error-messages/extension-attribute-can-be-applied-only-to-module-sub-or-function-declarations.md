---
title: '&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718237"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="0ba1c-102">&#39;Rozszerzenie&#39; atrybut można stosować tylko do &#39;modułu&#39;, &#39;Sub&#39;, lub &#39;funkcja&#39; deklaracji</span><span class="sxs-lookup"><span data-stu-id="0ba1c-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="0ba1c-103">Jedynym sposobem, aby rozszerzyć typu danych w języku Visual Basic jest zdefiniować metodę rozszerzenia w ramach standardowego modułu.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="0ba1c-104">Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="0ba1c-105">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0ba1c-106">Opcjonalnie moduł, który zawiera metodę rozszerzającą może być oznaczony w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="0ba1c-107">Zakaz używania atrybutu rozszerzenia jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="0ba1c-108">**Identyfikator błędu:** BC36550</span><span class="sxs-lookup"><span data-stu-id="0ba1c-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0ba1c-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0ba1c-109">To correct this error</span></span>  
  
-   <span data-ttu-id="0ba1c-110">Usuń atrybut rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="0ba1c-111">Zmodyfikowanie Twojego rozszerzenia jako metoda, zdefiniowana w module otaczającej.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ba1c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ba1c-112">Example</span></span>  
 <span data-ttu-id="0ba1c-113">W poniższym przykładzie zdefiniowano `Print` metodę `String` typu danych.</span><span class="sxs-lookup"><span data-stu-id="0ba1c-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ba1c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ba1c-114">See also</span></span>
- [<span data-ttu-id="0ba1c-115">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="0ba1c-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="0ba1c-116">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="0ba1c-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="0ba1c-117">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="0ba1c-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
