---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 38549b2fcce0740b2b9cfd42d950e56b343e7a30
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524678"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="88732-102">> \<remarks (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88732-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="88732-103">Określa sekcję Uwagi dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="88732-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88732-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88732-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="88732-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88732-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="88732-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="88732-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88732-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88732-107">Remarks</span></span>  
 <span data-ttu-id="88732-108">Użyj znacznika `<remarks>`, aby dodać informacje o typie, uzupełniając informacje określone za pomocą [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="88732-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="88732-109">Te informacje są wyświetlane w Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="88732-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="88732-110">Aby uzyskać informacje na temat Przeglądarka obiektów, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="88732-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="88732-111">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="88732-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88732-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="88732-112">Example</span></span>  
 <span data-ttu-id="88732-113">W tym przykładzie używa znacznika `<remarks>`, aby wyjaśnić, jak działa Metoda `UpdateRecord`.</span><span class="sxs-lookup"><span data-stu-id="88732-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="88732-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88732-114">See also</span></span>

- [<span data-ttu-id="88732-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="88732-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
