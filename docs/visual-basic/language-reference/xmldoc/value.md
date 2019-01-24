---
title: '&lt;wartość&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 92c8c2ac7b95e97b37c907e3837bc90dac384b33
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558946"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="3380e-102">&lt;wartość&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3380e-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="3380e-103">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="3380e-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3380e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3380e-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3380e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3380e-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="3380e-106">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="3380e-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3380e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3380e-107">Remarks</span></span>  
 <span data-ttu-id="3380e-108">Użyj `<value>` tag do opisywania właściwości.</span><span class="sxs-lookup"><span data-stu-id="3380e-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="3380e-109">Należy pamiętać, że podczas dodawania właściwości, za pomocą Kreatora kodów w środowisku programowania Visual Studio, spowoduje to dodanie [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md) tag w przypadku nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="3380e-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="3380e-110">Następnie należy ręcznie dodać `<value>` tag do opisania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="3380e-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="3380e-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="3380e-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3380e-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3380e-112">Example</span></span>  
 <span data-ttu-id="3380e-113">W tym przykładzie użyto `<value>` tag do opisania wartość, jaką `Counter` przechowuje właściwości.</span><span class="sxs-lookup"><span data-stu-id="3380e-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3380e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3380e-114">See also</span></span>
- [<span data-ttu-id="3380e-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="3380e-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
