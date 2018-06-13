---
title: '&lt;typeparamref&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 36e5a8998018839214da00287a2bf8dc2c5925a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356266"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="e56f0-102">&lt;typeparamref&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="e56f0-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e56f0-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e56f0-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e56f0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e56f0-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e56f0-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e56f0-105">The name of the type parameter.</span></span> <span data-ttu-id="e56f0-106">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="e56f0-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e56f0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e56f0-107">Remarks</span></span>  
 <span data-ttu-id="e56f0-108">Aby uzyskać więcej informacji dotyczące parametrów typu w typach ogólnych i metody, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="e56f0-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="e56f0-109">Umożliwia użytkownikom pliku dokumentacji format programu word w jakiś sposób distinct, na przykład kursywą tego tagu.</span><span class="sxs-lookup"><span data-stu-id="e56f0-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="e56f0-110">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e56f0-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56f0-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e56f0-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e56f0-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e56f0-112">See Also</span></span>  
 [<span data-ttu-id="e56f0-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e56f0-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e56f0-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e56f0-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
