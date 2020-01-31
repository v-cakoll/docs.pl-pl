---
title: <param> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789756"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="e65e7-102">\<param > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="e65e7-102">\<param> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="e65e7-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e65e7-103">Syntax</span></span>

```xml
<param name="name">description</param>
```

## <a name="parameters"></a><span data-ttu-id="e65e7-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e65e7-104">Parameters</span></span>

- `name`

  <span data-ttu-id="e65e7-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="e65e7-105">The name of a method parameter.</span></span> <span data-ttu-id="e65e7-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="e65e7-106">Enclose the name in double quotation marks (" ").</span></span>

- `description`

  <span data-ttu-id="e65e7-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="e65e7-107">A description for the parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="e65e7-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e65e7-108">Remarks</span></span>

<span data-ttu-id="e65e7-109">Tag \<param > należy użyć w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="e65e7-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="e65e7-110">Aby udokumentować wiele parametrów, Użyj wielu tagów \<param >.</span><span class="sxs-lookup"><span data-stu-id="e65e7-110">To document multiple parameters, use multiple \<param> tags.</span></span>

<span data-ttu-id="e65e7-111">Tekst dla tagu \<param > zostanie wyświetlony w IntelliSense, Przeglądarka obiektów i w raporcie w sieci Web komentarza do kodu.</span><span class="sxs-lookup"><span data-stu-id="e65e7-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>

<span data-ttu-id="e65e7-112">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e65e7-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="e65e7-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e65e7-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a><span data-ttu-id="e65e7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e65e7-114">See also</span></span>

- [<span data-ttu-id="e65e7-115">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="e65e7-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="e65e7-116">Zalecane Tagi dla komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e65e7-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
