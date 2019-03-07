---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: d8efd2359ecb65bec1b427d8b1dca4b0c88a1152
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469030"
---
# <a name="c-visual-basic"></a><span data-ttu-id="44aef-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44aef-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="44aef-103">Wskazuje, że tekst w ciągu opisu jest kod.</span><span class="sxs-lookup"><span data-stu-id="44aef-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44aef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44aef-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="44aef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44aef-105">Parameters</span></span>  
  
|<span data-ttu-id="44aef-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="44aef-106">Parameter</span></span>|<span data-ttu-id="44aef-107">Opis</span><span class="sxs-lookup"><span data-stu-id="44aef-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="44aef-108">Tekst, który chcesz wskazać jako kod.</span><span class="sxs-lookup"><span data-stu-id="44aef-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44aef-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44aef-109">Remarks</span></span>  
 <span data-ttu-id="44aef-110">`<c>` Tag zapewnia sposób, aby wskazać, że tekst w opis powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="44aef-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="44aef-111">Użyj [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) aby wskazać wiele wierszy, jako kod.</span><span class="sxs-lookup"><span data-stu-id="44aef-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="44aef-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="44aef-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44aef-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="44aef-113">Example</span></span>  
 <span data-ttu-id="44aef-114">W tym przykładzie użyto `<c>` tagu w sekcji podsumowania w celu wskazania, że `Counter` jest kod.</span><span class="sxs-lookup"><span data-stu-id="44aef-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="44aef-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44aef-115">See also</span></span>
- [<span data-ttu-id="44aef-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="44aef-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
