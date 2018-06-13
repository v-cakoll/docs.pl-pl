---
title: '&lt;wartość&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: f33a4ec32b45d8996bd39f0cc49097b5fd9252e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602462"
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="eb437-102">&lt;wartość&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb437-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="eb437-103">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb437-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb437-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb437-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb437-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb437-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="eb437-106">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb437-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb437-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb437-107">Remarks</span></span>  
 <span data-ttu-id="eb437-108">Użyj `<value>` tag do opisu właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb437-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="eb437-109">Należy pamiętać, że podczas dodawania właściwości przy użyciu Kreatora kodu w środowisku projektowym Visual Studio, spowoduje to dodanie [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md) tag nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb437-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="eb437-110">Następnie należy ręcznie dodać `<value>` tag do opisywania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="eb437-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="eb437-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="eb437-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb437-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb437-112">Example</span></span>  
 <span data-ttu-id="eb437-113">W tym przykładzie użyto `<value>` tag do opisywania jakie korzyści `Counter` właściwości blokad.</span><span class="sxs-lookup"><span data-stu-id="eb437-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eb437-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb437-114">See Also</span></span>  
 [<span data-ttu-id="eb437-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="eb437-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
