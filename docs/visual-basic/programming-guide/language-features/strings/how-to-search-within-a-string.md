---
title: 'Instrukcje: Wyszukiwanie wewnątrz ciągu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: b690aa78a2cf07b0db5bdd28d7d71ed4a79fbf61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032087"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="c7e3f-102">Instrukcje: Wyszukiwanie wewnątrz ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7e3f-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="c7e3f-103">Ten przykład wywołuje <xref:System.String.IndexOf%2A> metody <xref:System.String> obiektu, aby zgłosić indeks pierwszego wystąpienia podciągu.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7e3f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7e3f-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7e3f-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c7e3f-105">Compiling the Code</span></span>  
 <span data-ttu-id="c7e3f-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c7e3f-106">This example requires:</span></span>  
  
- <span data-ttu-id="c7e3f-107">`Imports` Instrukcję, określając <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="c7e3f-108">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c7e3f-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c7e3f-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="c7e3f-109">Robust Programming</span></span>  
 <span data-ttu-id="c7e3f-110"><xref:System.String.IndexOf%2A> Metoda zgłasza położenie pierwszego wystąpienia znaku pierwszego wystąpienia podciągu.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="c7e3f-111">Indeks jest oparty na 0, co oznacza, że pierwszym znakiem ciągu ma indeks 0.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="c7e3f-112">Jeśli <xref:System.String.IndexOf%2A> nie zwraca podciąg, zwraca -1.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="c7e3f-113"><xref:System.String.IndexOf%2A> Metoda jest uwzględniana wielkość liter i używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="c7e3f-114">Dla formantu optymalne błąd, możesz chcieć ująć wyszukiwania ciągów w `Try` bloku [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="c7e3f-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e3f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7e3f-115">See also</span></span>

- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="c7e3f-116">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c7e3f-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="c7e3f-117">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7e3f-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="c7e3f-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="c7e3f-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
