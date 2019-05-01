---
title: 'Instrukcje: Tworzenie ciągu z tablicy wartości znaków (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 1f72cb86ffa38dc929062fab2f5592a781f2de27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054058"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="76497-102">Instrukcje: Tworzenie ciągu z tablicy wartości znaków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76497-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="76497-103">W tym przykładzie tworzy ciągu "abcd" na podstawie poszczególnych znaków.</span><span class="sxs-lookup"><span data-stu-id="76497-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76497-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="76497-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76497-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="76497-105">Compiling the Code</span></span>  
 <span data-ttu-id="76497-106">Ta metoda nie ma żadnych specjalnych wymagań.</span><span class="sxs-lookup"><span data-stu-id="76497-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="76497-107">Składnia `"a"c`, w którym jeden `c` następuje pojedynczy znak w cudzysłów, służy do tworzenia znak literału.</span><span class="sxs-lookup"><span data-stu-id="76497-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="76497-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="76497-108">Robust Programming</span></span>  
 <span data-ttu-id="76497-109">Znaki null (równoważne `Chr(0)`) w ciągu prowadzić do nieoczekiwanych wyników przy użyciu ciągu.</span><span class="sxs-lookup"><span data-stu-id="76497-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="76497-110">Znak null, będzie ona uwzględniona w ciągu, ale znaki po znaku null nie będą wyświetlane w niektórych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="76497-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76497-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76497-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="76497-112">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="76497-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="76497-113">Typy danych</span><span class="sxs-lookup"><span data-stu-id="76497-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
