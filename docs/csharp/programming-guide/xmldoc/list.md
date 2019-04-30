---
title: <list> - C# Przewodnik programowania
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
ms.openlocfilehash: 9ac1d749d18a9d02ce28f8cf600495f345ec0e89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61708044"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="d682b-102">\<Lista > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d682b-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d682b-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="d682b-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d682b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d682b-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="d682b-105">Termin, aby zdefiniować, które są definiowane w `description`.</span><span class="sxs-lookup"><span data-stu-id="d682b-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="d682b-106">Element w punktora lub Lista numerowana lub definicji `term`.</span><span class="sxs-lookup"><span data-stu-id="d682b-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d682b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d682b-107">Remarks</span></span>  
 <span data-ttu-id="d682b-108">\<Listheader > Blokuj służy do definiowania wiersz nagłówka tabeli lub definicji listy.</span><span class="sxs-lookup"><span data-stu-id="d682b-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="d682b-109">Podczas definiowania tabeli, wystarczy podać wpis termin w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="d682b-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="d682b-110">Każdy element na liście jest określony za pomocą \<elementu > bloku.</span><span class="sxs-lookup"><span data-stu-id="d682b-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="d682b-111">Podczas tworzenia listy definicji, musisz podać obydwie wartości `term` i `description`.</span><span class="sxs-lookup"><span data-stu-id="d682b-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="d682b-112">Jednak dla tabeli, listy punktowanej lub numerowanej, wystarczy podać wpis dla `description`.</span><span class="sxs-lookup"><span data-stu-id="d682b-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="d682b-113">Masz tyle listy lub tabeli \<elementu > blokuje zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="d682b-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="d682b-114">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="d682b-114">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d682b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d682b-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="d682b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d682b-116">See also</span></span>

- [<span data-ttu-id="d682b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d682b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d682b-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="d682b-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
