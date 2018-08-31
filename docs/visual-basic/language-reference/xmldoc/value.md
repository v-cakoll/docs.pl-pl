---
title: '&lt;wartość&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: ef14836c438cf6a1de300270d9882c1e53e716ee
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258046"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="b086f-102">&lt;wartość&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b086f-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="b086f-103">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="b086f-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b086f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b086f-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b086f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b086f-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="b086f-106">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="b086f-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b086f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b086f-107">Remarks</span></span>  
 <span data-ttu-id="b086f-108">Użyj `<value>` tag do opisywania właściwości.</span><span class="sxs-lookup"><span data-stu-id="b086f-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="b086f-109">Należy pamiętać, że podczas dodawania właściwości, za pomocą Kreatora kodów w środowisku programowania Visual Studio, spowoduje to dodanie [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md) tag w przypadku nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b086f-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="b086f-110">Następnie należy ręcznie dodać `<value>` tag do opisania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="b086f-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="b086f-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b086f-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b086f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b086f-112">Example</span></span>  
 <span data-ttu-id="b086f-113">W tym przykładzie użyto `<value>` tag do opisania wartość, jaką `Counter` przechowuje właściwości.</span><span class="sxs-lookup"><span data-stu-id="b086f-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b086f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b086f-114">See Also</span></span>  
 [<span data-ttu-id="b086f-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="b086f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
