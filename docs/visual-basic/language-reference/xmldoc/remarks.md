---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 7125f6079811421bc5a7abdce2e13d591a299630
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269331"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="f3ad6-102">\<Remarks > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3ad6-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="f3ad6-103">Określa sekcji uwag, elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f3ad6-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ad6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3ad6-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3ad6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3ad6-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="f3ad6-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f3ad6-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3ad6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3ad6-107">Remarks</span></span>  
 <span data-ttu-id="f3ad6-108">Użyj `<remarks>` tag, aby dodać informacje o typie, uzupełniające informacje określony za pomocą [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="f3ad6-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="f3ad6-109">Te informacje są wyświetlane w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="f3ad6-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="f3ad6-110">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="f3ad6-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="f3ad6-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="f3ad6-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3ad6-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3ad6-112">Example</span></span>  
 <span data-ttu-id="f3ad6-113">W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="f3ad6-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f3ad6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3ad6-114">See also</span></span>
- [<span data-ttu-id="f3ad6-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="f3ad6-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
