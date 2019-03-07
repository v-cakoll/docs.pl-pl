---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 7ab1f4a19793c408acfe1c4adf76aed5679fc696
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474270"
---
# <a name="value-visual-basic"></a><span data-ttu-id="9a469-102">\<wartość > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a469-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="9a469-103">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a469-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a469-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a469-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a469-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a469-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="9a469-106">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a469-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a469-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a469-107">Remarks</span></span>  
 <span data-ttu-id="9a469-108">Użyj `<value>` tag do opisywania właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a469-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="9a469-109">Należy pamiętać, że podczas dodawania właściwości, za pomocą Kreatora kodów w środowisku programowania Visual Studio, spowoduje to dodanie [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md) tag w przypadku nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a469-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="9a469-110">Następnie należy ręcznie dodać `<value>` tag do opisania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="9a469-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="9a469-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="9a469-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a469-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a469-112">Example</span></span>  
 <span data-ttu-id="9a469-113">W tym przykładzie użyto `<value>` tag do opisania wartość, jaką `Counter` przechowuje właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a469-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9a469-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a469-114">See also</span></span>
- [<span data-ttu-id="9a469-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="9a469-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
