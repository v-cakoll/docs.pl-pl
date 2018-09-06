---
title: '&lt;Kod&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: e66aebe35dd8f6443fefe3b07842b37270159e6e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858642"
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="b73ae-102">&lt;Kod&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b73ae-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="b73ae-103">Wskazuje, że tekst jest wiele wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="b73ae-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b73ae-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b73ae-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b73ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b73ae-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="b73ae-106">Tekst, aby oznaczyć jako kod.</span><span class="sxs-lookup"><span data-stu-id="b73ae-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b73ae-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b73ae-107">Remarks</span></span>  
 <span data-ttu-id="b73ae-108">Użyj `<code>` tag, aby wskazać wiele wierszy, jako kod.</span><span class="sxs-lookup"><span data-stu-id="b73ae-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="b73ae-109">Użyj [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) do wskazania, że tekst w opis powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="b73ae-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="b73ae-110">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b73ae-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b73ae-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b73ae-111">Example</span></span>  
 <span data-ttu-id="b73ae-112">W tym przykładzie użyto \<kodu > tag obejmujący przykładowy kod dla przy użyciu `ID` pola.</span><span class="sxs-lookup"><span data-stu-id="b73ae-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b73ae-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b73ae-113">See Also</span></span>  
 [<span data-ttu-id="b73ae-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="b73ae-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
