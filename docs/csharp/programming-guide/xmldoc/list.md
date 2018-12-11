---
title: '&lt;Lista&gt; - C# Programming Guide'
ms.custom: seodec18
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
ms.openlocfilehash: b960349d26a4addb5f4723bd7aa3f19b07e5f4d2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241551"
---
# <a name="ltlistgt-c-programming-guide"></a><span data-ttu-id="fefd0-102">&lt;Lista&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="fefd0-102">&lt;list&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fefd0-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="fefd0-103">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fefd0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="fefd0-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="fefd0-105">Termin, aby zdefiniować, które są definiowane w `description`.</span><span class="sxs-lookup"><span data-stu-id="fefd0-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="fefd0-106">Element w punktora lub Lista numerowana lub definicji `term`.</span><span class="sxs-lookup"><span data-stu-id="fefd0-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fefd0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fefd0-107">Remarks</span></span>  
 <span data-ttu-id="fefd0-108">\<Listheader > Blokuj służy do definiowania wiersz nagłówka tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="fefd0-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="fefd0-109">Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="fefd0-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="fefd0-110">Każdy element na liście jest określony za pomocą \<elementu > bloku.</span><span class="sxs-lookup"><span data-stu-id="fefd0-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="fefd0-111">Podczas tworzenia listy definicji, musisz podać obydwie wartości `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="fefd0-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="fefd0-112">Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.</span><span class="sxs-lookup"><span data-stu-id="fefd0-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="fefd0-113">Masz tyle listy lub tabeli \<elementu > blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="fefd0-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="fefd0-114">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="fefd0-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fefd0-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="fefd0-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fefd0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fefd0-116">See Also</span></span>

- [<span data-ttu-id="fefd0-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fefd0-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fefd0-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="fefd0-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
