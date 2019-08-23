---
title: Zalecane Tagi dla komentarzy do dokumentacji C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: ac8629dacbb8c1fde1f55468e5d2aeaf78cfe017
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928026"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="3ed54-102">Znaczniki zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3ed54-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="3ed54-103">Kompilator przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwa została określona w opcji wiersza polecenia **/doc.** C#</span><span class="sxs-lookup"><span data-stu-id="3ed54-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="3ed54-104">Aby utworzyć ostateczną dokumentację opartą na pliku generowanym przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="3ed54-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="3ed54-105">Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="3ed54-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ed54-106">Komentarzy do dokumentacji nie można zastosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ed54-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="3ed54-107">Kompilator będzie przetwarzać dowolny tag, który jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="3ed54-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="3ed54-108">Poniższe Tagi zapewniają ogólnie używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3ed54-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="3ed54-109">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="3ed54-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="3ed54-110">\<c></span><span class="sxs-lookup"><span data-stu-id="3ed54-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="3ed54-111">\<> para</span><span class="sxs-lookup"><span data-stu-id="3ed54-111">\<para></span></span>](./para.md)|<span data-ttu-id="3ed54-112">[\<see>](./see.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="3ed54-113">\<> kodu</span><span class="sxs-lookup"><span data-stu-id="3ed54-113">\<code></span></span>](./code.md)|<span data-ttu-id="3ed54-114">[\<> param](./param.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="3ed54-115">[\<seealso>](./seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="3ed54-116">\<przykład ></span><span class="sxs-lookup"><span data-stu-id="3ed54-116">\<example></span></span>](./example.md)|[<span data-ttu-id="3ed54-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="3ed54-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="3ed54-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="3ed54-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="3ed54-119">[\<> wyjątku](./exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="3ed54-120">[\<> uprawnień](./permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="3ed54-121">[\<typeparam >](./typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="3ed54-122">[\<Uwzględnij >](./include.md)\*</span><span class="sxs-lookup"><span data-stu-id="3ed54-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="3ed54-123">\<uwagi ></span><span class="sxs-lookup"><span data-stu-id="3ed54-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="3ed54-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="3ed54-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="3ed54-125">\<list></span><span class="sxs-lookup"><span data-stu-id="3ed54-125">\<list></span></span>](./list.md)|[<span data-ttu-id="3ed54-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="3ed54-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="3ed54-127">\<value></span><span class="sxs-lookup"><span data-stu-id="3ed54-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="3ed54-128">(\* wskazuje, że kompilator weryfikuje składnię).</span><span class="sxs-lookup"><span data-stu-id="3ed54-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="3ed54-129">Jeśli chcesz, aby w tekście komentarza do dokumentacji pojawiły się nawiasy kątowe, użyj kodowania `<` HTML `>` i, `&lt;` które `&gt;` jest odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3ed54-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="3ed54-130">To kodowanie pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3ed54-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="3ed54-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ed54-131">See also</span></span>

- [<span data-ttu-id="3ed54-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3ed54-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3ed54-133">/doc (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3ed54-133">/doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="3ed54-134">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="3ed54-134">XML Documentation Comments</span></span>](./index.md)
