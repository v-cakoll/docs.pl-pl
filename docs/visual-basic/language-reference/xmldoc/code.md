---
title: '&lt;Kod&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="41ee8-102">&lt;Kod&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41ee8-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="41ee8-103">Wskazuje, czy tekst ma wiele wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="41ee8-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ee8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41ee8-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41ee8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="41ee8-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="41ee8-106">Tekst, który chcesz oznaczyć jako kod.</span><span class="sxs-lookup"><span data-stu-id="41ee8-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41ee8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41ee8-107">Remarks</span></span>  
 <span data-ttu-id="41ee8-108">Użyj `<code>` tag, aby wskazać wiele wierszy, jak kod.</span><span class="sxs-lookup"><span data-stu-id="41ee8-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="41ee8-109">Użyj [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) aby wskazać, że tekst opisu powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="41ee8-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="41ee8-110">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="41ee8-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41ee8-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="41ee8-111">Example</span></span>  
 <span data-ttu-id="41ee8-112">W tym przykładzie użyto \<kod > tag, aby uwzględnić przykładowy kod służący do przy użyciu `ID` pola.</span><span class="sxs-lookup"><span data-stu-id="41ee8-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="41ee8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41ee8-113">See Also</span></span>  
 [<span data-ttu-id="41ee8-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="41ee8-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
