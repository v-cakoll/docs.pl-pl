---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 510b00d2220b9c65b0e2b8fa3ead70925a9f54ba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821923"
---
# <a name="example-visual-basic"></a><span data-ttu-id="64443-102">\<przykład > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64443-102">\<example> (Visual Basic)</span></span>
<span data-ttu-id="64443-103">Określa przykład dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="64443-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64443-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64443-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a><span data-ttu-id="64443-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64443-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="64443-106">Opis przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="64443-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64443-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64443-107">Remarks</span></span>  
 <span data-ttu-id="64443-108">`<example>` Należy określić przykładem przedstawiającym sposób użycia metody lub innego członka biblioteki.</span><span class="sxs-lookup"><span data-stu-id="64443-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="64443-109">Często wiąże się to przy użyciu [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) tagu.</span><span class="sxs-lookup"><span data-stu-id="64443-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="64443-110">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="64443-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64443-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="64443-111">Example</span></span>  
 <span data-ttu-id="64443-112">W tym przykładzie użyto `<example>` tag, aby uwzględnić przykład za pomocą `ID` pola.</span><span class="sxs-lookup"><span data-stu-id="64443-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="64443-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64443-113">See also</span></span>

- [<span data-ttu-id="64443-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="64443-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
