---
title: "Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="54267-102">Porady: Sprawdzanie poprawności ciągów reprezentujących daty lub godziny (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="54267-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="54267-103">Poniższy kod przykładzie `Boolean` wartość, która wskazuje, czy ciąg reprezentuje prawidłowej daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="54267-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54267-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="54267-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="54267-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="54267-105">Compiling the Code</span></span>  
 <span data-ttu-id="54267-106">Zastąp `("01/01/03")` i `"9:30 PM"` Data i godzina, o których chcesz zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="54267-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="54267-107">Można zastąpić ciąg z innego ciągu ustalony `String` zmiennej, lub za pomocą metody która zwraca wartość typu ciąg, takie jak `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="54267-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="54267-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="54267-108">Robust Programming</span></span>  
 <span data-ttu-id="54267-109">Ta metoda służy do sprawdzenia ciągu przed próby konwersji `String` do `DateTime` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="54267-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="54267-110">Najpierw Sprawdzanie daty lub godziny, można uniknąć generowania wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="54267-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54267-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54267-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="54267-112">Sprawdzanie poprawności ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="54267-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
