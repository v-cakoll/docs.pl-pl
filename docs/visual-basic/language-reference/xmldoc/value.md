---
title: '&lt;wartość&gt; (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a72c6330596e59d26fbae9d13f6b9c8b1987e519
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltvaluegt-visual-basic"></a><span data-ttu-id="f14c8-102">&lt;wartość&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f14c8-102">&lt;value&gt; (Visual Basic)</span></span>
<span data-ttu-id="f14c8-103">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="f14c8-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f14c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f14c8-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f14c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f14c8-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="f14c8-106">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="f14c8-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f14c8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f14c8-107">Remarks</span></span>  
 <span data-ttu-id="f14c8-108">Użyj `<value>` tag do opisu właściwości.</span><span class="sxs-lookup"><span data-stu-id="f14c8-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="f14c8-109">Należy pamiętać, że podczas dodawania właściwości przy użyciu Kreatora kodu w środowisku projektowym Visual Studio, spowoduje to dodanie [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md) tag nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f14c8-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="f14c8-110">Następnie należy ręcznie dodać `<value>` tag do opisywania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="f14c8-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="f14c8-111">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="f14c8-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f14c8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f14c8-112">Example</span></span>  
 <span data-ttu-id="f14c8-113">W tym przykładzie użyto `<value>` tag do opisywania jakie korzyści `Counter` właściwości blokad.</span><span class="sxs-lookup"><span data-stu-id="f14c8-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f14c8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f14c8-114">See Also</span></span>  
 [<span data-ttu-id="f14c8-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="f14c8-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
