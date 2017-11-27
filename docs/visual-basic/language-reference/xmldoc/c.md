---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="70119-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70119-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="70119-103">Wskazuje, że tekst opisu jest kod.</span><span class="sxs-lookup"><span data-stu-id="70119-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70119-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70119-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70119-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70119-105">Parameters</span></span>  
  
|<span data-ttu-id="70119-106">Parametr</span><span class="sxs-lookup"><span data-stu-id="70119-106">Parameter</span></span>|<span data-ttu-id="70119-107">Opis</span><span class="sxs-lookup"><span data-stu-id="70119-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="70119-108">Tekst, który chcesz wskazać jako kod.</span><span class="sxs-lookup"><span data-stu-id="70119-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70119-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70119-109">Remarks</span></span>  
 <span data-ttu-id="70119-110">`<c>` Tag zapewnia sposób, aby wskazać, że tekst opisu powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="70119-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="70119-111">Użyj [ \<kod >](../../../visual-basic/language-reference/xmldoc/code.md) wskazująca wiele wierszy, jak kod.</span><span class="sxs-lookup"><span data-stu-id="70119-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="70119-112">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="70119-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70119-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="70119-113">Example</span></span>  
 <span data-ttu-id="70119-114">W tym przykładzie użyto `<c>` tagu w sekcji podsumowania, aby wskazać, że `Counter` jest kod.</span><span class="sxs-lookup"><span data-stu-id="70119-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="70119-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70119-115">See Also</span></span>  
 [<span data-ttu-id="70119-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="70119-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
