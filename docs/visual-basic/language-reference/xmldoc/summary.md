---
title: '&lt;Podsumowanie&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a3008d1393c44aa0ec2398a2bd6afa079013e7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="ced52-102">&lt;Podsumowanie&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ced52-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="ced52-103">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ced52-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ced52-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ced52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ced52-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="ced52-106">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="ced52-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ced52-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ced52-107">Remarks</span></span>  
 <span data-ttu-id="ced52-108">Użyj `<summary>` tag do opisu typu lub członka typu.</span><span class="sxs-lookup"><span data-stu-id="ced52-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="ced52-109">Użyj [ \<Uwagi >](../../../visual-basic/language-reference/xmldoc/remarks.md) można dodać dodatkowe informacje do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="ced52-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="ced52-110">Tekst dla `<summary>` tag jest jedynym źródłem informacji o typie w IntelliSense i jest wyświetlany w przeglądarce obiektów.</span><span class="sxs-lookup"><span data-stu-id="ced52-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="ced52-111">Informacje o przeglądarce obiektów, zobacz [wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="ced52-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="ced52-112">Kompiluj z użyciem [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) na przetwarzanie komentarzy dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="ced52-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ced52-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ced52-113">Example</span></span>  
 <span data-ttu-id="ced52-114">W tym przykładzie użyto `<summary>` tag do opisywania `ResetCounter` — metoda i `Counter` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ced52-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ced52-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ced52-115">See Also</span></span>  
 [<span data-ttu-id="ced52-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="ced52-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
