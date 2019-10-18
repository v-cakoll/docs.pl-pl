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
ms.openlocfilehash: ed7a8f8a06771a18dc4244bffbda53e9adbd4e90
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523416"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="9784d-102">\<param > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="9784d-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9784d-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="9784d-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9784d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="9784d-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9784d-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="9784d-105">The name of a method parameter.</span></span> <span data-ttu-id="9784d-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="9784d-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="9784d-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="9784d-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9784d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9784d-108">Remarks</span></span>  
 <span data-ttu-id="9784d-109">Tag > \<param powinien zostać użyty w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="9784d-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="9784d-110">Aby udokumentować wiele parametrów, Użyj wielu tagów > \<param.</span><span class="sxs-lookup"><span data-stu-id="9784d-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="9784d-111">Tekst \<param tagu > zostanie wyświetlony w IntelliSense, Przeglądarka obiektów i w raporcie w sieci Web komentarza do kodu.</span><span class="sxs-lookup"><span data-stu-id="9784d-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="9784d-112">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="9784d-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9784d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="9784d-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9784d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9784d-114">See also</span></span>

- [<span data-ttu-id="9784d-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9784d-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9784d-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="9784d-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
