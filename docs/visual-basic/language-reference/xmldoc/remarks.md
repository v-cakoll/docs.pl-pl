---
title: '&lt;Uwagi&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 6e4e280760b9238fdc403ac5fe586743334e4c69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="55143-102">&lt;Uwagi&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55143-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="55143-103">Określa elementu członkowskiego w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="55143-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55143-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55143-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55143-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55143-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="55143-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="55143-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55143-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55143-107">Remarks</span></span>  
 <span data-ttu-id="55143-108">Użyj `<remarks>` znacznik w celu dodania informacji o typie, uzupełniające podanych informacji o [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="55143-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="55143-109">Informacje te pojawiają się w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="55143-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="55143-110">Informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="55143-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="55143-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="55143-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55143-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="55143-112">Example</span></span>  
 <span data-ttu-id="55143-113">W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metoda wykonuje.</span><span class="sxs-lookup"><span data-stu-id="55143-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="55143-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55143-114">See Also</span></span>  
 [<span data-ttu-id="55143-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="55143-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
