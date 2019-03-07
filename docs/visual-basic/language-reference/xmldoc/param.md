---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: f80d9f3024107ace2102fb9ec9e8657d3219aafa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502244"
---
# <a name="param-visual-basic"></a><span data-ttu-id="28f40-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28f40-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="28f40-103">Określa nazwę parametru i opis.</span><span class="sxs-lookup"><span data-stu-id="28f40-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28f40-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28f40-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="28f40-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28f40-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="28f40-106">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="28f40-106">The name of a method parameter.</span></span> <span data-ttu-id="28f40-107">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="28f40-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="28f40-108">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="28f40-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28f40-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28f40-109">Remarks</span></span>  
 <span data-ttu-id="28f40-110">`<param>` Używany tag w komentarzu do deklaracji metody do opisania jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="28f40-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="28f40-111">Tekst dla `<param>` tag pojawi się w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="28f40-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="28f40-112">Informacje o parametrach IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="28f40-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="28f40-113">Aby uzyskać więcej informacji, zobacz [za pomocą funkcji IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="28f40-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="28f40-114">Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="28f40-114">Object Browser.</span></span> <span data-ttu-id="28f40-115">Aby uzyskać więcej informacji, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="28f40-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="28f40-116">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="28f40-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f40-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="28f40-117">Example</span></span>  
 <span data-ttu-id="28f40-118">W tym przykładzie użyto `<param>` tag do opisania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="28f40-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="28f40-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28f40-119">See also</span></span>
- [<span data-ttu-id="28f40-120">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="28f40-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
