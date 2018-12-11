---
title: '&lt;paramref&gt; - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 90c22b81f17adb1fcfdb94f32047e85c0bd8f4e5
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243632"
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="cec74-102">&lt;paramref&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="cec74-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="cec74-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="cec74-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cec74-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="cec74-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="cec74-105">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="cec74-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="cec74-106">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="cec74-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cec74-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cec74-107">Remarks</span></span>  
 <span data-ttu-id="cec74-108">\<Paramref > tag zapewnia sposób, aby wskazać, że wyraz w kodzie komentarze, na przykład w \<podsumowania > lub \<Uwagi > Blokuj odwołuje się do parametru.</span><span class="sxs-lookup"><span data-stu-id="cec74-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="cec74-109">Plik XML mogą być przetwarzane do formatowania tego słowa w jakiś sposób distinct, takie jak przy użyciu czcionki pogrubieniem lub kursywą.</span><span class="sxs-lookup"><span data-stu-id="cec74-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="cec74-110">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="cec74-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec74-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="cec74-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cec74-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cec74-112">See Also</span></span>

- [<span data-ttu-id="cec74-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cec74-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cec74-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="cec74-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
