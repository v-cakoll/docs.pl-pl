---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 1ef8d76699534a7408912424bcdea651d8314364
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283988"
---
# <a name="paramref-visual-basic"></a><span data-ttu-id="ee1d3-102">\<paramref > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee1d3-102">\<paramref> (Visual Basic)</span></span>
<span data-ttu-id="ee1d3-103">Formatuje wyrazem jako parametr.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee1d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee1d3-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee1d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee1d3-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ee1d3-106">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="ee1d3-107">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="ee1d3-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee1d3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee1d3-108">Remarks</span></span>  
 <span data-ttu-id="ee1d3-109">`<paramref>` Tag zapewnia sposób, aby wskazać, że wyraz jest parametrem.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="ee1d3-110">Plik XML mogą być przetwarzane do formatowania tego parametru w jakiś sposób distinct.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="ee1d3-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee1d3-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee1d3-112">Example</span></span>  
 <span data-ttu-id="ee1d3-113">W tym przykładzie użyto `<paramref>` tag do odwoływania się do `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="ee1d3-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ee1d3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee1d3-114">See also</span></span>
- [<span data-ttu-id="ee1d3-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="ee1d3-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
