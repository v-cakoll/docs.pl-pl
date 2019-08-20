---
title: <value> — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 4d967d671b3a27698b457c80ff5a8f7031dc6bcb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587405"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="fa626-102">\<wartość > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="fa626-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="fa626-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa626-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa626-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="fa626-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="fa626-105">Opis właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa626-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa626-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa626-106">Remarks</span></span>  
 <span data-ttu-id="fa626-107">Tag \<Value > umożliwia opisanie wartości reprezentowanej przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="fa626-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="fa626-108">Należy pamiętać, że po dodaniu właściwości za pośrednictwem Kreatora kodu w środowisku deweloperskim Visual Studio .NET zostanie dodany [ \<tag > podsumowujący](./summary.md) dla nowej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa626-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="fa626-109">Następnie należy ręcznie dodać \<wartość > tag, aby opisać wartość, którą reprezentuje właściwość.</span><span class="sxs-lookup"><span data-stu-id="fa626-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="fa626-110">Kompiluj z [/doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="fa626-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa626-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa626-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="fa626-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa626-112">See also</span></span>

- [<span data-ttu-id="fa626-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fa626-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fa626-114">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="fa626-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
