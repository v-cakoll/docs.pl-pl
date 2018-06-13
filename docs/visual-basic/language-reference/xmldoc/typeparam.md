---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 76e0e8d4757f29bb5df82ea1482beff3dd43c0e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598017"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="d6258-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6258-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="d6258-103">Definiuje typ parametru nazwę i opis.</span><span class="sxs-lookup"><span data-stu-id="d6258-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6258-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6258-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6258-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6258-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d6258-106">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d6258-106">The name of the type parameter.</span></span> <span data-ttu-id="d6258-107">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="d6258-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d6258-108">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d6258-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6258-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6258-109">Remarks</span></span>  
 <span data-ttu-id="d6258-110">Użyj `<typeparam>` tag w komentarz dla typu ogólnego lub deklaracji elementu członkowskiego ogólny opis jednego z parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="d6258-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="d6258-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="d6258-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6258-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6258-112">Example</span></span>  
 <span data-ttu-id="d6258-113">W tym przykładzie użyto `<typeparam>` tag do opisywania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="d6258-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d6258-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6258-114">See Also</span></span>  
 [<span data-ttu-id="d6258-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="d6258-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
