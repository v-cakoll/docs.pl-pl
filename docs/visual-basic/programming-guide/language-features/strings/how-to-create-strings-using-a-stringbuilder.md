---
title: 'Instrukcje: Tworzenie ciągów za pomocą StringBuilder w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 00fefcc138164288d872cd339f165dc6ffc0131a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834195"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="b4750-102">Instrukcje: Tworzenie ciągów za pomocą StringBuilder w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4750-102">How to: Create Strings Using a StringBuilder in Visual Basic</span></span>
<span data-ttu-id="b4750-103">Ten przykład tworzy ciąg z wielu mniejszych ciągów za pomocą <xref:System.Text.StringBuilder> klasy.</span><span class="sxs-lookup"><span data-stu-id="b4750-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="b4750-104"><xref:System.Text.StringBuilder> Klasy jest bardziej wydajne niż `&=` operator łączenie wielu ciągów.</span><span class="sxs-lookup"><span data-stu-id="b4750-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4750-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4750-105">Example</span></span>  
 <span data-ttu-id="b4750-106">Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągów do tego wystąpienia, a następnie zwraca jego reprezentację ciągu.</span><span class="sxs-lookup"><span data-stu-id="b4750-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation.</span></span>  
  
 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]  
  
## <a name="see-also"></a><span data-ttu-id="b4750-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4750-107">See also</span></span>

- [<span data-ttu-id="b4750-108">Używanie klasy StringBuilder</span><span class="sxs-lookup"><span data-stu-id="b4750-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="b4750-109">&=, operator</span><span class="sxs-lookup"><span data-stu-id="b4750-109">&= Operator</span></span>](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="b4750-110">Ciągi</span><span class="sxs-lookup"><span data-stu-id="b4750-110">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="b4750-111">Tworzenie nowych ciągów</span><span class="sxs-lookup"><span data-stu-id="b4750-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="b4750-112">Manipulowanie ciągami</span><span class="sxs-lookup"><span data-stu-id="b4750-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
