---
title: <see>- Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: f4834f88c646b44269f8290c2ad08698c34e714a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627675"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="02002-102">\<zobacz> (przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="02002-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="02002-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="02002-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="02002-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="02002-104">Parameters</span></span>

- <span data-ttu-id="02002-105">cref =`member`" "</span><span class="sxs-lookup"><span data-stu-id="02002-105">cref = "`member`"</span></span>

  <span data-ttu-id="02002-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="02002-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="02002-107">Kompilator sprawdza, czy istnieje `member` dany element kodu i przekazuje do nazwy elementu w wyjściowym pliku XML.</span><span class="sxs-lookup"><span data-stu-id="02002-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="02002-108">Umieść *element członkowski* w cudzysłowie podwójnym (" ").</span><span class="sxs-lookup"><span data-stu-id="02002-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="02002-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02002-109">Remarks</span></span>

<span data-ttu-id="02002-110">Znacznik \<> zobacz umożliwia określenie łącza z poziomu tekstu.</span><span class="sxs-lookup"><span data-stu-id="02002-110">The \<see> tag lets you specify a link from within text.</span></span> <span data-ttu-id="02002-111">Użyj [ \<seealso>,](./seealso.md) aby wskazać, że tekst powinien być umieszczony w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="02002-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="02002-112">Użyj [atrybutu cref,](./cref-attribute.md) aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.</span><span class="sxs-lookup"><span data-stu-id="02002-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="02002-113">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="02002-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="02002-114">W poniższym \<przykładzie przedstawiono znacznik> w sekcji podsumowania.</span><span class="sxs-lookup"><span data-stu-id="02002-114">The following example shows a \<see> tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="02002-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02002-115">See also</span></span>

- [<span data-ttu-id="02002-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="02002-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="02002-117">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="02002-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
