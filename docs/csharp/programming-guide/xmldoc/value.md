---
title: '&lt;wartość&gt; (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 22de15560d6db6e8a70cea744dd9d85359336306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356434"
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="a1962-102">&lt;wartość&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="a1962-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="a1962-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1962-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1962-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1962-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="a1962-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1962-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1962-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1962-106">Remarks</span></span>  
 <span data-ttu-id="a1962-107">\<Wartość > znacznik umożliwia opisano wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="a1962-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="a1962-108">Należy pamiętać, że podczas dodawania właściwości za pośrednictwem Kreatora kodu w środowisku projektowym Visual Studio .NET, spowoduje to dodanie [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) tag nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1962-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="a1962-109">Następnie należy ręcznie dodać \<wartość > tag do opisywania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="a1962-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="a1962-110">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="a1962-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1962-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1962-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a1962-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1962-112">See Also</span></span>  
 [<span data-ttu-id="a1962-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a1962-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a1962-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="a1962-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
