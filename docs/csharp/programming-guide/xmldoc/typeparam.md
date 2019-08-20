---
title: <typeparam> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: ea48cf0cdfc2dc48ad29ab6219449f801739bc8f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587593"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="739cb-102">\<typeparam > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="739cb-102">\<typeparam> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="739cb-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="739cb-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="739cb-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="739cb-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="739cb-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="739cb-105">The name of the type parameter.</span></span> <span data-ttu-id="739cb-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="739cb-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="739cb-107">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="739cb-107">A description for the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="739cb-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="739cb-108">Remarks</span></span>  
 <span data-ttu-id="739cb-109">`<typeparam>` Tag powinien być używany w komentarzu dla typu ogólnego lub deklaracji metody, aby opisać parametr typu.</span><span class="sxs-lookup"><span data-stu-id="739cb-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="739cb-110">Dodaj tag dla każdego parametru typu ogólnego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="739cb-110">Add a tag for each type parameter of the generic type or method.</span></span>  
  
 <span data-ttu-id="739cb-111">Aby uzyskać więcej informacji, zobacz [Ogólne](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="739cb-111">For more information, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="739cb-112">Tekst dla `<typeparam>` tagu będzie wyświetlany w IntelliSense, raport sieci Web przeglądarka obiektówgo komentarza do kodu [okna](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) .</span><span class="sxs-lookup"><span data-stu-id="739cb-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>  
  
 <span data-ttu-id="739cb-113">Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="739cb-113">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="739cb-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="739cb-114">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="739cb-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="739cb-115">See also</span></span>

- [<span data-ttu-id="739cb-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="739cb-116">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="739cb-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="739cb-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="739cb-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="739cb-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
