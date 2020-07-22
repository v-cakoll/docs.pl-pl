---
title: <see>— Przewodnik programowania w języku C#
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
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863789"
---
# <a name="see-c-programming-guide"></a><span data-ttu-id="97c98-102">\<see>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="97c98-102">\<see> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="97c98-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="97c98-103">Syntax</span></span>

```xml
<see cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="97c98-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="97c98-104">Parameters</span></span>

- <span data-ttu-id="97c98-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="97c98-105">cref = "`member`"</span></span>

  <span data-ttu-id="97c98-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="97c98-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="97c98-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="97c98-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="97c98-108">Umieść *składową* w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="97c98-108">Place *member* within double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="97c98-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97c98-109">Remarks</span></span>

<span data-ttu-id="97c98-110">`<see>`Tag pozwala określić łącze z poziomu tekstu.</span><span class="sxs-lookup"><span data-stu-id="97c98-110">The `<see>` tag lets you specify a link from within text.</span></span> <span data-ttu-id="97c98-111">Użyj [\<seealso>](./seealso.md) , aby wskazać, że tekst powinien być umieszczony w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="97c98-111">Use [\<seealso>](./seealso.md) to indicate that text should be placed in a See Also section.</span></span> <span data-ttu-id="97c98-112">Użyj [atrybutu cref](./cref-attribute.md) , aby utworzyć wewnętrzne hiperłącza do stron dokumentacji dla elementów kodu.</span><span class="sxs-lookup"><span data-stu-id="97c98-112">Use the [cref Attribute](./cref-attribute.md) to create internal hyperlinks to documentation pages for code elements.</span></span> <span data-ttu-id="97c98-113">Ponadto ``href`` jest prawidłowym atrybutem, który będzie działać jako hiperłącze.</span><span class="sxs-lookup"><span data-stu-id="97c98-113">Also, ``href`` is a valid Attribute that will function as a hyperlink.</span></span>

<span data-ttu-id="97c98-114">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="97c98-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

<span data-ttu-id="97c98-115">W poniższym przykładzie pokazano `<see>` tag w sekcji podsumowania.</span><span class="sxs-lookup"><span data-stu-id="97c98-115">The following example shows a `<see>` tag within a summary section.</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a><span data-ttu-id="97c98-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97c98-116">See also</span></span>

- [<span data-ttu-id="97c98-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="97c98-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="97c98-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="97c98-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
