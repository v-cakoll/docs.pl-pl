---
title: <list>
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
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352321"
---
# <a name="list-visual-basic"></a><span data-ttu-id="e692f-101">> listy \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e692f-101">\<list> (Visual Basic)</span></span>
<span data-ttu-id="e692f-102">Definiuje listę lub tabelę.</span><span class="sxs-lookup"><span data-stu-id="e692f-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e692f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e692f-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e692f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e692f-104">Parameters</span></span>  
 `type`  
 <span data-ttu-id="e692f-105">Typ listy.</span><span class="sxs-lookup"><span data-stu-id="e692f-105">The type of the list.</span></span> <span data-ttu-id="e692f-106">Musi być "punktorem" dla listy punktowanej, "number" dla listy numerowanej lub "Table" dla jednokolumnowej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e692f-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="e692f-107">Używane tylko wtedy, gdy `type` jest "Table".</span><span class="sxs-lookup"><span data-stu-id="e692f-107">Only used when `type` is "table."</span></span> <span data-ttu-id="e692f-108">Termin do zdefiniowania, który jest zdefiniowany w tagu Description.</span><span class="sxs-lookup"><span data-stu-id="e692f-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="e692f-109">Gdy `type` jest "punktor" lub "number", `description` jest pozycją na liście, gdy `type` jest "Tabela", `description` jest definicją `term`.</span><span class="sxs-lookup"><span data-stu-id="e692f-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e692f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e692f-110">Remarks</span></span>  
 <span data-ttu-id="e692f-111">Blok `<listheader>` definiuje nagłówek tabeli lub listy definicji.</span><span class="sxs-lookup"><span data-stu-id="e692f-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="e692f-112">Podczas definiowania tabeli należy tylko podać wpis dla `term` w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="e692f-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="e692f-113">Każdy element na liście jest określany za pomocą bloku `<item>`.</span><span class="sxs-lookup"><span data-stu-id="e692f-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="e692f-114">Podczas tworzenia listy definicji należy określić zarówno `term`, jak i `description`.</span><span class="sxs-lookup"><span data-stu-id="e692f-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="e692f-115">Jednak w przypadku tabeli, listy punktowanej lub listy numerowanej trzeba podać tylko wpis dla `description`.</span><span class="sxs-lookup"><span data-stu-id="e692f-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="e692f-116">Lista lub tabela może zawierać dowolną liczbę bloków `<item>` w zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="e692f-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="e692f-117">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e692f-117">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e692f-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e692f-118">Example</span></span>  
 <span data-ttu-id="e692f-119">W tym przykładzie używa znacznika `<list>`, aby zdefiniować listę punktowaną w sekcji uwagi.</span><span class="sxs-lookup"><span data-stu-id="e692f-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e692f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e692f-120">See also</span></span>

- [<span data-ttu-id="e692f-121">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="e692f-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
