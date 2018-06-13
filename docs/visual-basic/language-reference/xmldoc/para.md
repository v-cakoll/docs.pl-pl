---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cb80f4b39bee128790b311732adf1202dbbc6993
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601728"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="dfccd-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfccd-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="dfccd-103">Określa, czy zawartość jest w formacie akapitu.</span><span class="sxs-lookup"><span data-stu-id="dfccd-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfccd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfccd-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfccd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfccd-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="dfccd-106">Tekst akapitu.</span><span class="sxs-lookup"><span data-stu-id="dfccd-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfccd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfccd-107">Remarks</span></span>  
 <span data-ttu-id="dfccd-108">`<para>` Tag jest używany wewnątrz tagu, takich jak [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md), lub [ \<zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md), i umożliwia dodawanie struktury w tekście.</span><span class="sxs-lookup"><span data-stu-id="dfccd-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="dfccd-109">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="dfccd-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfccd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="dfccd-110">Example</span></span>  
 <span data-ttu-id="dfccd-111">W tym przykładzie użyto `<para>` tagu w sekcji uwag do podziału `UpdateRecord` metody do dwóch akapitów.</span><span class="sxs-lookup"><span data-stu-id="dfccd-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dfccd-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dfccd-112">See Also</span></span>  
 [<span data-ttu-id="dfccd-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="dfccd-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
