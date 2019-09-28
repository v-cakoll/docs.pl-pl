---
title: Parametrów typu nie można używać jako kwalifikatorów
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592136"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="15463-102">Parametrów typu nie można używać jako kwalifikatorów</span><span class="sxs-lookup"><span data-stu-id="15463-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="15463-103">Element programistyczny jest kwalifikowana za pomocą ciągu kwalifikacji, który zawiera parametr typu.</span><span class="sxs-lookup"><span data-stu-id="15463-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="15463-104">Parametr typu reprezentuje wymaganie dla typu, który ma zostać dostarczony podczas konstruowania typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="15463-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="15463-105">Nie reprezentuje określonego zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="15463-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="15463-106">Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="15463-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="15463-107">Poniższe instrukcje mogą generować ten błąd.</span><span class="sxs-lookup"><span data-stu-id="15463-107">The following statements can generate this error.</span></span>  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="15463-108">**Identyfikator błędu:** BC32098</span><span class="sxs-lookup"><span data-stu-id="15463-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15463-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="15463-109">To correct this error</span></span>  
  
1. <span data-ttu-id="15463-110">Usuń parametr typu z ciągu kwalifikacji lub zastąp go zdefiniowanym typem.</span><span class="sxs-lookup"><span data-stu-id="15463-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2. <span data-ttu-id="15463-111">Jeśli musisz użyć skonstruowanego typu do zlokalizowania kwalifikowanego elementu programistycznego, musisz użyć dodatkowej logiki programu.</span><span class="sxs-lookup"><span data-stu-id="15463-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15463-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15463-112">See also</span></span>

- [<span data-ttu-id="15463-113">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="15463-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="15463-114">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15463-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="15463-115">Lista typów</span><span class="sxs-lookup"><span data-stu-id="15463-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
