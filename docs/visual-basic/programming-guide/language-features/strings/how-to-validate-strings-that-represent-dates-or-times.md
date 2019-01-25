---
title: 'Instrukcje: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 1a838d9d156ad9c05a70a4d4d72db1a288731c9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685402"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="24f0d-102">Instrukcje: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24f0d-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="24f0d-103">Poniższy kod ustawia przykład `Boolean` wartość, która wskazuje, czy ciąg reprezentuje prawidłowej daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="24f0d-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24f0d-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="24f0d-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24f0d-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="24f0d-105">Compiling the Code</span></span>  
 <span data-ttu-id="24f0d-106">Zastąp `("01/01/03")` i `"9:30 PM"` z daty i godziny, którą chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="24f0d-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="24f0d-107">Można zastąpić ciąg z innego ciągu ustalonych `String` zmiennej, lub z metodą, zwraca wartość typu ciąg, takie jak `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="24f0d-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="24f0d-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="24f0d-108">Robust Programming</span></span>  
 <span data-ttu-id="24f0d-109">Ta metoda służy do sprawdzenia ciągu przed próby skonwertowania `String` do `DateTime` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="24f0d-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="24f0d-110">Najpierw Sprawdzanie daty lub godziny, można uniknąć generowania wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="24f0d-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f0d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24f0d-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="24f0d-112">Sprawdzanie poprawności ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24f0d-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
