---
title: <list> - Przewodnik programowania C#
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789752"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="272a0-102">\<lista> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="272a0-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="272a0-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="272a0-103">Syntax</span></span>

```xml
<list type="bullet|number|table">
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

## <a name="parameters"></a><span data-ttu-id="272a0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="272a0-104">Parameters</span></span>

- `term`

  <span data-ttu-id="272a0-105">Termin do zdefiniowania, który `description`zostanie zdefiniowany w .</span><span class="sxs-lookup"><span data-stu-id="272a0-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="272a0-106">Element na liście punktorowej lub numerowanej `term`lub definicja .</span><span class="sxs-lookup"><span data-stu-id="272a0-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="272a0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="272a0-107">Remarks</span></span>

<span data-ttu-id="272a0-108">Blok \<> listheader służy do definiowania wiersza nagłówka tabeli lub listy definicji.</span><span class="sxs-lookup"><span data-stu-id="272a0-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="272a0-109">Podczas definiowania tabeli, należy podać tylko wpis dla terminu w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="272a0-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="272a0-110">Każdy element na liście jest \<określony z elementem> bloku.</span><span class="sxs-lookup"><span data-stu-id="272a0-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="272a0-111">Podczas tworzenia listy definicji należy określić `term` oba `description`i .</span><span class="sxs-lookup"><span data-stu-id="272a0-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="272a0-112">Jednak w przypadku tabeli, listy punktowanej lub listy numerowanej wystarczy `description`podać wpis dla .</span><span class="sxs-lookup"><span data-stu-id="272a0-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="272a0-113">Lista lub tabela może \<mieć dowolną liczbę elementów> bloków, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="272a0-113">A list or table can have as many \<item> blocks as needed.</span></span>

<span data-ttu-id="272a0-114">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="272a0-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="272a0-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="272a0-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="272a0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="272a0-116">See also</span></span>

- [<span data-ttu-id="272a0-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="272a0-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="272a0-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="272a0-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
