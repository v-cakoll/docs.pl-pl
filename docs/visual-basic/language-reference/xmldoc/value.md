---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 240c2131179420834e6dade729ee631c0d7811a4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352172"
---
# <a name="value-visual-basic"></a><span data-ttu-id="d757f-101">> wartości \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d757f-101">\<value> (Visual Basic)</span></span>
<span data-ttu-id="d757f-102">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="d757f-102">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d757f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="d757f-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="d757f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d757f-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="d757f-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="d757f-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d757f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d757f-106">Remarks</span></span>  
 <span data-ttu-id="d757f-107">Użyj znacznika `<value>`, aby opisać właściwość.</span><span class="sxs-lookup"><span data-stu-id="d757f-107">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="d757f-108">Należy pamiętać, że po dodaniu właściwości przy użyciu kreatora kodu w środowisku deweloperskim programu Visual Studio zostanie dodany tag [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) dla nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d757f-108">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="d757f-109">Następnie należy ręcznie dodać tag `<value>`, aby opisać wartość, którą reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="d757f-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="d757f-110">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="d757f-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d757f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d757f-111">Example</span></span>  
 <span data-ttu-id="d757f-112">W tym przykładzie używa znacznika `<value>` do opisania wartości właściwości `Counter`.</span><span class="sxs-lookup"><span data-stu-id="d757f-112">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d757f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d757f-113">See also</span></span>

- [<span data-ttu-id="d757f-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="d757f-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
