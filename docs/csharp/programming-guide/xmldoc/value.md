---
title: '&lt;wartość&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 24ef4aba13668cd04e20f17ebffac9eb68e796ca
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779289"
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="33fec-102">&lt;wartość&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="33fec-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="33fec-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="33fec-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33fec-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="33fec-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="33fec-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="33fec-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33fec-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33fec-106">Remarks</span></span>  
 <span data-ttu-id="33fec-107">\<Wartość > znacznik umożliwia opisują wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="33fec-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="33fec-108">Należy pamiętać, że po dodaniu właściwości za pomocą Kreatora kodów w środowisku programowania Visual Studio .NET, spowoduje to dodanie [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) tag w przypadku nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="33fec-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="33fec-109">Następnie należy ręcznie dodać \<wartość > tag do opisania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="33fec-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="33fec-110">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="33fec-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33fec-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="33fec-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="33fec-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33fec-112">See Also</span></span>

- [<span data-ttu-id="33fec-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="33fec-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="33fec-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="33fec-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
