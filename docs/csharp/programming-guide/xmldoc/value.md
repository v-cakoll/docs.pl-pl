---
title: <value> - C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 1a1a4beb4a3412fe7739a69ecd0fed650b332fb2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263946"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="88449-102">\<wartość > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="88449-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="88449-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="88449-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88449-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="88449-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="88449-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="88449-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88449-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88449-106">Remarks</span></span>  
 <span data-ttu-id="88449-107">\<Wartość > znacznik umożliwia opisują wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="88449-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="88449-108">Należy pamiętać, że po dodaniu właściwości za pomocą Kreatora kodów w środowisku programowania Visual Studio .NET, spowoduje to dodanie [ \<podsumowania >](../../../csharp/programming-guide/xmldoc/summary.md) tag w przypadku nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="88449-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="88449-109">Następnie należy ręcznie dodać \<wartość > tag do opisania wartość, która reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="88449-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="88449-110">Kompiluj przy użyciu [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="88449-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88449-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="88449-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="88449-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88449-112">See also</span></span>

- [<span data-ttu-id="88449-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88449-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="88449-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="88449-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
