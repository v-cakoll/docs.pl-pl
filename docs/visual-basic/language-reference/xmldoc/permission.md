---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 71b00b669804e644d1171480192b9d55455bdf53
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352261"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="99568-101">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99568-101">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="99568-102">Specifies a required permission for the member.</span><span class="sxs-lookup"><span data-stu-id="99568-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99568-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="99568-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="99568-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="99568-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="99568-105">A reference to a member or field that is available to be called from the current compilation environment.</span><span class="sxs-lookup"><span data-stu-id="99568-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="99568-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span><span class="sxs-lookup"><span data-stu-id="99568-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="99568-107">Enclose `member` in quotation marks (" ").</span><span class="sxs-lookup"><span data-stu-id="99568-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="99568-108">A description of the access to the member.</span><span class="sxs-lookup"><span data-stu-id="99568-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99568-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="99568-109">Remarks</span></span>  
 <span data-ttu-id="99568-110">Use the `<permission>` tag to document the access of a member.</span><span class="sxs-lookup"><span data-stu-id="99568-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="99568-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span><span class="sxs-lookup"><span data-stu-id="99568-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="99568-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span><span class="sxs-lookup"><span data-stu-id="99568-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99568-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="99568-113">Example</span></span>  
 <span data-ttu-id="99568-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span><span class="sxs-lookup"><span data-stu-id="99568-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="99568-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99568-115">See also</span></span>

- [<span data-ttu-id="99568-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="99568-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
