---
title: "&#39; Rozszerzenie &#39; Atrybut można stosować tylko do &#39; Moduł &#39; &#39; Sub &#39; lub &#39; Funkcja &#39; deklaracje"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="a9dfc-102">&#39; Rozszerzenie &#39; Atrybut można stosować tylko do &#39; Moduł &#39; &#39; Sub &#39; lub &#39; Funkcja &#39; deklaracje</span><span class="sxs-lookup"><span data-stu-id="a9dfc-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="a9dfc-103">Jedynym sposobem rozszerzenia typu danych w języku Visual Basic jest określenie metody rozszerzenia wewnątrz standardowy moduł.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="a9dfc-104">Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="a9dfc-105">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="a9dfc-106">Opcjonalnie moduł, który zawiera metody rozszerzenia mogą być oznaczone w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="a9dfc-107">Nie użycie atrybutu rozszerzenia jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="a9dfc-108">**Identyfikator błędu:** BC36550</span><span class="sxs-lookup"><span data-stu-id="a9dfc-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a9dfc-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a9dfc-109">To correct this error</span></span>  
  
-   <span data-ttu-id="a9dfc-110">Usuń atrybut rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="a9dfc-111">Zmodyfikowanie rozszerzenie metodą zdefiniowanego w module otaczającej.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9dfc-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9dfc-112">Example</span></span>  
 <span data-ttu-id="a9dfc-113">W poniższym przykładzie zdefiniowano `Print` metodę `String` typu danych.</span><span class="sxs-lookup"><span data-stu-id="a9dfc-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a9dfc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9dfc-114">See Also</span></span>  
 [<span data-ttu-id="a9dfc-115">Atrybuty — omówienie</span><span class="sxs-lookup"><span data-stu-id="a9dfc-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="a9dfc-116">Metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="a9dfc-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="a9dfc-117">Module — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9dfc-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
