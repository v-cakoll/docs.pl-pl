---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3e889f97565f7961ce975f41e9ec4c85a4d0d2c6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965993"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="e2c85-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c85-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="e2c85-103">Formatuje wyrazem jako parametr.</span><span class="sxs-lookup"><span data-stu-id="e2c85-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2c85-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2c85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2c85-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e2c85-106">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="e2c85-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="e2c85-107">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="e2c85-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2c85-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2c85-108">Remarks</span></span>  
 <span data-ttu-id="e2c85-109">`<paramref>` Tag zapewnia sposób, aby wskazać, że wyraz jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="e2c85-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="e2c85-110">Plik XML mogą być przetwarzane do formatowania tego parametru w jakiś sposób distinct.</span><span class="sxs-lookup"><span data-stu-id="e2c85-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="e2c85-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e2c85-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2c85-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2c85-112">Example</span></span>  
 <span data-ttu-id="e2c85-113">W tym przykładzie użyto `<paramref>` tag do odwoływania się do `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="e2c85-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e2c85-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2c85-114">See also</span></span>
- [<span data-ttu-id="e2c85-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e2c85-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
