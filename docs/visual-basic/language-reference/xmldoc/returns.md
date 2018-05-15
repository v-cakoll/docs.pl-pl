---
title: '&lt;Zwraca&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: effc55bd65ae6c54575b7931529499505a9523cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="1ae49-102">&lt;Zwraca&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ae49-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="1ae49-103">Określa wartość zwracaną właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ae49-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ae49-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1ae49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ae49-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="1ae49-106">Opis wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="1ae49-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ae49-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ae49-107">Remarks</span></span>  
 <span data-ttu-id="1ae49-108">Użyj `<returns>` tag w komentarz dla deklaracji metody do opisywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="1ae49-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="1ae49-109">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="1ae49-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ae49-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ae49-110">Example</span></span>  
 <span data-ttu-id="1ae49-111">W tym przykładzie użyto `<returns>` tag, aby wyjaśnić, co `DoesRecordExist` funkcja zwraca.</span><span class="sxs-lookup"><span data-stu-id="1ae49-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1ae49-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ae49-112">See Also</span></span>  
 [<span data-ttu-id="1ae49-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="1ae49-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
