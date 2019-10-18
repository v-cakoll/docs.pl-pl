---
title: <list> — C# Przewodnik programowania
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
ms.openlocfilehash: 0df6653171aa0366f555c39e4644f13b2b7384f9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523430"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="ff3d5-102">\<list > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="ff3d5-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ff3d5-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff3d5-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ff3d5-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff3d5-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="ff3d5-105">Termin do zdefiniowania, który zostanie zdefiniowany w `description`.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="ff3d5-106">Element na liście punktowanej lub numerowanej lub definicji `term`.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff3d5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff3d5-107">Remarks</span></span>  
 <span data-ttu-id="ff3d5-108">Blok > \<listheader jest używany do definiowania wiersza nagłówka tabeli lub listy definicji.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="ff3d5-109">Podczas definiowania tabeli należy podać tylko wpis dla terminu w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="ff3d5-110">Każdy element na liście jest określany za pomocą bloku \<item >.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="ff3d5-111">Podczas tworzenia listy definicji należy określić zarówno `term`, jak i `description`.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="ff3d5-112">Jednak dla tabeli, listy punktowanej lub listy numerowanej należy podać tylko wpis dla `description`.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="ff3d5-113">Lista lub tabela może zawierać dowolną liczbę \<item > bloków.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="ff3d5-114">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ff3d5-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff3d5-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff3d5-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ff3d5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff3d5-116">See also</span></span>

- [<span data-ttu-id="ff3d5-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ff3d5-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ff3d5-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="ff3d5-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
