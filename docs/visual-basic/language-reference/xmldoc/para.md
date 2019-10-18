---
title: <para> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: aa4e4c14717b69b9ca4595e20c768a2b91aac1e4
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524740"
---
# <a name="para-visual-basic"></a><span data-ttu-id="51139-102">> \<para (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51139-102">\<para> (Visual Basic)</span></span>
<span data-ttu-id="51139-103">Określa, że zawartość jest sformatowana w akapicie.</span><span class="sxs-lookup"><span data-stu-id="51139-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51139-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51139-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="51139-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51139-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="51139-106">Tekst akapitu.</span><span class="sxs-lookup"><span data-stu-id="51139-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51139-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51139-107">Remarks</span></span>  
 <span data-ttu-id="51139-108">Tag `<para>` jest używany wewnątrz tagu, takiego jak [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md)lub [\<returns](../../../visual-basic/language-reference/xmldoc/returns.md)>, i umożliwia dodanie struktury do tekstu.</span><span class="sxs-lookup"><span data-stu-id="51139-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="51139-109">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="51139-109">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51139-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="51139-110">Example</span></span>  
 <span data-ttu-id="51139-111">W tym przykładzie używa znacznika `<para>`, aby podzielić sekcję Uwagi dla metody `UpdateRecord` na dwa akapity.</span><span class="sxs-lookup"><span data-stu-id="51139-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="51139-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51139-112">See also</span></span>

- [<span data-ttu-id="51139-113">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="51139-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
