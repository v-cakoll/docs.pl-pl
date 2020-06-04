---
title: 'Porady: tworzenie dokumentacji XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403242"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="85813-102">Porady: tworzenie dokumentacji XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85813-102">How to: Create XML Documentation in Visual Basic</span></span>

<span data-ttu-id="85813-103">Ten przykład pokazuje, jak dodać komentarze dokumentacji XML do kodu.</span><span class="sxs-lookup"><span data-stu-id="85813-103">This example shows how to add XML documentation comments to your code.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="85813-104">Aby utworzyć dokumentację XML dla typu lub elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="85813-104">To create XML documentation for a type or member</span></span>

1. <span data-ttu-id="85813-105">W **edytorze kodu**Umieść kursor w wierszu powyżej typu lub elementu członkowskiego, dla którego chcesz utworzyć dokumentację.</span><span class="sxs-lookup"><span data-stu-id="85813-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>

2. <span data-ttu-id="85813-106">Wpisz `'''` (trzy znaki pojedynczego cudzysłowu).</span><span class="sxs-lookup"><span data-stu-id="85813-106">Type `'''` (three single-quotation marks).</span></span>

    <span data-ttu-id="85813-107">Szkielet XML dla typu lub elementu członkowskiego jest dodawany w **edytorze kodu**.</span><span class="sxs-lookup"><span data-stu-id="85813-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>

3. <span data-ttu-id="85813-108">Dodaj opisowe informacje między odpowiednimi tagami.</span><span class="sxs-lookup"><span data-stu-id="85813-108">Add descriptive information between the appropriate tags.</span></span>

    > [!NOTE]
    > <span data-ttu-id="85813-109">Jeśli dodasz dodatkowe linie w bloku dokumentacji XML, każdy wiersz musi rozpoczynać się od `'''` .</span><span class="sxs-lookup"><span data-stu-id="85813-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>

4. <span data-ttu-id="85813-110">Dodaj dodatkowy kod, który używa typu lub elementu członkowskiego z nowymi komentarzami dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="85813-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>

    <span data-ttu-id="85813-111">IntelliSense wyświetla tekst ze \<summary> znacznika dla typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="85813-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>

5. <span data-ttu-id="85813-112">Skompiluj kod w celu wygenerowania pliku XML zawierającego Komentarze do dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="85813-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="85813-113">Aby uzyskać więcej informacji, zobacz [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="85813-113">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="85813-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85813-114">See also</span></span>

- [<span data-ttu-id="85813-115">Dokumentowanie kodu za pomocą XML</span><span class="sxs-lookup"><span data-stu-id="85813-115">Documenting Your Code with XML</span></span>](documenting-your-code-with-xml.md)
- [<span data-ttu-id="85813-116">Tagi komentarza XML</span><span class="sxs-lookup"><span data-stu-id="85813-116">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="85813-117">-doc</span><span class="sxs-lookup"><span data-stu-id="85813-117">-doc</span></span>](../../reference/command-line-compiler/doc.md)
