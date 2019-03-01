---
title: <typeparamref> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 0ee9e3571ab601f56ddee2fd9a02bb19f50bac62
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967363"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="8bb7c-102">\<typeparamref > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="8bb7c-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="8bb7c-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bb7c-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8bb7c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb7c-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8bb7c-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8bb7c-105">The name of the type parameter.</span></span> <span data-ttu-id="8bb7c-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="8bb7c-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bb7c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bb7c-107">Remarks</span></span>  
 <span data-ttu-id="8bb7c-108">Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metod, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="8bb7c-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="8bb7c-109">Użyj tego tagu, aby umożliwić klientom pliku dokumentacji sformatować wyraz w jakiś sposób distinct, na przykład kursywą.</span><span class="sxs-lookup"><span data-stu-id="8bb7c-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="8bb7c-110">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="8bb7c-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bb7c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb7c-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb7c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bb7c-112">See also</span></span>

- [<span data-ttu-id="8bb7c-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="8bb7c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8bb7c-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="8bb7c-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
