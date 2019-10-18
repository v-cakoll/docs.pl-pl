---
title: Zalecane Tagi dla komentarzy do dokumentacji C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: d17ff0b78d8ae40916447e8e12da7948a21e5717
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523371"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="efb3d-102">Znaczniki zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="efb3d-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="efb3d-103">Kompilator przetwarza komentarze dokumentacji w kodzie i formatuje je jako XML w pliku, którego nazwa została określona w opcji wiersza polecenia **/doc.** C#</span><span class="sxs-lookup"><span data-stu-id="efb3d-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="efb3d-104">Aby utworzyć ostateczną dokumentację opartą na pliku generowanym przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="efb3d-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="efb3d-105">Tagi są przetwarzane na konstrukcjach kodu, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="efb3d-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="efb3d-106">Komentarzy do dokumentacji nie można zastosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="efb3d-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="efb3d-107">Kompilator będzie przetwarzać dowolny tag, który jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="efb3d-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="efb3d-108">Poniższe Tagi zapewniają ogólnie używane funkcje w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="efb3d-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="efb3d-109">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="efb3d-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="efb3d-110">\<c ></span><span class="sxs-lookup"><span data-stu-id="efb3d-110">\<c></span></span>](./code-inline.md)|[<span data-ttu-id="efb3d-111">\<para ></span><span class="sxs-lookup"><span data-stu-id="efb3d-111">\<para></span></span>](./para.md)|<span data-ttu-id="efb3d-112">[\<see >](./see.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-112">[\<see>](./see.md)\*</span></span>|  
|[<span data-ttu-id="efb3d-113">\<code ></span><span class="sxs-lookup"><span data-stu-id="efb3d-113">\<code></span></span>](./code.md)|<span data-ttu-id="efb3d-114">[\<param >](./param.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-114">[\<param>](./param.md)\*</span></span>|<span data-ttu-id="efb3d-115">[\<seealso >](./seealso.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-115">[\<seealso>](./seealso.md)\*</span></span>|  
|[<span data-ttu-id="efb3d-116">\<example ></span><span class="sxs-lookup"><span data-stu-id="efb3d-116">\<example></span></span>](./example.md)|[<span data-ttu-id="efb3d-117">\<paramref ></span><span class="sxs-lookup"><span data-stu-id="efb3d-117">\<paramref></span></span>](./paramref.md)|[<span data-ttu-id="efb3d-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="efb3d-118">\<summary></span></span>](./summary.md)|  
|<span data-ttu-id="efb3d-119">[\<exception >](./exception.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-119">[\<exception>](./exception.md)\*</span></span>|<span data-ttu-id="efb3d-120">[\<permission >](./permission.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-120">[\<permission>](./permission.md)\*</span></span>|<span data-ttu-id="efb3d-121">[\<typeparam >](./typeparam.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-121">[\<typeparam>](./typeparam.md)\*</span></span>|  
|<span data-ttu-id="efb3d-122">[\<include >](./include.md) \*</span><span class="sxs-lookup"><span data-stu-id="efb3d-122">[\<include>](./include.md)\*</span></span>|[<span data-ttu-id="efb3d-123">\<remarks ></span><span class="sxs-lookup"><span data-stu-id="efb3d-123">\<remarks></span></span>](./remarks.md)|[<span data-ttu-id="efb3d-124">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="efb3d-124">\<typeparamref></span></span>](./typeparamref.md)|  
|[<span data-ttu-id="efb3d-125">\<list ></span><span class="sxs-lookup"><span data-stu-id="efb3d-125">\<list></span></span>](./list.md)|[<span data-ttu-id="efb3d-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="efb3d-126">\<returns></span></span>](./returns.md)|[<span data-ttu-id="efb3d-127">\<value></span><span class="sxs-lookup"><span data-stu-id="efb3d-127">\<value></span></span>](./value.md)|  
  
 <span data-ttu-id="efb3d-128">(\* wskazuje, że kompilator weryfikuje składnię).</span><span class="sxs-lookup"><span data-stu-id="efb3d-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="efb3d-129">Jeśli chcesz, aby nawiasy kątowe pojawiały się w tekście komentarza do dokumentacji, użyj kodowania HTML `<` i `>` `&lt;` i `&gt;` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="efb3d-129">If you want angle brackets to appear in the text of a documentation comment, use the HTML encoding of `<` and `>` which is `&lt;` and `&gt;` respectively.</span></span> <span data-ttu-id="efb3d-130">To kodowanie pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="efb3d-130">This encoding is shown in the following example:</span></span>
  
```csharp  
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```
  
## <a name="see-also"></a><span data-ttu-id="efb3d-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efb3d-131">See also</span></span>

- [<span data-ttu-id="efb3d-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="efb3d-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="efb3d-133">-doc (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="efb3d-133">-doc (C# Compiler Options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="efb3d-134">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="efb3d-134">XML Documentation Comments</span></span>](./index.md)
