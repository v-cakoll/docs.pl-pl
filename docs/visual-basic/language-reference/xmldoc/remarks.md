---
title: <remarks> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c5c088472ae09a416953d9c0829cad1cb48646b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940819"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="e95fb-102">\<Remarks > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e95fb-102">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="e95fb-103">Określa sekcji uwag, elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e95fb-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e95fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e95fb-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e95fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e95fb-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e95fb-106">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e95fb-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e95fb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e95fb-107">Remarks</span></span>  
 <span data-ttu-id="e95fb-108">Użyj `<remarks>` tag, aby dodać informacje o typie, uzupełniające informacje określony za pomocą [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="e95fb-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="e95fb-109">Te informacje są wyświetlane w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="e95fb-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="e95fb-110">Aby uzyskać informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="e95fb-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="e95fb-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e95fb-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e95fb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e95fb-112">Example</span></span>  
 <span data-ttu-id="e95fb-113">W tym przykładzie użyto `<remarks>` tag, aby wyjaśnić, co `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="e95fb-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e95fb-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e95fb-114">See also</span></span>

- [<span data-ttu-id="e95fb-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e95fb-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
