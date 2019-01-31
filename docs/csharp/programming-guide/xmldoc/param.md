---
title: <param> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 3f1099da6a43ed7f48389a16e3be6a3b6b98a148
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271580"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="c618c-102">\<param > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="c618c-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c618c-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="c618c-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c618c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c618c-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c618c-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="c618c-105">The name of a method parameter.</span></span> <span data-ttu-id="c618c-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="c618c-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="c618c-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="c618c-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c618c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c618c-108">Remarks</span></span>  
 <span data-ttu-id="c618c-109">\<Param > używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="c618c-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="c618c-110">Dokumentowanie wiele parametrów, należy użyć wielu \<param > tagów.</span><span class="sxs-lookup"><span data-stu-id="c618c-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="c618c-111">Tekst dla \<param > będą wyświetlane w IntelliSense, przeglądarki obiektów i w raporcie Web komentarz kodu.</span><span class="sxs-lookup"><span data-stu-id="c618c-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="c618c-112">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="c618c-112">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c618c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c618c-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/param_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c618c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c618c-114">See also</span></span>

- [<span data-ttu-id="c618c-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c618c-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c618c-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="c618c-116">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
