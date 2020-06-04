---
title: <typeparam>
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 2ad54845645172acb5b91935f5347a828510e3aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411489"
---
# <a name="typeparam-visual-basic"></a><span data-ttu-id="8afac-101">\<typeparam> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8afac-101">\<typeparam> (Visual Basic)</span></span>
<span data-ttu-id="8afac-102">Definiuje nazwę i opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8afac-102">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afac-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="8afac-103">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
## <a name="parameters"></a><span data-ttu-id="8afac-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="8afac-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="8afac-105">Nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8afac-105">The name of the type parameter.</span></span> <span data-ttu-id="8afac-106">Ujmij nazwę w znaki podwójnego cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="8afac-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="8afac-107">Opis parametru typu.</span><span class="sxs-lookup"><span data-stu-id="8afac-107">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8afac-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8afac-108">Remarks</span></span>  
 <span data-ttu-id="8afac-109">Użyj `<typeparam>` znacznika w komentarzu dla typu ogólnego lub ogólnej deklaracji elementu członkowskiego, aby opisać jeden z parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="8afac-109">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="8afac-110">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="8afac-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8afac-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="8afac-111">Example</span></span>  
 <span data-ttu-id="8afac-112">W tym przykładzie używa `<typeparam>` znacznika do opisania `id` parametru.</span><span class="sxs-lookup"><span data-stu-id="8afac-112">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="8afac-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8afac-113">See also</span></span>

- [<span data-ttu-id="8afac-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="8afac-114">XML Comment Tags</span></span>](index.md)
