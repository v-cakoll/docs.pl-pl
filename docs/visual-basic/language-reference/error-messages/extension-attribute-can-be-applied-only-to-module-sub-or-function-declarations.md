---
title: Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583181"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="76f16-102">Atrybut „Extension” można stosować tylko w deklaracjach „Module”, „Sub” lub „Function”</span><span class="sxs-lookup"><span data-stu-id="76f16-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>

<span data-ttu-id="76f16-103">Jedynym sposobem rozszerzania typu danych w Visual Basic jest zdefiniowanie metody rozszerzającej wewnątrz modułu standardowego.</span><span class="sxs-lookup"><span data-stu-id="76f16-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="76f16-104">Metoda rozszerzenia może być `Sub` procedurą lub `Function` procedurą.</span><span class="sxs-lookup"><span data-stu-id="76f16-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="76f16-105">Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia, `<Extension()>` z przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="76f16-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="76f16-106">Opcjonalnie moduł, który zawiera metodę rozszerzenia, może być oznaczony w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="76f16-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="76f16-107">Żadne inne użycie atrybutu Extension nie jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="76f16-107">No other use of the extension attribute is valid.</span></span>

<span data-ttu-id="76f16-108">**Identyfikator błędu:** BC36550</span><span class="sxs-lookup"><span data-stu-id="76f16-108">**Error ID:** BC36550</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="76f16-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="76f16-109">To correct this error</span></span>

- <span data-ttu-id="76f16-110">Usuń atrybut rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="76f16-110">Remove the extension attribute.</span></span>

- <span data-ttu-id="76f16-111">Przeprojektowanie rozszerzenia jako metody zdefiniowanej w otaczającym module.</span><span class="sxs-lookup"><span data-stu-id="76f16-111">Redesign your extension as a method, defined in an enclosing module.</span></span>

## <a name="example"></a><span data-ttu-id="76f16-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="76f16-112">Example</span></span>

<span data-ttu-id="76f16-113">W poniższym przykładzie zdefiniowano metodę `Print` dla typu danych `String`.</span><span class="sxs-lookup"><span data-stu-id="76f16-113">The following example defines a `Print` method for the `String` data type.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="76f16-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76f16-114">See also</span></span>

- [<span data-ttu-id="76f16-115">Przegląd atrybutów</span><span class="sxs-lookup"><span data-stu-id="76f16-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="76f16-116">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="76f16-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="76f16-117">Module, instrukcja</span><span class="sxs-lookup"><span data-stu-id="76f16-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
