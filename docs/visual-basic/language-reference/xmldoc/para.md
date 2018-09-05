---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: fa11c713a5ed5793b50865753f8bcdeaabf56e83
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534920"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="228d9-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="228d9-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="228d9-103">Określa, że zawartość jest w formacie akapitu.</span><span class="sxs-lookup"><span data-stu-id="228d9-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="228d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="228d9-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="228d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="228d9-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="228d9-106">Tekst akapitu.</span><span class="sxs-lookup"><span data-stu-id="228d9-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="228d9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="228d9-107">Remarks</span></span>  
 <span data-ttu-id="228d9-108">`<para>` Tag jest przeznaczona do użytku wewnątrz znacznik, taki jak [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md), lub [ \<zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md), i umożliwia dodawanie struktury w tekście.</span><span class="sxs-lookup"><span data-stu-id="228d9-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="228d9-109">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="228d9-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="228d9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="228d9-110">Example</span></span>  
 <span data-ttu-id="228d9-111">W tym przykładzie użyto `<para>` tagu podziału sekcję Spostrzeżenia, aby `UpdateRecord` metody do dwóch akapitach.</span><span class="sxs-lookup"><span data-stu-id="228d9-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="228d9-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="228d9-112">See Also</span></span>  
 [<span data-ttu-id="228d9-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="228d9-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
