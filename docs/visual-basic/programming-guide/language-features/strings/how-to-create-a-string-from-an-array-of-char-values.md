---
title: 'Porady: tworzenie ciągu z tablicy wartości znaków'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344386"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="5e7bf-102">Porady: tworzenie ciągu z tablicy wartości znaków (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e7bf-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="5e7bf-103">This example creates the string "abcd" from individual characters.</span><span class="sxs-lookup"><span data-stu-id="5e7bf-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e7bf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e7bf-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e7bf-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5e7bf-105">Compiling the Code</span></span>  
 <span data-ttu-id="5e7bf-106">This method has no special requirements.</span><span class="sxs-lookup"><span data-stu-id="5e7bf-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="5e7bf-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span><span class="sxs-lookup"><span data-stu-id="5e7bf-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5e7bf-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5e7bf-108">Robust Programming</span></span>  
 <span data-ttu-id="5e7bf-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span><span class="sxs-lookup"><span data-stu-id="5e7bf-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="5e7bf-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span><span class="sxs-lookup"><span data-stu-id="5e7bf-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7bf-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e7bf-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="5e7bf-112">Char, typ danych</span><span class="sxs-lookup"><span data-stu-id="5e7bf-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="5e7bf-113">Typy danych</span><span class="sxs-lookup"><span data-stu-id="5e7bf-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
