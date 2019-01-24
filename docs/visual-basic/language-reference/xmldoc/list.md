---
title: '&lt;Lista&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 8d9bcffc32a1d1670aba1ce0e7b0ff0a6dc7112d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521117"
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="3fce8-102">&lt;Lista&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fce8-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="3fce8-103">Definiuje listy lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="3fce8-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fce8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fce8-104">Syntax</span></span>  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fce8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fce8-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="3fce8-106">Typ listy.</span><span class="sxs-lookup"><span data-stu-id="3fce8-106">The type of the list.</span></span> <span data-ttu-id="3fce8-107">Musi być "bullet" na liście punktowanej we wcześniejszej, "number", dla listy numerowanej lub "table" dla tabeli dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="3fce8-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="3fce8-108">Używana tylko w przypadku `type` jest "table".</span><span class="sxs-lookup"><span data-stu-id="3fce8-108">Only used when `type` is "table."</span></span> <span data-ttu-id="3fce8-109">Termin, aby zdefiniować, która jest zdefiniowana w tagu opis.</span><span class="sxs-lookup"><span data-stu-id="3fce8-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="3fce8-110">Gdy `type` "bullet" lub "number" `description` element na liście po `type` jest "tabeli" `description` jest definicja `term`.</span><span class="sxs-lookup"><span data-stu-id="3fce8-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fce8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3fce8-111">Remarks</span></span>  
 <span data-ttu-id="3fce8-112">`<listheader>` Bloku określa nagłówek tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="3fce8-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="3fce8-113">Podczas definiowania tabeli, wystarczy podać wpis dla `term` w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="3fce8-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="3fce8-114">Każdy element na liście jest określony za pomocą `<item>` bloku.</span><span class="sxs-lookup"><span data-stu-id="3fce8-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="3fce8-115">Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="3fce8-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="3fce8-116">Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.</span><span class="sxs-lookup"><span data-stu-id="3fce8-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3fce8-117">Masz tyle listy lub tabeli `<item>` blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="3fce8-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="3fce8-118">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="3fce8-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fce8-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3fce8-119">Example</span></span>  
 <span data-ttu-id="3fce8-120">W tym przykładzie użyto `<list>` tag, aby zdefiniować listy punktowanej w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="3fce8-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3fce8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fce8-121">See also</span></span>
- [<span data-ttu-id="3fce8-122">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="3fce8-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
