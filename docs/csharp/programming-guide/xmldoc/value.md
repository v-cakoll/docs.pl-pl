---
title: "&lt;wartość&gt; (C# przewodnik programowania w języku)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="e041a-102">&lt;wartość&gt; (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="e041a-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e041a-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="e041a-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e041a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e041a-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="e041a-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="e041a-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e041a-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e041a-106">Remarks</span></span>  
 <span data-ttu-id="e041a-107">\<Wartość > znacznik umożliwia opisano wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="e041a-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="e041a-108">Należy pamiętać, że podczas dodawania właściwości za pośrednictwem Kreatora kodu w środowisku projektowym Visual Studio .NET, spowoduje to dodanie [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) tag nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e041a-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="e041a-109">Następnie należy ręcznie dodać \<wartość > tag do opisywania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="e041a-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="e041a-110">Kompiluj z użyciem [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="e041a-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e041a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e041a-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e041a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e041a-112">See Also</span></span>  
 [<span data-ttu-id="e041a-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e041a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e041a-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="e041a-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
