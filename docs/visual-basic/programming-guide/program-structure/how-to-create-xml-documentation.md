---
title: 'Porady: tworzenie dokumentacji XML w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 63b6485de5aba2ca49d54a057045bec2062d12dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="195b5-102">Porady: tworzenie dokumentacji XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="195b5-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="195b5-103">W tym przykładzie przedstawiono sposób dodawania komentarzy dokumentacji XML w kodzie.</span><span class="sxs-lookup"><span data-stu-id="195b5-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="195b5-104">Aby utworzyć plik dokumentacji XML dla typu lub elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="195b5-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="195b5-105">W **edytora kodu**, umieść kursor w wierszu powyżej typu lub elementu członkowskiego, dla którego chcesz utworzyć dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="195b5-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="195b5-106">Typ `'''` (trzy znaków pojedynczego cudzysłowu).</span><span class="sxs-lookup"><span data-stu-id="195b5-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="195b5-107">Szkielet XML dla typu lub elementu członkowskiego został dodany w **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="195b5-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="195b5-108">Dodaj informacje opisowe między odpowiednich tagów.</span><span class="sxs-lookup"><span data-stu-id="195b5-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="195b5-109">Jeśli dodasz dodatkowe wiersze w bloku dokumentacji XML, każdy wiersz musi rozpoczynać się od `'''`.</span><span class="sxs-lookup"><span data-stu-id="195b5-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="195b5-110">Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego o nowe komentarze dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="195b5-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="195b5-111">Funkcja IntelliSense wyświetla tekst z \<podsumowania > tag dla typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="195b5-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="195b5-112">Należy skompilować kod aby wygenerować plik XML zawierający komentarze dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="195b5-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="195b5-113">Aby uzyskać więcej informacji, zobacz [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="195b5-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195b5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="195b5-114">See Also</span></span>  
 [<span data-ttu-id="195b5-115">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="195b5-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="195b5-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="195b5-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="195b5-117">/ doc</span><span class="sxs-lookup"><span data-stu-id="195b5-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
