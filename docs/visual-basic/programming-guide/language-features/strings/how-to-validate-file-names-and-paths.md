---
title: 'Instrukcje: Sprawdzanie poprawności nazw plików oraz ścieżek'
ms.date: 07/20/2015
helpviewer_keywords:
- file names [Visual Basic], validating
- strings [Visual Basic], validating
- Boolean values [Visual Basic]
- paths [Visual Basic], validating
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
ms.openlocfilehash: 3b4695dfbcaf05c73bd53af5be7a49d081eb8e47
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410583"
---
# <a name="how-to-validate-file-names-and-paths-in-visual-basic"></a><span data-ttu-id="e481d-102">Porady: sprawdzanie poprawności nazw plików oraz ścieżek w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e481d-102">How to: Validate File Names and Paths in Visual Basic</span></span>
<span data-ttu-id="e481d-103">Ten przykład zwraca `Boolean` wartość wskazującą, czy ciąg reprezentuje nazwę pliku lub ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="e481d-103">This example returns a `Boolean` value that indicates whether a string represents a file name or path.</span></span> <span data-ttu-id="e481d-104">Sprawdzanie poprawności sprawdza, czy nazwa zawiera znaki, które nie są dozwolone przez system plików.</span><span class="sxs-lookup"><span data-stu-id="e481d-104">The validation checks if the name contains characters that are not allowed by the file system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e481d-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e481d-105">Example</span></span>  
 [!code-vb[VbVbcnRegEx#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#4)]  
  
 <span data-ttu-id="e481d-106">Ten przykład nie sprawdza, czy nazwa ma nieprawidłowo umieszczone kolonie lub katalogi bez nazwy lub jeśli długość nazwy przekracza maksymalną długość zdefiniowaną przez system.</span><span class="sxs-lookup"><span data-stu-id="e481d-106">This example does not check if the name has incorrectly placed colons, or directories with no name, or if the length of the name exceeds the system-defined maximum length.</span></span> <span data-ttu-id="e481d-107">Nie sprawdza także, czy aplikacja ma uprawnienia dostępu do zasobu systemu plików o określonej nazwie.</span><span class="sxs-lookup"><span data-stu-id="e481d-107">It also does not check if the application has permission to access the file-system resource with the specified name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e481d-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e481d-108">See also</span></span>

- <xref:System.IO.Path.GetInvalidPathChars%2A>
- [<span data-ttu-id="e481d-109">Sprawdzanie poprawności ciągów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e481d-109">Validating Strings in Visual Basic</span></span>](validating-strings.md)
