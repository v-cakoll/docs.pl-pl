---
title: "Porady: wyszukiwanie wewnątrz ciągu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="1c7f9-102">Porady: wyszukiwanie wewnątrz ciągu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c7f9-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="1c7f9-103">W tym przykładzie wywołuje <xref:System.String.IndexOf%2A> metoda <xref:System.String> obiektu do zgłaszania indeks pierwszego wystąpienia podciągu.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c7f9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c7f9-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c7f9-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1c7f9-105">Compiling the Code</span></span>  
 <span data-ttu-id="1c7f9-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1c7f9-106">This example requires:</span></span>  
  
-   <span data-ttu-id="1c7f9-107">`Imports` Określenie instrukcji <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="1c7f9-108">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="1c7f9-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1c7f9-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1c7f9-109">Robust Programming</span></span>  
 <span data-ttu-id="1c7f9-110"><xref:System.String.IndexOf%2A> Metoda zgłasza lokalizacji pierwszego znaku pierwszego wystąpienia podciąg.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="1c7f9-111">Indeks jest oparty na 0, co oznacza, że pierwszy znak w ciągu ma indeks 0.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="1c7f9-112">Jeśli <xref:System.String.IndexOf%2A> nie zwraca podciąg, zwraca -1.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="1c7f9-113"><xref:System.String.IndexOf%2A> Metoda jest rozróżniana wielkość liter i używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="1c7f9-114">Kontrolki optymalne błąd, możesz chcieć ujmij wyszukaj ciąg w `Try` zablokować z [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="1c7f9-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7f9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c7f9-115">See Also</span></span>  
 <xref:System.String.IndexOf%2A>  
 [<span data-ttu-id="1c7f9-116">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="1c7f9-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="1c7f9-117">Wprowadzenie do ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c7f9-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="1c7f9-118">Ciągi</span><span class="sxs-lookup"><span data-stu-id="1c7f9-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
