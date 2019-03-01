---
title: 'Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: d29553071d68319d754406b3104da6e096f908fd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975527"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="5672b-102">Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5672b-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="5672b-103">W tym przykładzie zwraca `Boolean` wartość, która wskazuje, czy ciąg reprezentuje nazwę pliku lub ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="5672b-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="5672b-104">Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone przez system plików.</span><span class="sxs-lookup"><span data-stu-id="5672b-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5672b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5672b-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="5672b-106">W tym przykładzie nie sprawdza, czy nazwa niepoprawnie został umieszczony w dwukropki lub katalogi bez nazwy, czy długość nazwy przekracza maksymalną długość zdefiniowaną przez system.</span><span class="sxs-lookup"><span data-stu-id="5672b-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="5672b-107">Ponadto nie sprawdza ona, czy aplikacja ma uprawnienia dostępu do zasobu systemu plików przy użyciu określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="5672b-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5672b-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5672b-108">See also</span></span>
- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="5672b-109">Sprawdzanie poprawności ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5672b-109">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
