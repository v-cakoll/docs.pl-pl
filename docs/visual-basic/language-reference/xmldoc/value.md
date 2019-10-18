---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 516ff6ba534478d066b8ca06baee46bdd4b35265
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524604"
---
# <a name="value-visual-basic"></a><span data-ttu-id="e3b9c-102">> \<value (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3b9c-102">\<value> (Visual Basic)</span></span>
<span data-ttu-id="e3b9c-103">Określa opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-103">Specifies the description of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3b9c-104">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3b9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3b9c-105">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="e3b9c-106">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-106">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3b9c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3b9c-107">Remarks</span></span>  
 <span data-ttu-id="e3b9c-108">Użyj znacznika `<value>`, aby opisać właściwość.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-108">Use the `<value>` tag to describe a property.</span></span> <span data-ttu-id="e3b9c-109">Należy pamiętać, że po dodaniu właściwości przy użyciu kreatora kodu w środowisku deweloperskim programu Visual Studio zostanie dodany tag [> \<summary](../../../visual-basic/language-reference/xmldoc/summary.md) dla nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-109">Note that when you add a property using the code wizard in the Visual Studio development environment, it will add a [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="e3b9c-110">Następnie należy ręcznie dodać tag `<value>`, aby opisać wartość, którą reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-110">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="e3b9c-111">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3b9c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3b9c-112">Example</span></span>  
 <span data-ttu-id="e3b9c-113">W tym przykładzie używa znacznika `<value>` do opisania wartości właściwości `Counter`.</span><span class="sxs-lookup"><span data-stu-id="e3b9c-113">This example uses the `<value>` tag to describe what value the `Counter` property holds.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e3b9c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3b9c-114">See also</span></span>

- [<span data-ttu-id="e3b9c-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e3b9c-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
