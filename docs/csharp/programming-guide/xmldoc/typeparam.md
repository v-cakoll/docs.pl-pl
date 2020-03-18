---
title: <typeparam> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793366"
---
# <a name="typeparam-c-programming-guide"></a><span data-ttu-id="1717c-102">\<typeparam> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="1717c-102">\<typeparam> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1717c-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="1717c-103">Syntax</span></span>

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a><span data-ttu-id="1717c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="1717c-104">Parameters</span></span>

- `name`

  <span data-ttu-id="1717c-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1717c-105">The name of the type parameter.</span></span> <span data-ttu-id="1717c-106">Nazwę ująć w podwójne cudzysłowy (" ").</span><span class="sxs-lookup"><span data-stu-id="1717c-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="1717c-107">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1717c-107">A description for the type parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="1717c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1717c-108">Remarks</span></span>

<span data-ttu-id="1717c-109">Tag `<typeparam>` powinien być używany w komentarzu dla typu ogólnego lub deklaracji metody do opisania parametru typu.</span><span class="sxs-lookup"><span data-stu-id="1717c-109">The `<typeparam>` tag should be used in the comment for a generic type or method declaration to describe a type parameter.</span></span> <span data-ttu-id="1717c-110">Dodaj znacznik dla każdego parametru typu typu ogólnego lub metody.</span><span class="sxs-lookup"><span data-stu-id="1717c-110">Add a tag for each type parameter of the generic type or method.</span></span>

<span data-ttu-id="1717c-111">Aby uzyskać więcej informacji, zobacz [Generyk .](../generics/index.md)</span><span class="sxs-lookup"><span data-stu-id="1717c-111">For more information, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="1717c-112">Tekst znacznika `<typeparam>` będzie wyświetlany w raporcie internetowym IntelliSense, w raporcie internetowym [kodu okna przeglądarki obiektów.](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser)</span><span class="sxs-lookup"><span data-stu-id="1717c-112">The text for the `<typeparam>` tag will be displayed in IntelliSense, the [Object Browser Window](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) code comment web report.</span></span>

<span data-ttu-id="1717c-113">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="1717c-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1717c-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1717c-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="1717c-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1717c-115">See also</span></span>

- [<span data-ttu-id="1717c-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1717c-116">C# reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="1717c-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1717c-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1717c-118">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="1717c-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
