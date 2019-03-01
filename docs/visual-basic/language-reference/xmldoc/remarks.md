---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 90f358aad8e3219b2e3cb3e9b996a24b3138828b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970834"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="06ff9-102">\<Remarks > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06ff9-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="06ff9-103">Określa sekcji uwag, elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="06ff9-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ff9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06ff9-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06ff9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06ff9-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="06ff9-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="06ff9-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06ff9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06ff9-107">Remarks</span></span>  
 <span data-ttu-id="06ff9-108">Użyj `<remarks>` tag, aby dodać informacje o typie, uzupełniające informacje określony za pomocą [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="06ff9-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="06ff9-109">Te informacje są wyświetlane w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="06ff9-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="06ff9-110">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="06ff9-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="06ff9-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="06ff9-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06ff9-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="06ff9-112">Example</span></span>  
 <span data-ttu-id="06ff9-113">W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="06ff9-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="06ff9-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06ff9-114">See also</span></span>
- [<span data-ttu-id="06ff9-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="06ff9-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
