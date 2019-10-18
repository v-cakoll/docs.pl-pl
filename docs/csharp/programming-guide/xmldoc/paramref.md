---
title: <paramref> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 43e98565ff7294ebb6fa7e71d1be17522dbb15de
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523400"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="c69bd-102">\<paramref > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="c69bd-102">\<paramref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c69bd-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="c69bd-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="c69bd-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="c69bd-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="c69bd-105">Nazwa parametru, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="c69bd-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="c69bd-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="c69bd-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c69bd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c69bd-107">Remarks</span></span>  
 <span data-ttu-id="c69bd-108">Tag \<paramref > umożliwia wskazanie, że słowo w komentarzach do kodu, na przykład w \<summary > lub \<remarks > bloku odwołuje się do parametru.</span><span class="sxs-lookup"><span data-stu-id="c69bd-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="c69bd-109">Plik XML można przetworzyć, aby sformatować ten wyraz w sposób niezależny, na przykład za pomocą czcionki pogrubionej lub kursywy.</span><span class="sxs-lookup"><span data-stu-id="c69bd-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="c69bd-110">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="c69bd-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c69bd-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c69bd-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="c69bd-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c69bd-112">See also</span></span>

- [<span data-ttu-id="c69bd-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c69bd-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c69bd-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="c69bd-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
