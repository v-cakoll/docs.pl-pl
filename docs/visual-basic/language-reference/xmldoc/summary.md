---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411502"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="afe8f-101">\<summary> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afe8f-101">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="afe8f-102">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="afe8f-102">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe8f-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="afe8f-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="afe8f-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="afe8f-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="afe8f-105">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="afe8f-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afe8f-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afe8f-106">Remarks</span></span>  
 <span data-ttu-id="afe8f-107">Użyj `<summary>` znacznika, aby opisać typ lub element członkowski typu.</span><span class="sxs-lookup"><span data-stu-id="afe8f-107">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="afe8f-108">Służy [\<remarks>](remarks.md) do dodawania dodatkowych informacji do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="afe8f-108">Use [\<remarks>](remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="afe8f-109">Tekst `<summary>` znacznika jest jedynym źródłem informacji o typie w technologii IntelliSense i jest również wyświetlany w Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="afe8f-109">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="afe8f-110">Aby uzyskać informacje na temat Przeglądarka obiektów, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="afe8f-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="afe8f-111">Kompiluj z [-doc](../../reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="afe8f-111">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe8f-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="afe8f-112">Example</span></span>  
 <span data-ttu-id="afe8f-113">W tym przykładzie używa `<summary>` znacznika do opisania `ResetCounter` metody i `Counter` właściwości.</span><span class="sxs-lookup"><span data-stu-id="afe8f-113">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="afe8f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afe8f-114">See also</span></span>

- [<span data-ttu-id="afe8f-115">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="afe8f-115">XML Comment Tags</span></span>](index.md)
