---
title: <seealso> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093464"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="ee3f5-102">\<seealso> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="ee3f5-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="ee3f5-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee3f5-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="ee3f5-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee3f5-104">Parameters</span></span>

- <span data-ttu-id="ee3f5-105">cref = `member`" "</span><span class="sxs-lookup"><span data-stu-id="ee3f5-105">cref = " `member`"</span></span>

  <span data-ttu-id="ee3f5-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ee3f5-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ee3f5-107">Kompilator sprawdza, czy istnieje `member` dany element kodu i przekazuje do nazwy elementu w wyjściowym pliku XML.`member`</span><span class="sxs-lookup"><span data-stu-id="ee3f5-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="ee3f5-108">muszą znajdować się w cudzysłowie podwójnym (" ").</span><span class="sxs-lookup"><span data-stu-id="ee3f5-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="ee3f5-109">Aby uzyskać informacje na temat tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="ee3f5-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="ee3f5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee3f5-110">Remarks</span></span>

<span data-ttu-id="ee3f5-111">Znacznik \<seealso> umożliwia określenie tekstu, który może być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="ee3f5-111">The \<seealso> tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="ee3f5-112">Użyj [ \<>,](./see.md) aby określić łącze z poziomu tekstu.</span><span class="sxs-lookup"><span data-stu-id="ee3f5-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="ee3f5-113">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ee3f5-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="ee3f5-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee3f5-114">Example</span></span>

<span data-ttu-id="ee3f5-115">Zobacz [ \<podsumowanie>](./summary.md) przykład \<użyciem seealso>.</span><span class="sxs-lookup"><span data-stu-id="ee3f5-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee3f5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee3f5-116">See also</span></span>

- [<span data-ttu-id="ee3f5-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ee3f5-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="ee3f5-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="ee3f5-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
