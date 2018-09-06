---
title: '&lt;Uwagi&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 97fca8758d9c21ac0b8f15bf9d5831750fbabe77
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863036"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="7d2f7-102">&lt;Uwagi&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d2f7-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="7d2f7-103">Określa sekcji uwag, elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7d2f7-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d2f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d2f7-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d2f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d2f7-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="7d2f7-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7d2f7-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d2f7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d2f7-107">Remarks</span></span>  
 <span data-ttu-id="7d2f7-108">Użyj `<remarks>` tag, aby dodać informacje o typie, uzupełniające informacje określony za pomocą [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="7d2f7-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="7d2f7-109">Te informacje są wyświetlane w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="7d2f7-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="7d2f7-110">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="7d2f7-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="7d2f7-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="7d2f7-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d2f7-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d2f7-112">Example</span></span>  
 <span data-ttu-id="7d2f7-113">W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="7d2f7-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7d2f7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d2f7-114">See Also</span></span>  
 [<span data-ttu-id="7d2f7-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="7d2f7-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
