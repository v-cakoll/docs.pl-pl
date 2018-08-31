---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 153f5ddeeb7d09159049af4d466b0695f5cb6f23
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331362"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="a6803-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6803-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="a6803-103">Formatuje wyrazem jako parametr.</span><span class="sxs-lookup"><span data-stu-id="a6803-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6803-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6803-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6803-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6803-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a6803-106">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="a6803-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="a6803-107">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="a6803-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6803-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6803-108">Remarks</span></span>  
 <span data-ttu-id="a6803-109">`<paramref>` Tag zapewnia sposób, aby wskazać, że wyraz jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="a6803-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="a6803-110">Plik XML mogą być przetwarzane do formatowania tego parametru w jakiś sposób distinct.</span><span class="sxs-lookup"><span data-stu-id="a6803-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="a6803-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="a6803-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6803-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6803-112">Example</span></span>  
 <span data-ttu-id="a6803-113">W tym przykładzie użyto `<paramref>` tag do odwoływania się do `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="a6803-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a6803-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6803-114">See Also</span></span>  
 [<span data-ttu-id="a6803-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="a6803-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
