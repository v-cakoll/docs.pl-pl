---
title: <typeparamref> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 451f101a3002a9590bdf616b01c6c8bab27efd69
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523312"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="f5461-102">\<typeparamref > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="f5461-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="f5461-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5461-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5461-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5461-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="f5461-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="f5461-105">The name of the type parameter.</span></span> <span data-ttu-id="f5461-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="f5461-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5461-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5461-107">Remarks</span></span>  
 <span data-ttu-id="f5461-108">Aby uzyskać więcej informacji na temat parametrów typu w typach ogólnych i metodach, zobacz [Generics](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5461-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="f5461-109">Ten tag umożliwia użytkownikom pliku dokumentacji formatowanie wyrazu w niektórych odrębnych przypadkach, na przykład kursywą.</span><span class="sxs-lookup"><span data-stu-id="f5461-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="f5461-110">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="f5461-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5461-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5461-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f5461-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5461-112">See also</span></span>

- [<span data-ttu-id="f5461-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f5461-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f5461-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="f5461-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
