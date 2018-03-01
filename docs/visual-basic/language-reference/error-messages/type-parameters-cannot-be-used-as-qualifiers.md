---
title: "Parametrów typu nie można używać jako kwalifikatorów"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="9b795-102">Parametrów typu nie można używać jako kwalifikatorów</span><span class="sxs-lookup"><span data-stu-id="9b795-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="9b795-103">Element programowania jest kwalifikowany za pomocą kwalifikacji ciąg, który zawiera parametr typu.</span><span class="sxs-lookup"><span data-stu-id="9b795-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="9b795-104">Parametr typu reprezentuje typ, który ma zostać podane w przypadku typu ogólnego jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="9b795-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="9b795-105">Ten element nie reprezentuje określonego typu zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="9b795-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="9b795-106">Ciąg kwalifikacji musi zawierać tylko elementy, które są zdefiniowane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9b795-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="9b795-107">Poniższe instrukcje może spowodować wygenerowanie tego błędu.</span><span class="sxs-lookup"><span data-stu-id="9b795-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="9b795-108">**Identyfikator błędu:** BC32098</span><span class="sxs-lookup"><span data-stu-id="9b795-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9b795-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9b795-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="9b795-110">Usuń parametr typu z ciągu kwalifikacji lub Zamień zdefiniowanego typu.</span><span class="sxs-lookup"><span data-stu-id="9b795-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="9b795-111">Jeśli musisz użyć skonstruowanego typu można znaleźć elementu programistycznego jest kwalifikowana, należy użyć dodatkowe logice programu.</span><span class="sxs-lookup"><span data-stu-id="9b795-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b795-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b795-112">See Also</span></span>  
 [<span data-ttu-id="9b795-113">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="9b795-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="9b795-114">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b795-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="9b795-115">Lista typów</span><span class="sxs-lookup"><span data-stu-id="9b795-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
