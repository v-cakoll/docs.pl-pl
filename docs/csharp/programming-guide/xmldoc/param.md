---
title: <param> - Przewodnik programowania C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789756"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="b75f7-102">\<param> (przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="b75f7-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b75f7-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="b75f7-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="b75f7-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b75f7-104">Parameters</span></span>

- `name`

  <span data-ttu-id="b75f7-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="b75f7-105">The name of a method parameter.</span></span> <span data-ttu-id="b75f7-106">Nazwę ująć w podwójne cudzysłowy (" ").</span><span class="sxs-lookup"><span data-stu-id="b75f7-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="b75f7-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="b75f7-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="b75f7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b75f7-108">Remarks</span></span>

<span data-ttu-id="b75f7-109">Tag \<> param powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów metody.</span><span class="sxs-lookup"><span data-stu-id="b75f7-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="b75f7-110">Aby udokumentować wiele parametrów, należy użyć wielu \<tagów> paramów.</span><span class="sxs-lookup"><span data-stu-id="b75f7-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="b75f7-111">Tekst znacznika \<> param ów będzie wyświetlany w intelliSense, przeglądarce obiektów oraz w raporcie internetowym komentarzu kodu.</span><span class="sxs-lookup"><span data-stu-id="b75f7-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="b75f7-112">Skompiluj za pomocą [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) aby przetworzyć komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b75f7-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b75f7-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b75f7-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="b75f7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b75f7-114">See also</span></span>

- [<span data-ttu-id="b75f7-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b75f7-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="b75f7-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="b75f7-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
