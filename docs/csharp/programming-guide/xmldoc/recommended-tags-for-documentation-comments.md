---
title: Zalecane Tagi dla komentarzy do dokumentacji C# — Przewodnik programowania
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789727"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="3cade-102">Zalecane Tagi dla komentarzy do dokumentacjiC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="3cade-102">Recommended tags for documentation comments (C# programming guide)</span></span>

<span data-ttu-id="3cade-103">Kompilator przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwa została określona w opcji wiersza polecenia **/doc.** C#</span><span class="sxs-lookup"><span data-stu-id="3cade-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="3cade-104">Aby utworzyć ostateczną dokumentację opartą na pliku generowanym przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="3cade-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

<span data-ttu-id="3cade-105">Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="3cade-105">Tags are processed on code constructs such as types and type members.</span></span>

> [!NOTE]
> <span data-ttu-id="3cade-106">Komentarzy do dokumentacji nie można zastosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3cade-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="3cade-107">Kompilator będzie przetwarzać dowolny tag, który jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="3cade-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="3cade-108">Poniższe Tagi zapewniają ogólnie używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3cade-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="3cade-109">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="3cade-109">Tags</span></span>  
  
|||||  
|---|---|---|---|
|[<span data-ttu-id="3cade-110">\<c></span><span class="sxs-lookup"><span data-stu-id="3cade-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="3cade-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="3cade-111">\<para></span></span>](./para.md)|<span data-ttu-id="3cade-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-112">[\<see>](./see.md)\*</span></span>|[<span data-ttu-id="3cade-113">\<value></span><span class="sxs-lookup"><span data-stu-id="3cade-113">\<value></span></span>](./value.md)  
|[<span data-ttu-id="3cade-114">> kodu \<</span><span class="sxs-lookup"><span data-stu-id="3cade-114">\<code></span></span>](./code.md)|<span data-ttu-id="3cade-115">[\<param >](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-115">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="3cade-116">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-116">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="3cade-117">przykład \<</span><span class="sxs-lookup"><span data-stu-id="3cade-117">\<example></span></span>](./example.md)|[<span data-ttu-id="3cade-118">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="3cade-118">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="3cade-119">\<summary></span><span class="sxs-lookup"><span data-stu-id="3cade-119">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="3cade-120">[\<> wyjątków](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-120">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="3cade-121">[> uprawnień\<](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-121">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="3cade-122">[\<typeparam >](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-122">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="3cade-123">[\<uwzględnić >](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="3cade-123">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="3cade-124">\<uwagi ></span><span class="sxs-lookup"><span data-stu-id="3cade-124">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="3cade-125">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="3cade-125">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="3cade-126">\<list></span><span class="sxs-lookup"><span data-stu-id="3cade-126">\<list></span></span>](./list.md)|[<span data-ttu-id="3cade-127">\<inheritdoc ></span><span class="sxs-lookup"><span data-stu-id="3cade-127">\<inheritdoc></span></span>](./inheritdoc.md)|[<span data-ttu-id="3cade-128">\<returns></span><span class="sxs-lookup"><span data-stu-id="3cade-128">\<returns></span></span>](./returns.md)|
  
<span data-ttu-id="3cade-129">(\* oznacza, że kompilator weryfikuje składnię).</span><span class="sxs-lookup"><span data-stu-id="3cade-129">(\* denotes that the compiler verifies syntax.)</span></span>

<span data-ttu-id="3cade-130">Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj kodowania HTML `<` i `>` `&lt;` i `&gt;` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3cade-130">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="3cade-131">To kodowanie jest pokazane w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3cade-131">This encoding is shown in the following example.</span></span>

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a><span data-ttu-id="3cade-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cade-132">See also</span></span>

- [<span data-ttu-id="3cade-133">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="3cade-133">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="3cade-134">-doc (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3cade-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="3cade-135">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="3cade-135">XML documentation comments</span></span>](./index.md)
