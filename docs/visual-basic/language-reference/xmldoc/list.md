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
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="24398-102">&lt;Lista&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24398-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="24398-103">Definiuje listy lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="24398-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24398-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24398-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="24398-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24398-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="24398-106">Typ listy.</span><span class="sxs-lookup"><span data-stu-id="24398-106">The type of the list.</span></span> <span data-ttu-id="24398-107">Musi być "bullet" do listy punktowanej, "numer" Lista numerowana lub "Tabela" dla tabeli dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="24398-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="24398-108">Używana tylko w przypadku `type` jest "table".</span><span class="sxs-lookup"><span data-stu-id="24398-108">Only used when `type` is "table."</span></span> <span data-ttu-id="24398-109">Termin Aby zdefiniować, który jest zdefiniowany w tagu opis.</span><span class="sxs-lookup"><span data-stu-id="24398-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="24398-110">Gdy `type` "bullet" lub "number" `description` jest pozycją na liście po `type` jest "tabeli" `description` znajduje się definicja metody `term`.</span><span class="sxs-lookup"><span data-stu-id="24398-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24398-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24398-111">Remarks</span></span>  
 <span data-ttu-id="24398-112">`<listheader>` Bloku definiuje nagłówek tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="24398-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="24398-113">Podczas definiowania tabeli, wystarczy podać wpis dotyczący `term` w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="24398-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="24398-114">Każdy element na liście zostanie określony z `<item>` bloku.</span><span class="sxs-lookup"><span data-stu-id="24398-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="24398-115">Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="24398-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="24398-116">Jednak dla tabeli, lista punktowana lub Lista numerowana, wystarczy podać wpis dotyczący `description`.</span><span class="sxs-lookup"><span data-stu-id="24398-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="24398-117">Listy lub tabeli może mieć tyle `<item>` blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="24398-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="24398-118">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="24398-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24398-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="24398-119">Example</span></span>  
 <span data-ttu-id="24398-120">W tym przykładzie użyto `<list>` tag do definiowania listy punktowanej w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="24398-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="24398-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24398-121">See Also</span></span>  
 [<span data-ttu-id="24398-122">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="24398-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
