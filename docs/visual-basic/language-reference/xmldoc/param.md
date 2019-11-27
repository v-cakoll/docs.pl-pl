---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4405fdf2defbb27aa2146d20083fd406d1f07236
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352298"
---
# <a name="param-visual-basic"></a><span data-ttu-id="11b3c-101">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11b3c-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="11b3c-102">Definiuje nazwę i opis parametru.</span><span class="sxs-lookup"><span data-stu-id="11b3c-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11b3c-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="11b3c-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="11b3c-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="11b3c-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="11b3c-105">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="11b3c-105">The name of a method parameter.</span></span> <span data-ttu-id="11b3c-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="11b3c-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="11b3c-107">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="11b3c-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11b3c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11b3c-108">Remarks</span></span>  
 <span data-ttu-id="11b3c-109">Tag `<param>` powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="11b3c-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="11b3c-110">Tekst dla tagu `<param>` pojawi się w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="11b3c-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="11b3c-111">Informacje o parametrach funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="11b3c-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="11b3c-112">Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="11b3c-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="11b3c-113">Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="11b3c-113">Object Browser.</span></span> <span data-ttu-id="11b3c-114">Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="11b3c-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="11b3c-115">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="11b3c-115">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11b3c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="11b3c-116">Example</span></span>  
 <span data-ttu-id="11b3c-117">W tym przykładzie za pomocą tagu `<param>` można opisać parametr `id`.</span><span class="sxs-lookup"><span data-stu-id="11b3c-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="11b3c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11b3c-118">See also</span></span>

- [<span data-ttu-id="11b3c-119">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="11b3c-119">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
