---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935361"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="20d31-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20d31-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="20d31-103">Wskazuje, że tekst w ciągu opisu jest kod.</span><span class="sxs-lookup"><span data-stu-id="20d31-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20d31-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20d31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="20d31-105">Parameters</span></span>  
  
|<span data-ttu-id="20d31-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="20d31-106">Parameter</span></span>|<span data-ttu-id="20d31-107">Opis</span><span class="sxs-lookup"><span data-stu-id="20d31-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="20d31-108">Tekst, który chcesz wskazać jako kod.</span><span class="sxs-lookup"><span data-stu-id="20d31-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20d31-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20d31-109">Remarks</span></span>  
 <span data-ttu-id="20d31-110">`<c>` Tag zapewnia sposób, aby wskazać, że tekst w opis powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="20d31-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="20d31-111">Użyj [ \<kodu >](../../../visual-basic/language-reference/xmldoc/code.md) aby wskazać wiele wierszy, jako kod.</span><span class="sxs-lookup"><span data-stu-id="20d31-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="20d31-112">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="20d31-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20d31-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="20d31-113">Example</span></span>  
 <span data-ttu-id="20d31-114">W tym przykładzie użyto `<c>` tagu w sekcji podsumowania w celu wskazania, że `Counter` jest kod.</span><span class="sxs-lookup"><span data-stu-id="20d31-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="20d31-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="20d31-115">See Also</span></span>  
 [<span data-ttu-id="20d31-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="20d31-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
