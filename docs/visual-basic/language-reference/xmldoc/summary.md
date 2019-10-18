---
title: <summary> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 25a0b307756401bed4d4c77d3668c2af53ba8b42
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524631"
---
# <a name="summary-visual-basic"></a><span data-ttu-id="4349e-102">> \<summary (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4349e-102">\<summary> (Visual Basic)</span></span>
<span data-ttu-id="4349e-103">Określa podsumowanie elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4349e-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4349e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4349e-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a><span data-ttu-id="4349e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4349e-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="4349e-106">Podsumowanie obiektu.</span><span class="sxs-lookup"><span data-stu-id="4349e-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4349e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4349e-107">Remarks</span></span>  
 <span data-ttu-id="4349e-108">Użyj znacznika `<summary>`, aby opisać typ lub element członkowski typu.</span><span class="sxs-lookup"><span data-stu-id="4349e-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="4349e-109">Użyj [> \<remarks](../../../visual-basic/language-reference/xmldoc/remarks.md) , aby dodać informacje uzupełniające do opisu typu.</span><span class="sxs-lookup"><span data-stu-id="4349e-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="4349e-110">Tekst dla tagu `<summary>` jest jedynym źródłem informacji o typie w technologii IntelliSense i jest również wyświetlany w Przeglądarka obiektów.</span><span class="sxs-lookup"><span data-stu-id="4349e-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="4349e-111">Aby uzyskać informacje na temat Przeglądarka obiektów, zobacz [Wyświetlanie struktury kodu](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="4349e-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="4349e-112">Kompiluj z [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) , aby przetwarzać komentarze dokumentacji do pliku.</span><span class="sxs-lookup"><span data-stu-id="4349e-112">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4349e-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4349e-113">Example</span></span>  
 <span data-ttu-id="4349e-114">W tym przykładzie za pomocą tagu `<summary>` można opisać metodę `ResetCounter` i Właściwość `Counter`.</span><span class="sxs-lookup"><span data-stu-id="4349e-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4349e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4349e-115">See also</span></span>

- [<span data-ttu-id="4349e-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4349e-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
