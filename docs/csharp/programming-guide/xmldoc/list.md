---
title: '&lt;Lista&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 3f9d1e2b08b672ca58e96767aedaa71a8826c0ab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512435"
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="131b6-102">&lt;Lista&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="131b6-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="131b6-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="131b6-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
#### <a name="parameters"></a><span data-ttu-id="131b6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="131b6-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="131b6-105">Termin, aby zdefiniować, które są definiowane w `description`.</span><span class="sxs-lookup"><span data-stu-id="131b6-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="131b6-106">Element w punktora lub Lista numerowana lub definicji `term`.</span><span class="sxs-lookup"><span data-stu-id="131b6-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="131b6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="131b6-107">Remarks</span></span>  
 <span data-ttu-id="131b6-108">\<Listheader > Blokuj służy do definiowania wiersz nagłówka tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="131b6-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="131b6-109">Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="131b6-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="131b6-110">Każdy element na liście jest określony za pomocą \<elementu > bloku.</span><span class="sxs-lookup"><span data-stu-id="131b6-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="131b6-111">Podczas tworzenia listy definicji, musisz podać obydwie wartości `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="131b6-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="131b6-112">Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.</span><span class="sxs-lookup"><span data-stu-id="131b6-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="131b6-113">Masz tyle listy lub tabeli \<elementu > blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="131b6-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="131b6-114">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="131b6-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="131b6-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="131b6-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="131b6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="131b6-116">See Also</span></span>

- [<span data-ttu-id="131b6-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="131b6-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="131b6-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="131b6-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
