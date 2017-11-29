---
title: "&lt;Lista&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d997f3692d21959daa8eaec9eeeac8c0a1dc9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="30492-102">&lt;Lista&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="30492-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="30492-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="30492-103">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="30492-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="30492-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="30492-105">Termin, aby zdefiniować, który zostanie zdefiniowany w `description`.</span><span class="sxs-lookup"><span data-stu-id="30492-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="30492-106">Element punktora lub Lista numerowana definicji `term`.</span><span class="sxs-lookup"><span data-stu-id="30492-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30492-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30492-107">Remarks</span></span>  
 <span data-ttu-id="30492-108">\<Listheader > Blok służy do definiowania wiersz nagłówka tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="30492-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="30492-109">Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="30492-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="30492-110">Każdy element na liście zostanie określony z \<elementu > bloku.</span><span class="sxs-lookup"><span data-stu-id="30492-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="30492-111">Podczas tworzenia listy definicji, należy określić zarówno `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="30492-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="30492-112">Jednak dla tabeli, lista punktowana lub Lista numerowana, tylko należy podać wpis dotyczący `description`.</span><span class="sxs-lookup"><span data-stu-id="30492-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="30492-113">Listy lub tabeli może mieć tyle \<elementu > blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="30492-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="30492-114">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="30492-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30492-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="30492-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="30492-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30492-116">See Also</span></span>  
 [<span data-ttu-id="30492-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30492-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="30492-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="30492-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
