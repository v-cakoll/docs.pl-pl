---
title: <seealso> — Przewodnik programowania w języku C#
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
ms.openlocfilehash: 1b801ac1b5a0a59d97ccc35ec78930d99223e846
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287223"
---
# <a name="seealso-c-programming-guide"></a><span data-ttu-id="35f5a-102">\<seealso>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="35f5a-102">\<seealso> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="35f5a-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="35f5a-103">Syntax</span></span>

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a><span data-ttu-id="35f5a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="35f5a-104">Parameters</span></span>

- <span data-ttu-id="35f5a-105">cref = " `member` "</span><span class="sxs-lookup"><span data-stu-id="35f5a-105">cref = " `member`"</span></span>

  <span data-ttu-id="35f5a-106">Odwołanie do elementu członkowskiego lub pola, które jest dostępne do wywołania z bieżącego środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="35f5a-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="35f5a-107">Kompilator sprawdza, czy dany element kodu istnieje i przekazuje `member` do nazwy elementu w wyjściowym kodzie XML.`member`</span><span class="sxs-lookup"><span data-stu-id="35f5a-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.`member`</span></span> <span data-ttu-id="35f5a-108">musi znajdować się w podwójnym cudzysłowie ("").</span><span class="sxs-lookup"><span data-stu-id="35f5a-108">must appear within double quotation marks (" ").</span></span>

  <span data-ttu-id="35f5a-109">Aby uzyskać informacje na temat sposobu tworzenia odwołania cref do typu ogólnego, zobacz [atrybut cref](./cref-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="35f5a-109">For information on how to create a cref reference to a generic type, see [cref attribute](./cref-attribute.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="35f5a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35f5a-110">Remarks</span></span>

<span data-ttu-id="35f5a-111">`<seealso>`Tag pozwala określić tekst, który może być wyświetlany w sekcji Zobacz też.</span><span class="sxs-lookup"><span data-stu-id="35f5a-111">The `<seealso>` tag lets you specify the text that you might want to appear in a See Also section.</span></span> <span data-ttu-id="35f5a-112">Służy [\<see>](./see.md) do określania linku w tekście.</span><span class="sxs-lookup"><span data-stu-id="35f5a-112">Use [\<see>](./see.md) to specify a link from within text.</span></span>

<span data-ttu-id="35f5a-113">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="35f5a-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="35f5a-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="35f5a-114">Example</span></span>

<span data-ttu-id="35f5a-115">Zobacz [\<summary>](./summary.md) , aby zobaczyć przykład użycia \<seealso> .</span><span class="sxs-lookup"><span data-stu-id="35f5a-115">See [\<summary>](./summary.md) for an example of using \<seealso>.</span></span>

## <a name="see-also"></a><span data-ttu-id="35f5a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35f5a-116">See also</span></span>

- [<span data-ttu-id="35f5a-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="35f5a-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="35f5a-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="35f5a-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
