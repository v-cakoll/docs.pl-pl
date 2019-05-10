---
title: Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 88212fb2c04eab61b719a161ae01ccdda9a6110d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640729"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="8e05e-102">Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”</span><span class="sxs-lookup"><span data-stu-id="8e05e-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="8e05e-103">Jedynym sposobem, aby rozszerzyć typu danych w języku Visual Basic jest zdefiniować metodę rozszerzenia w ramach standardowego modułu.</span><span class="sxs-lookup"><span data-stu-id="8e05e-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="8e05e-104">Metoda rozszerzenia może być `Sub` procedury lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="8e05e-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="8e05e-105">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8e05e-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="8e05e-106">Opcjonalnie moduł, który zawiera metodę rozszerzającą może być oznaczony w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="8e05e-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="8e05e-107">Zakaz używania atrybutu rozszerzenia jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8e05e-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="8e05e-108">**Identyfikator błędu:** BC36550</span><span class="sxs-lookup"><span data-stu-id="8e05e-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8e05e-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8e05e-109">To correct this error</span></span>  
  
- <span data-ttu-id="8e05e-110">Usuń atrybut rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8e05e-110">Remove the extension attribute.</span></span>  
  
- <span data-ttu-id="8e05e-111">Zmodyfikowanie Twojego rozszerzenia jako metoda, zdefiniowana w module otaczającej.</span><span class="sxs-lookup"><span data-stu-id="8e05e-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e05e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e05e-112">Example</span></span>  
 <span data-ttu-id="8e05e-113">W poniższym przykładzie zdefiniowano `Print` metodę `String` typu danych.</span><span class="sxs-lookup"><span data-stu-id="8e05e-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e05e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e05e-114">See also</span></span>

- [<span data-ttu-id="8e05e-115">Omówienie atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e05e-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="8e05e-116">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="8e05e-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="8e05e-117">Instrukcja Module</span><span class="sxs-lookup"><span data-stu-id="8e05e-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
