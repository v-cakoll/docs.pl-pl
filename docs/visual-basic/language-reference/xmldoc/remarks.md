---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: b327e548bcdce1522a888855bd88e3150695147b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352252"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="fd1a6-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd1a6-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="fd1a6-102">Specifies a remarks section for the member.</span><span class="sxs-lookup"><span data-stu-id="fd1a6-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd1a6-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd1a6-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd1a6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd1a6-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="fd1a6-105">A description of the member.</span><span class="sxs-lookup"><span data-stu-id="fd1a6-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd1a6-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd1a6-106">Remarks</span></span>  
 <span data-ttu-id="fd1a6-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="fd1a6-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="fd1a6-108">This information appears in the Object Browser.</span><span class="sxs-lookup"><span data-stu-id="fd1a6-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="fd1a6-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="fd1a6-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="fd1a6-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="fd1a6-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd1a6-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd1a6-111">Example</span></span>  
 <span data-ttu-id="fd1a6-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span><span class="sxs-lookup"><span data-stu-id="fd1a6-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="fd1a6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd1a6-113">See also</span></span>

- [<span data-ttu-id="fd1a6-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="fd1a6-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
