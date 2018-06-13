---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598665"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="30824-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30824-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="30824-103">Formatuje wyraz jako parametr.</span><span class="sxs-lookup"><span data-stu-id="30824-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30824-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30824-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30824-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30824-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="30824-106">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="30824-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="30824-107">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="30824-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30824-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30824-108">Remarks</span></span>  
 <span data-ttu-id="30824-109">`<paramref>` Tag udostępnia sposób wskazują, że wyraz jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="30824-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="30824-110">Aby sformatować ten parametr w jakiś sposób różne mogą być przetwarzane plik XML.</span><span class="sxs-lookup"><span data-stu-id="30824-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="30824-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="30824-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30824-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="30824-112">Example</span></span>  
 <span data-ttu-id="30824-113">W tym przykładzie użyto `<paramref>` tag do odwoływania się do `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="30824-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="30824-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30824-114">See Also</span></span>  
 [<span data-ttu-id="30824-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="30824-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
