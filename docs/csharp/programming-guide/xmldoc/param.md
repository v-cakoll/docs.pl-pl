---
title: <param> — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: f9613a7373a829d2a52f3f56b8ea1ab35ebdcf5f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711730"
---
# <a name="param-c-programming-guide"></a><span data-ttu-id="ed730-102">\<param > (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="ed730-102">\<param> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="ed730-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed730-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed730-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed730-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="ed730-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="ed730-105">The name of a method parameter.</span></span> <span data-ttu-id="ed730-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="ed730-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ed730-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="ed730-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed730-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed730-108">Remarks</span></span>  
 <span data-ttu-id="ed730-109">Tag \<param > należy użyć w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="ed730-109">The \<param> tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span> <span data-ttu-id="ed730-110">Aby udokumentować wiele parametrów, Użyj wielu tagów \<param >.</span><span class="sxs-lookup"><span data-stu-id="ed730-110">To document multiple parameters, use multiple \<param> tags.</span></span>  
  
 <span data-ttu-id="ed730-111">Tekst dla tagu \<param > zostanie wyświetlony w IntelliSense, Przeglądarka obiektów i w raporcie w sieci Web komentarza do kodu.</span><span class="sxs-lookup"><span data-stu-id="ed730-111">The text for the \<param> tag will be displayed in IntelliSense, the Object Browser, and in the Code Comment Web Report.</span></span>  
  
 <span data-ttu-id="ed730-112">Kompiluj z [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ed730-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed730-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed730-113">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ed730-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed730-114">See also</span></span>

- [<span data-ttu-id="ed730-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ed730-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ed730-116">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="ed730-116">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
