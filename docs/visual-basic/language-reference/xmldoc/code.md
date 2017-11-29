---
title: '&lt;Kod&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7c1d8ab3db0c36c6a2935b9ffbef15e87df5ebc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="ae8ed-102">&lt;Kod&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae8ed-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="ae8ed-103">Wskazuje, czy tekst ma wiele wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="ae8ed-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae8ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae8ed-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae8ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae8ed-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="ae8ed-106">Tekst, który chcesz oznaczyć jako kod.</span><span class="sxs-lookup"><span data-stu-id="ae8ed-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae8ed-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae8ed-107">Remarks</span></span>  
 <span data-ttu-id="ae8ed-108">Użyj `<code>` tag, aby wskazać wiele wierszy, jak kod.</span><span class="sxs-lookup"><span data-stu-id="ae8ed-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="ae8ed-109">Użyj [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) aby wskazać, że tekst opisu powinien być oznaczony jako kod.</span><span class="sxs-lookup"><span data-stu-id="ae8ed-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="ae8ed-110">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ae8ed-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae8ed-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae8ed-111">Example</span></span>  
 <span data-ttu-id="ae8ed-112">W tym przykładzie użyto \<kod > tag, aby uwzględnić przykładowy kod służący do przy użyciu `ID` pola.</span><span class="sxs-lookup"><span data-stu-id="ae8ed-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ae8ed-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae8ed-113">See Also</span></span>  
 [<span data-ttu-id="ae8ed-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="ae8ed-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
