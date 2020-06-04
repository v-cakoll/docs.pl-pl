---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400024"
---
# <a name="remarks-visual-basic"></a><span data-ttu-id="0ee38-101">\<remarks> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ee38-101">\<remarks> (Visual Basic)</span></span>
<span data-ttu-id="0ee38-102">Określa sekcję Uwagi dla elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0ee38-102">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee38-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ee38-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ee38-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ee38-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0ee38-105">Opis elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0ee38-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ee38-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ee38-106">Remarks</span></span>  
 <span data-ttu-id="0ee38-107">Użyj `<remarks>` znacznika, aby dodać informacje o typie, uzupełniając informacje określone za pomocą [\<summary>](summary.md) .</span><span class="sxs-lookup"><span data-stu-id="0ee38-107">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](summary.md).</span></span>  
  
 <span data-ttu-id="0ee38-108">Te informacje są wyświetlane w Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="0ee38-108">This information appears in the Object Browser.</span></span> <span data-ttu-id="0ee38-109">Aby uzyskać informacje na temat Przeglądarka obiektów, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="0ee38-109">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="0ee38-110">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="0ee38-110">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ee38-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ee38-111">Example</span></span>  
 <span data-ttu-id="0ee38-112">W tym przykładzie używa `<remarks>` znacznika do wyjaśnienia `UpdateRecord` metody.</span><span class="sxs-lookup"><span data-stu-id="0ee38-112">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="0ee38-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ee38-113">See also</span></span>

- [<span data-ttu-id="0ee38-114">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="0ee38-114">XML Comment Tags</span></span>](index.md)
