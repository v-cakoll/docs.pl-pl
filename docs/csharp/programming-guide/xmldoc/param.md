---
title: <param> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: e2e9bd4478ceaf2f491aba0aa3db8bae7857f28d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587925"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="4d8c1-102">\<param > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="4d8c1-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4d8c1-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d8c1-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d8c1-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d8c1-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4d8c1-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="4d8c1-105">The name of a method parameter.</span></span> <span data-ttu-id="4d8c1-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="4d8c1-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4d8c1-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="4d8c1-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d8c1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d8c1-108">Remarks</span></span>  
 <span data-ttu-id="4d8c1-109">Tag \<> param powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="4d8c1-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="4d8c1-110">Aby udokumentować wiele parametrów, użyj \<wielu tagów > PARAM.</span><span class="sxs-lookup"><span data-stu-id="4d8c1-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="4d8c1-111">Tekst dla \<tagu > param będzie wyświetlany w technologii IntelliSense, Przeglądarka obiektów i w raporcie w sieci Web komentarza do kodu.</span><span class="sxs-lookup"><span data-stu-id="4d8c1-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="4d8c1-112">Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4d8c1-112">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d8c1-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4d8c1-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4d8c1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d8c1-114">See also</span></span>

- [<span data-ttu-id="4d8c1-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4d8c1-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4d8c1-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="4d8c1-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
