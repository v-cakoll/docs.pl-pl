---
title: Zalecane tagi przeznaczone do komentarzy dokumentacji - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: a6d07b6c288ebbe24c9cf5c531ef333946855f82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675848"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a><span data-ttu-id="a516b-102">Znaczniki zalecane dla komentarzy do dokumentacji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a516b-102">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="a516b-103">Kompilator języka C# przetwarza komentarze dokumentacji w kodzie i sformatuje je jako kod XML w pliku o nazwie określonej w **/doc** opcji wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a516b-103">The C# compiler processes documentation comments in your code and formats them as XML in a file whose name you specify in the **/doc** command-line option.</span></span> <span data-ttu-id="a516b-104">Aby utworzyć dokumentację na podstawie pliku generowanych przez kompilator, można utworzyć narzędzie niestandardowe, lub użyj narzędzia takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="a516b-104">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="a516b-105">Tagi są przetwarzane na kodzie konstrukcji, takich jak typy i elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="a516b-105">Tags are processed on code constructs such as types and type members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a516b-106">Komentarze dokumentacji nie można zastosować do przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a516b-106">Documentation comments cannot be applied to a namespace.</span></span>  
  
 <span data-ttu-id="a516b-107">Kompilator przetworzy dowolnymi tagami, które jest prawidłowym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="a516b-107">The compiler will process any tag that is valid XML.</span></span> <span data-ttu-id="a516b-108">Następujące znaczniki oferuje powszechnie używanych w dokumentacji użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a516b-108">The following tags provide generally used functionality in user documentation.</span></span>  
  
## <a name="tags"></a><span data-ttu-id="a516b-109">Znaczniki</span><span class="sxs-lookup"><span data-stu-id="a516b-109">Tags</span></span>  
  
||||  
|---|---|---|  
|[<span data-ttu-id="a516b-110">\<c></span><span class="sxs-lookup"><span data-stu-id="a516b-110">\<c></span></span>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[<span data-ttu-id="a516b-111">\<para></span><span class="sxs-lookup"><span data-stu-id="a516b-111">\<para></span></span>](../../../csharp/programming-guide/xmldoc/para.md)|<span data-ttu-id="a516b-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-112">[\<see>](../../../csharp/programming-guide/xmldoc/see.md)\*</span></span>|  
|[<span data-ttu-id="a516b-113">\<code></span><span class="sxs-lookup"><span data-stu-id="a516b-113">\<code></span></span>](../../../csharp/programming-guide/xmldoc/code.md)|<span data-ttu-id="a516b-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-114">[\<param>](../../../csharp/programming-guide/xmldoc/param.md)\*</span></span>|<span data-ttu-id="a516b-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-115">[\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md)\*</span></span>|  
|[<span data-ttu-id="a516b-116">\<przykład ></span><span class="sxs-lookup"><span data-stu-id="a516b-116">\<example></span></span>](../../../csharp/programming-guide/xmldoc/example.md)|[<span data-ttu-id="a516b-117">\<paramref></span><span class="sxs-lookup"><span data-stu-id="a516b-117">\<paramref></span></span>](../../../csharp/programming-guide/xmldoc/paramref.md)|[<span data-ttu-id="a516b-118">\<summary></span><span class="sxs-lookup"><span data-stu-id="a516b-118">\<summary></span></span>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|<span data-ttu-id="a516b-119">[\<wyjątku >](../../../csharp/programming-guide/xmldoc/exception.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-119">[\<exception>](../../../csharp/programming-guide/xmldoc/exception.md)\*</span></span>|<span data-ttu-id="a516b-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-120">[\<permission>](../../../csharp/programming-guide/xmldoc/permission.md)\*</span></span>|<span data-ttu-id="a516b-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-121">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*</span></span>|  
|<span data-ttu-id="a516b-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span><span class="sxs-lookup"><span data-stu-id="a516b-122">[\<include>](../../../csharp/programming-guide/xmldoc/include.md)\*</span></span>|[<span data-ttu-id="a516b-123">\<Remarks ></span><span class="sxs-lookup"><span data-stu-id="a516b-123">\<remarks></span></span>](../../../csharp/programming-guide/xmldoc/remarks.md)|[<span data-ttu-id="a516b-124">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="a516b-124">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[<span data-ttu-id="a516b-125">\<list></span><span class="sxs-lookup"><span data-stu-id="a516b-125">\<list></span></span>](../../../csharp/programming-guide/xmldoc/list.md)|[<span data-ttu-id="a516b-126">\<returns></span><span class="sxs-lookup"><span data-stu-id="a516b-126">\<returns></span></span>](../../../csharp/programming-guide/xmldoc/returns.md)|[<span data-ttu-id="a516b-127">\<value></span><span class="sxs-lookup"><span data-stu-id="a516b-127">\<value></span></span>](../../../csharp/programming-guide/xmldoc/value.md)|  
  
 <span data-ttu-id="a516b-128">(\* oznacza, że kompilator sprawdza składnię.)</span><span class="sxs-lookup"><span data-stu-id="a516b-128">(\* denotes that the compiler verifies syntax.)</span></span>  
  
 <span data-ttu-id="a516b-129">Nawiasy są wyświetlane w tekście komentarza do dokumentacji, użyć `<` i `>`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a516b-129">If you want angle brackets to appear in the text of a documentation comment, use `<` and `>`, as shown in the following example.</span></span>  
  
```csharp  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a516b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a516b-130">See also</span></span>

- [<span data-ttu-id="a516b-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a516b-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a516b-132">/ doc (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="a516b-132">/doc (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="a516b-133">Komentarze dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="a516b-133">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
