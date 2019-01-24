---
title: 'Instrukcje: Tworzenie dokumentacji XML w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: d67724aad6cd3e7af30531328d85e89937390dd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551374"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="4adde-102">Instrukcje: Tworzenie dokumentacji XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4adde-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="4adde-103">W tym przykładzie przedstawiono sposób dodawania komentarzy dokumentacji XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4adde-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="4adde-104">Aby utworzyć dokumentacji XML dla typu lub składowej</span><span class="sxs-lookup"><span data-stu-id="4adde-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="4adde-105">W **Edytor kodu**, umieść kursor w wierszu powyżej typu lub elementu członkowskiego, dla której chcesz utworzyć dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="4adde-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="4adde-106">Typ `'''` (trzy znaki pojedynczego cudzysłowu).</span><span class="sxs-lookup"><span data-stu-id="4adde-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="4adde-107">Szkielet XML dla typu lub elementu członkowskiego zostanie dodany do **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="4adde-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="4adde-108">Dodaj informacje opisowe między odpowiednie tagi.</span><span class="sxs-lookup"><span data-stu-id="4adde-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4adde-109">Jeśli dodasz dodatkowe wiersze w bloku dokumentacji XML, musi zaczynać się każdy wiersz `'''`.</span><span class="sxs-lookup"><span data-stu-id="4adde-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="4adde-110">Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego przy użyciu nowych komentarzy dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="4adde-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="4adde-111">Funkcja IntelliSense wyświetla tekst z \<podsumowania > tag w przypadku typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4adde-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="4adde-112">Skompiluj kod, aby wygenerować plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="4adde-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="4adde-113">Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="4adde-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adde-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4adde-114">See also</span></span>
- [<span data-ttu-id="4adde-115">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="4adde-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="4adde-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="4adde-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="4adde-117">/doc</span><span class="sxs-lookup"><span data-stu-id="4adde-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
