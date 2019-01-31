---
title: <typeparam> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 08f9cf42f32c48e5dca09fc1141c55f6ba8af109
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266276"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="d940b-102">\<typeparam > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="d940b-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d940b-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="d940b-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d940b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d940b-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d940b-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d940b-105">The name of the type parameter.</span></span> <span data-ttu-id="d940b-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="d940b-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d940b-107">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="d940b-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d940b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d940b-108">Remarks</span></span>  
 <span data-ttu-id="d940b-109">`<typeparam>` Używany tag w komentarzu do deklaracji ogólnej typie lub metodzie do opisania parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="d940b-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="d940b-110">Dodaj tag dla każdego typu parametru typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="d940b-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="d940b-111">Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d940b-111">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="d940b-112">Tekst dla `<typeparam>` będą wyświetlane w technologii IntelliSense, [okna przeglądarki obiektów](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) kodu komentarza raport sieci web.</span><span class="sxs-lookup"><span data-stu-id="d940b-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="d940b-113">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="d940b-113">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d940b-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="d940b-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparam_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d940b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d940b-115">See also</span></span>

- [<span data-ttu-id="d940b-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d940b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="d940b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d940b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d940b-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="d940b-118">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
