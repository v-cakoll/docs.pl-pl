---
title: "&lt;typeparam&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e1b8800e39b1ee5eeac8c5d3e4390ed3226b33a3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="lttypeparamgt-c-programming-guide"></a><span data-ttu-id="d1d48-102">&lt;typeparam&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="d1d48-102">&lt;typeparam&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d1d48-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1d48-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1d48-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1d48-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d1d48-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d1d48-105">The name of the type parameter.</span></span> <span data-ttu-id="d1d48-106">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="d1d48-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d1d48-107">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d1d48-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1d48-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1d48-108">Remarks</span></span>  
 <span data-ttu-id="d1d48-109">`<typeparam>` Tag powinny być używane w komentarz ogólny deklaracji typu lub metody do opisywania parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d1d48-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="d1d48-110">Dodaj tag dla każdego typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="d1d48-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="d1d48-111">Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1d48-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="d1d48-112">Tekst dla `<typeparam>` będą wyświetlane w IntelliSense, [okna przeglądarki obiektów](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) kodu — raport w sieci web komentarza.</span><span class="sxs-lookup"><span data-stu-id="d1d48-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](http://msdn.microsoft.com/library/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda) code comment web report.</span></span>  
  
 <span data-ttu-id="d1d48-113">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="d1d48-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1d48-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1d48-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d1d48-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1d48-115">See Also</span></span>  
 [<span data-ttu-id="d1d48-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d1d48-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d1d48-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d1d48-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d1d48-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="d1d48-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
