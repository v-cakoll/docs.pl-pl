---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400076"
---
# <a name="para-visual-basic"></a><span data-ttu-id="c5b16-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5b16-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="c5b16-102">Określa, że zawartość jest sformatowana w akapicie.</span><span class="sxs-lookup"><span data-stu-id="c5b16-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5b16-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5b16-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5b16-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5b16-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="c5b16-105">Tekst akapitu.</span><span class="sxs-lookup"><span data-stu-id="c5b16-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5b16-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5b16-106">Remarks</span></span>  
 <span data-ttu-id="c5b16-107">`<para>`Tag jest używany wewnątrz tagu, takiego jak [\<summary>](summary.md) , [\<remarks>](remarks.md) , lub [\<returns>](returns.md) , i umożliwia dodanie struktury do tekstu.</span><span class="sxs-lookup"><span data-stu-id="c5b16-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="c5b16-108">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="c5b16-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5b16-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5b16-109">Example</span></span>  
 <span data-ttu-id="c5b16-110">Ten przykład używa `<para>` znacznika, aby podzielić sekcję Uwagi dla `UpdateRecord` metody na dwa akapity.</span><span class="sxs-lookup"><span data-stu-id="c5b16-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="c5b16-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5b16-111">See also</span></span>

- [<span data-ttu-id="c5b16-112">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="c5b16-112">XML Comment Tags</span></span>](index.md)
