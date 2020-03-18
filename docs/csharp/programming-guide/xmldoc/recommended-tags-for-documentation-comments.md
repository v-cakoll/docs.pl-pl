---
title: Zalecane tagi do komentarzy dokumentacji - Przewodnik programowania C#
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789727"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="f65cd-102">Zalecane tagi komentarzy do dokumentacji (przewodnik programowania Języka C#)</span><span class="sxs-lookup"><span data-stu-id="f65cd-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="f65cd-103">Kompilator Języka C# przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwę określisz w opcji wiersza polecenia **/doc.**</span><span class="sxs-lookup"><span data-stu-id="f65cd-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="f65cd-104">Aby utworzyć ostateczną dokumentację na podstawie pliku wygenerowanego przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="f65cd-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="f65cd-105">Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="f65cd-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="f65cd-106">Nie można zastosować komentarzy dokumentacji do obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="f65cd-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="f65cd-107">Kompilator przetworzy dowolny tag, który jest prawidłowy mś.</span><span class="sxs-lookup"><span data-stu-id="f65cd-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="f65cd-108">Następujące tagi zawierają ogólnie używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f65cd-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="f65cd-109">Tagi</span><span class="sxs-lookup"><span data-stu-id="f65cd-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="f65cd-110">\<c></span><span class="sxs-lookup"><span data-stu-id="f65cd-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="f65cd-111">\<para></span><span class="sxs-lookup"><span data-stu-id="f65cd-111">\<para></span></span>](./para.md)|<span data-ttu-id="f65cd-112">[\<zobacz>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="f65cd-113">\<wartość></span><span class="sxs-lookup"><span data-stu-id="f65cd-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="f65cd-114">\<>kodu</span><span class="sxs-lookup"><span data-stu-id="f65cd-114">\<code></span></span>](./code.md)|<span data-ttu-id="f65cd-115">[\<param>](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="f65cd-116">[\<>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="f65cd-117">\<przykład></span><span class="sxs-lookup"><span data-stu-id="f65cd-117">\<example></span></span>](./example.md)|[<span data-ttu-id="f65cd-118">\<paramref></span><span class="sxs-lookup"><span data-stu-id="f65cd-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="f65cd-119">\<>podsumowującym</span><span class="sxs-lookup"><span data-stu-id="f65cd-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="f65cd-120">[\<>wyjątek](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="f65cd-121">[\<>uprawnień](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="f65cd-122">[\<>typuparam](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="f65cd-123">[\<obejmują>](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="f65cd-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="f65cd-124">\<uwagi></span><span class="sxs-lookup"><span data-stu-id="f65cd-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="f65cd-125">\<typparamref></span><span class="sxs-lookup"><span data-stu-id="f65cd-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="f65cd-126">\<>listy</span><span class="sxs-lookup"><span data-stu-id="f65cd-126">\<list></span></span>](./list.md)|[<span data-ttu-id="f65cd-127">\<dziedzic>zenia</span><span class="sxs-lookup"><span data-stu-id="f65cd-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="f65cd-128">\<zwraca></span><span class="sxs-lookup"><span data-stu-id="f65cd-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="f65cd-129">(\* oznacza, że kompilator weryfikuje składnię.)</span><span class="sxs-lookup"><span data-stu-id="f65cd-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="f65cd-130">Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście `<` `>` komentarza `&lt;` do `&gt;` dokumentacji, użyj kodowania HTML, a który jest i jest odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f65cd-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="f65cd-131">To kodowanie jest pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f65cd-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="f65cd-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f65cd-132">See also</span></span>

- [<span data-ttu-id="f65cd-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f65cd-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f65cd-134">-doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f65cd-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="f65cd-135">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="f65cd-135">XML documentation comments</span></span>](./index.md)
