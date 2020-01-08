---
title: 'Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348413"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="3dcf6-102">Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3dcf6-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="3dcf6-103">Poniższy przykład kodu ustawia wartość `Boolean`, która wskazuje, czy ciąg reprezentuje prawidłową datę lub godzinę.</span><span class="sxs-lookup"><span data-stu-id="3dcf6-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dcf6-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3dcf6-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="3dcf6-105">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="3dcf6-105">Compile the code</span></span>  
 <span data-ttu-id="3dcf6-106">Zastąp `("01/01/03")` i `"9:30 PM"` datą i godziną, którą chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="3dcf6-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="3dcf6-107">Można zastąpić ciąg innym zakodowanym ciągiem zawierającym zmienną `String` lub metodę zwracającą ciąg, na przykład `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="3dcf6-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3dcf6-108">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="3dcf6-108">Robust Programming</span></span>  
 <span data-ttu-id="3dcf6-109">Użyj tej metody, aby sprawdzić poprawność ciągu przed próbą przekonwertowania `String` na zmienną `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="3dcf6-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="3dcf6-110">Sprawdzając najpierw datę lub godzinę, można uniknąć generowania wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3dcf6-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dcf6-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3dcf6-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="3dcf6-112">Sprawdzanie poprawności ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3dcf6-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
