---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: d362f181921a39d274eaee78e85976522ce4fc15
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863192"
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="4f2f8-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f2f8-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="4f2f8-103">Definiuje typ parametru nazwę i opis.</span><span class="sxs-lookup"><span data-stu-id="4f2f8-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f2f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f2f8-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4f2f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f2f8-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4f2f8-106">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="4f2f8-106">The name of the type parameter.</span></span> <span data-ttu-id="4f2f8-107">Nazwę należy ująć w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="4f2f8-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="4f2f8-108">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="4f2f8-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f2f8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f2f8-109">Remarks</span></span>  
 <span data-ttu-id="4f2f8-110">Użyj `<typeparam>` tagu w komentarz dla typu ogólnego lub deklaracji ogólnej składowej, opisujący jeden z parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="4f2f8-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="4f2f8-111">Kompiluj przy użyciu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) do Przetwarzaj komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4f2f8-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f2f8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="4f2f8-112">Example</span></span>  
 <span data-ttu-id="4f2f8-113">W tym przykładzie użyto `<typeparam>` tag do opisania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="4f2f8-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4f2f8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f2f8-114">See Also</span></span>  
 [<span data-ttu-id="4f2f8-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4f2f8-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
