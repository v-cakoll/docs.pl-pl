---
title: 'Instrukcje: Tworzenie dokumentacji XML w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 95f6c5b23deadc16eb1e81f274e2cc5149598fb7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050440"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="b16e0-102">Instrukcje: Tworzenie dokumentacji XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b16e0-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="b16e0-103">W tym przykładzie przedstawiono sposób dodawania komentarzy dokumentacji XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b16e0-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="b16e0-104">Aby utworzyć dokumentacji XML dla typu lub składowej</span><span class="sxs-lookup"><span data-stu-id="b16e0-104">To create XML documentation for a type or member</span></span>  
  
1. <span data-ttu-id="b16e0-105">W **Edytor kodu**, umieść kursor w wierszu powyżej typu lub elementu członkowskiego, dla której chcesz utworzyć dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b16e0-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2. <span data-ttu-id="b16e0-106">Typ `'''` (trzy znaki pojedynczego cudzysłowu).</span><span class="sxs-lookup"><span data-stu-id="b16e0-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="b16e0-107">Szkielet XML dla typu lub elementu członkowskiego zostanie dodany do **Edytor kodu**.</span><span class="sxs-lookup"><span data-stu-id="b16e0-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3. <span data-ttu-id="b16e0-108">Dodaj informacje opisowe między odpowiednie tagi.</span><span class="sxs-lookup"><span data-stu-id="b16e0-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b16e0-109">Jeśli dodasz dodatkowe wiersze w bloku dokumentacji XML, musi zaczynać się każdy wiersz `'''`.</span><span class="sxs-lookup"><span data-stu-id="b16e0-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4. <span data-ttu-id="b16e0-110">Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego przy użyciu nowych komentarzy dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="b16e0-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="b16e0-111">Funkcja IntelliSense wyświetla tekst z \<podsumowania > tag w przypadku typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b16e0-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5. <span data-ttu-id="b16e0-112">Skompiluj kod, aby wygenerować plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b16e0-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="b16e0-113">Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="b16e0-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b16e0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b16e0-114">See also</span></span>

- [<span data-ttu-id="b16e0-115">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="b16e0-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="b16e0-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="b16e0-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="b16e0-117">/doc</span><span class="sxs-lookup"><span data-stu-id="b16e0-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
