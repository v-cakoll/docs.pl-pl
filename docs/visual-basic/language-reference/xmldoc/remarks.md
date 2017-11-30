---
title: '&lt;Uwagi&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f70c2d7df190d2ff8187882a9176dbe98984296
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="b31bb-102">&lt;Uwagi&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b31bb-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="b31bb-103">Określa elementu członkowskiego w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="b31bb-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b31bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b31bb-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b31bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b31bb-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="b31bb-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b31bb-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b31bb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b31bb-107">Remarks</span></span>  
 <span data-ttu-id="b31bb-108">Użyj `<remarks>` znacznik w celu dodania informacji o typie, uzupełniające podanych informacji o [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="b31bb-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="b31bb-109">Informacje te pojawiają się w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="b31bb-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="b31bb-110">Informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="b31bb-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="b31bb-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b31bb-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b31bb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b31bb-112">Example</span></span>  
 <span data-ttu-id="b31bb-113">W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metoda wykonuje.</span><span class="sxs-lookup"><span data-stu-id="b31bb-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b31bb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b31bb-114">See Also</span></span>  
 [<span data-ttu-id="b31bb-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="b31bb-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
