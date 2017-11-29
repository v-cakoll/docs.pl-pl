---
title: "&lt;paramref&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fff532c02538f121ebe399e1780d8c19d9d6633a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="62831-102">&lt;paramref&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="62831-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="62831-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="62831-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62831-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="62831-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="62831-105">Nazwa parametru do odwoływania się do.</span><span class="sxs-lookup"><span data-stu-id="62831-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="62831-106">Nazwę należy ująć w podwójny cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="62831-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62831-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62831-107">Remarks</span></span>  
 <span data-ttu-id="62831-108">\<Paramref > tag zapewnia sposób, aby wskazać, że wyraz w kodzie komentarze, na przykład w \<podsumowania > lub \<Uwagi > bloku odwołuje się do parametru.</span><span class="sxs-lookup"><span data-stu-id="62831-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="62831-109">Aby sformatować ten wyraz w jakiś sposób distinct, na przykład z pogrubieniem lub kursywą czcionki mogą być przetwarzane w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="62831-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="62831-110">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="62831-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62831-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="62831-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="62831-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62831-112">See Also</span></span>  
 [<span data-ttu-id="62831-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="62831-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="62831-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="62831-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
