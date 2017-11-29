---
title: '&lt;para&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e2a034974ed94b18da374fbd372063ea4d575440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="1c590-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c590-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="1c590-103">Określa, czy zawartość jest w formacie akapitu.</span><span class="sxs-lookup"><span data-stu-id="1c590-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c590-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c590-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c590-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c590-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="1c590-106">Tekst akapitu.</span><span class="sxs-lookup"><span data-stu-id="1c590-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c590-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c590-107">Remarks</span></span>  
 <span data-ttu-id="1c590-108">`<para>` Tag jest używany wewnątrz tagu, takich jak [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md), lub [ \<zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md), i umożliwia dodawanie struktury w tekście.</span><span class="sxs-lookup"><span data-stu-id="1c590-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="1c590-109">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="1c590-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c590-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c590-110">Example</span></span>  
 <span data-ttu-id="1c590-111">W tym przykładzie użyto `<para>` tagu w sekcji uwag do podziału `UpdateRecord` metody do dwóch akapitów.</span><span class="sxs-lookup"><span data-stu-id="1c590-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1c590-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c590-112">See Also</span></span>  
 [<span data-ttu-id="1c590-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="1c590-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
