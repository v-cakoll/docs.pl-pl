---
title: 'Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647865"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="a50d3-102">Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a50d3-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="a50d3-103">Poniższy kod przykładzie `Boolean` wartość, która wskazuje, czy ciąg reprezentuje prawidłowej daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="a50d3-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a50d3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a50d3-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a50d3-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a50d3-105">Compiling the Code</span></span>  
 <span data-ttu-id="a50d3-106">Zastąp `("01/01/03")` i `"9:30 PM"` Data i godzina, o których chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="a50d3-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="a50d3-107">Można zastąpić ciąg z innego ciągu ustalony `String` zmiennej, lub za pomocą metody która zwraca wartość typu ciąg, takie jak `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="a50d3-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a50d3-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a50d3-108">Robust Programming</span></span>  
 <span data-ttu-id="a50d3-109">Ta metoda służy do sprawdzenia ciągu przed próby konwersji `String` do `DateTime` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a50d3-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="a50d3-110">Najpierw Sprawdzanie daty lub godziny, można uniknąć generowania wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a50d3-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a50d3-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a50d3-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="a50d3-112">Sprawdzanie poprawności ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a50d3-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
