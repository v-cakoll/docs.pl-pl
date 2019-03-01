---
title: 'Instrukcje: Wyszukiwanie wewnątrz ciągu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: c150299efe07809d0d33edf882771f552c3e5b63
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982014"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="b0c44-102">Instrukcje: Wyszukiwanie wewnątrz ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0c44-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="b0c44-103">Ten przykład wywołuje <xref:System.String.IndexOf%2A> metody <xref:System.String> obiektu, aby zgłosić indeks pierwszego wystąpienia podciągu.</span><span class="sxs-lookup"><span data-stu-id="b0c44-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c44-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0c44-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b0c44-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b0c44-105">Compiling the Code</span></span>  
 <span data-ttu-id="b0c44-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b0c44-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b0c44-107">`Imports` Instrukcję, określając <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b0c44-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="b0c44-108">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b0c44-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b0c44-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="b0c44-109">Robust Programming</span></span>  
 <span data-ttu-id="b0c44-110"><xref:System.String.IndexOf%2A> Metoda zgłasza położenie pierwszego wystąpienia znaku pierwszego wystąpienia podciągu.</span><span class="sxs-lookup"><span data-stu-id="b0c44-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="b0c44-111">Indeks jest oparty na 0, co oznacza, że pierwszym znakiem ciągu ma indeks 0.</span><span class="sxs-lookup"><span data-stu-id="b0c44-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="b0c44-112">Jeśli <xref:System.String.IndexOf%2A> nie zwraca podciąg, zwraca -1.</span><span class="sxs-lookup"><span data-stu-id="b0c44-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="b0c44-113"><xref:System.String.IndexOf%2A> Metoda jest uwzględniana wielkość liter i używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="b0c44-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="b0c44-114">Dla formantu optymalne błąd, możesz chcieć ująć wyszukiwania ciągów w `Try` bloku [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0c44-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c44-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0c44-115">See also</span></span>
- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="b0c44-116">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b0c44-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b0c44-117">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0c44-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="b0c44-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="b0c44-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
