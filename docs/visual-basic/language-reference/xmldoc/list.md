---
title: '&lt;Lista&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="88d7a-102">&lt;Lista&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88d7a-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="88d7a-103">Definiuje listy lub tabeli.</span><span class="sxs-lookup"><span data-stu-id="88d7a-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d7a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88d7a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="88d7a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88d7a-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="88d7a-106">Typ listy.</span><span class="sxs-lookup"><span data-stu-id="88d7a-106">The type of the list.</span></span> <span data-ttu-id="88d7a-107">Musi być "bullet" do listy punktowanej, "numer" Lista numerowana lub "Tabela" dla tabeli dwie kolumny.</span><span class="sxs-lookup"><span data-stu-id="88d7a-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="88d7a-108">Używana tylko w przypadku `type` jest "table".</span><span class="sxs-lookup"><span data-stu-id="88d7a-108">Only used when `type` is "table."</span></span> <span data-ttu-id="88d7a-109">Termin Aby zdefiniować, który jest zdefiniowany w tagu opis.</span><span class="sxs-lookup"><span data-stu-id="88d7a-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="88d7a-110">Gdy `type` "bullet" lub "number" `description` jest pozycją na liście po `type` jest "tabeli" `description` znajduje się definicja metody `term`.</span><span class="sxs-lookup"><span data-stu-id="88d7a-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88d7a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88d7a-111">Remarks</span></span>  
 <span data-ttu-id="88d7a-112">`<listheader>` Bloku definiuje nagłówek tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="88d7a-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="88d7a-113">Podczas definiowania tabeli, wystarczy podać wpis dotyczący `term` w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="88d7a-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="88d7a-114">Każdy element na liście zostanie określony z `<item>` bloku.</span><span class="sxs-lookup"><span data-stu-id="88d7a-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="88d7a-115">Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="88d7a-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="88d7a-116">Jednak dla tabeli, lista punktowana lub Lista numerowana, wystarczy podać wpis dotyczący `description`.</span><span class="sxs-lookup"><span data-stu-id="88d7a-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="88d7a-117">Listy lub tabeli może mieć tyle `<item>` blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="88d7a-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="88d7a-118">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="88d7a-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88d7a-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="88d7a-119">Example</span></span>  
 <span data-ttu-id="88d7a-120">W tym przykładzie użyto `<list>` tag do definiowania listy punktowanej w sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="88d7a-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="88d7a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88d7a-121">See Also</span></span>  
 [<span data-ttu-id="88d7a-122">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="88d7a-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
