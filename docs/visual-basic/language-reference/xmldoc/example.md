---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f28dbf19bc03cb9d91323e9fa43a7081c1990db
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524006"
---
# <a name="example-visual-basic"></a><span data-ttu-id="e5f9b-102">> \<example (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5f9b-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="e5f9b-103">Określa przykład dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e5f9b-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5f9b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5f9b-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5f9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5f9b-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="e5f9b-106">Opis przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="e5f9b-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5f9b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5f9b-107">Remarks</span></span>  
 <span data-ttu-id="e5f9b-108">Tag `<example>` pozwala określić przykład użycia metody lub innego elementu członkowskiego biblioteki.</span><span class="sxs-lookup"><span data-stu-id="e5f9b-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="e5f9b-109">Ten proces często obejmuje użycie tagu [> \<code](../../../visual-basic/language-reference/xmldoc/code.md) .</span><span class="sxs-lookup"><span data-stu-id="e5f9b-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="e5f9b-110">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e5f9b-110">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5f9b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5f9b-111">Example</span></span>  
 <span data-ttu-id="e5f9b-112">W tym przykładzie użyto znacznika `<example>`, aby uwzględnić przykład użycia pola `ID`.</span><span class="sxs-lookup"><span data-stu-id="e5f9b-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e5f9b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5f9b-113">See also</span></span>

- [<span data-ttu-id="e5f9b-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e5f9b-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
