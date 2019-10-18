---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c62eab6b1fb1ba1cc7de83c12d7205cf0bbe46fa
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524721"
---
# <a name="param-visual-basic"></a><span data-ttu-id="b9f23-102">> \<param (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9f23-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="b9f23-103">Definiuje nazwę i opis parametru.</span><span class="sxs-lookup"><span data-stu-id="b9f23-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b9f23-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9f23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9f23-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="b9f23-106">Nazwa parametru metody.</span><span class="sxs-lookup"><span data-stu-id="b9f23-106">The name of a method parameter.</span></span> <span data-ttu-id="b9f23-107">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="b9f23-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="b9f23-108">Opis parametru.</span><span class="sxs-lookup"><span data-stu-id="b9f23-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9f23-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9f23-109">Remarks</span></span>  
 <span data-ttu-id="b9f23-110">Tag `<param>` powinien być używany w komentarzu dla deklaracji metody, aby opisać jeden z parametrów dla metody.</span><span class="sxs-lookup"><span data-stu-id="b9f23-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="b9f23-111">Tekst dla tagu `<param>` pojawi się w następujących lokalizacjach:</span><span class="sxs-lookup"><span data-stu-id="b9f23-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="b9f23-112">Informacje o parametrach funkcji IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b9f23-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="b9f23-113">Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="b9f23-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="b9f23-114">Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="b9f23-114">Object Browser.</span></span> <span data-ttu-id="b9f23-115">Aby uzyskać więcej informacji, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="b9f23-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="b9f23-116">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="b9f23-116">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9f23-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9f23-117">Example</span></span>  
 <span data-ttu-id="b9f23-118">W tym przykładzie za pomocą tagu `<param>` można opisać parametr `id`.</span><span class="sxs-lookup"><span data-stu-id="b9f23-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b9f23-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9f23-119">See also</span></span>

- [<span data-ttu-id="b9f23-120">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="b9f23-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
