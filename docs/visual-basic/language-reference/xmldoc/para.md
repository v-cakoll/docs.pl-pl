---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 96ef62d53fd1cc806c0dc72d2d0781b1c6297dc6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970873"
---
# <a name="para-visual-basic"></a><span data-ttu-id="e4513-102">\<para > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4513-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="e4513-103">Określa, że zawartość jest w formacie akapitu.</span><span class="sxs-lookup"><span data-stu-id="e4513-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4513-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4513-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4513-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4513-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="e4513-106">Tekst akapitu.</span><span class="sxs-lookup"><span data-stu-id="e4513-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4513-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4513-107">Remarks</span></span>  
 <span data-ttu-id="e4513-108">`<para>` Tag jest przeznaczona do użytku wewnątrz znacznik, taki jak [ \<podsumowania >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md), lub [ \<zwraca >](../../../visual-basic/language-reference/xmldoc/returns.md), i umożliwia dodawanie struktury w tekście.</span><span class="sxs-lookup"><span data-stu-id="e4513-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="e4513-109">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e4513-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4513-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="e4513-110">Example</span></span>  
 <span data-ttu-id="e4513-111">W tym przykładzie użyto `<para>` tagu podziału sekcję Spostrzeżenia, aby `UpdateRecord` metody do dwóch akapitach.</span><span class="sxs-lookup"><span data-stu-id="e4513-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e4513-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4513-112">See also</span></span>
- [<span data-ttu-id="e4513-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e4513-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
