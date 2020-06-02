---
title: <param> — Przewodnik programowania w języku C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287327"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="0a2de-102">\<param>(Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0a2de-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="0a2de-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a2de-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="0a2de-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a2de-104">Parameters</span></span>

- `name`

  <span data-ttu-id="0a2de-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="0a2de-105">The name of a method parameter.</span></span> <span data-ttu-id="0a2de-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="0a2de-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="0a2de-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="0a2de-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="0a2de-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a2de-108">Remarks</span></span>

<span data-ttu-id="0a2de-109">`<param>`Tag powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="0a2de-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="0a2de-110">Aby udokumentować wiele parametrów, Użyj wielu `<param>` tagów.</span><span class="sxs-lookup"><span data-stu-id="0a2de-110">To document multiple parameters, use multiple `<param>` tags.</span></span>

<span data-ttu-id="0a2de-111">Tekst `<param>` znacznika jest wyświetlany w obszarze IntelliSense, Przeglądarka obiektów i raport sieci Web komentarza do kodu.</span><span class="sxs-lookup"><span data-stu-id="0a2de-111">The text for the `<param>` tag is displayed in IntelliSense, the Object Browser, and the Code Comment Web Report.</span></span>

<span data-ttu-id="0a2de-112">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="0a2de-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="0a2de-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a2de-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="0a2de-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a2de-114">See also</span></span>

- [<span data-ttu-id="0a2de-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0a2de-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="0a2de-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="0a2de-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
