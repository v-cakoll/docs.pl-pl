---
title: '&lt;typeparamref&gt; - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: cfee16ad1cdc1e019a4133259c1603f5a0a09ac8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536558"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="f9b1f-102">&lt;typeparamref&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="f9b1f-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f9b1f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9b1f-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9b1f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9b1f-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f9b1f-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f9b1f-105">The name of the type parameter.</span></span> <span data-ttu-id="f9b1f-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="f9b1f-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9b1f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9b1f-107">Remarks</span></span>  
 <span data-ttu-id="f9b1f-108">Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metod, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9b1f-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="f9b1f-109">Użyj tego tagu, aby umożliwić klientom pliku dokumentacji sformatować wyraz w jakiś sposób distinct, na przykład kursywą.</span><span class="sxs-lookup"><span data-stu-id="f9b1f-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="f9b1f-110">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="f9b1f-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b1f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9b1f-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f9b1f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9b1f-112">See also</span></span>

- [<span data-ttu-id="f9b1f-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f9b1f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f9b1f-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="f9b1f-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
