---
title: Tworzenie dokumentu źródłowego Office Open XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 3db168b2c2971c3b44e54aefc24a9e08edb232d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640446"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="3d06e-102">Tworzenie dokumentu źródłowego Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d06e-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="3d06e-103">W tym temacie przedstawiono sposób tworzenia dokumentu schemat WordprocessingML Office Open XML używanego przez inne przykłady w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="3d06e-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="3d06e-104">Jeśli wykonaj te instrukcje, danych wyjściowych będzie zgodny w każdym przykładzie danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3d06e-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="3d06e-105">Jednak przykłady w tym samouczku będzie działać z dowolnego prawidłowego dokumentu schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="3d06e-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="3d06e-106">Aby utworzyć dokument, który korzysta z tego samouczka, muszą mieć Microsoft Office 2007 lub nowszej lub Microsoft Office 2003 z pakietu Microsoft Office zgodności musi mieć dla programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="3d06e-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="3d06e-107">Tworzenie dokumentu schemat WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="3d06e-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="3d06e-108">Aby utworzyć schemat WordprocessingML dokumentu</span><span class="sxs-lookup"><span data-stu-id="3d06e-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="3d06e-109">Utwórz nowy dokument programu Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="3d06e-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="3d06e-110">Wklej poniższy tekst do nowego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="3d06e-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="3d06e-111">Pierwszy wiersz należy sformatować przy użyciu stylu "Nagłówek 1".</span><span class="sxs-lookup"><span data-stu-id="3d06e-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="3d06e-112">Wybierz wiersze, które zawierają kod Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3d06e-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="3d06e-113">Pierwszy wiersz rozpoczyna się od `Imports` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3d06e-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="3d06e-114">Ostatni wiersz jest "End Class".</span><span class="sxs-lookup"><span data-stu-id="3d06e-114">The last line is "End Class".</span></span> <span data-ttu-id="3d06e-115">Formatuj linie czcionką courier.</span><span class="sxs-lookup"><span data-stu-id="3d06e-115">Format the lines with the courier font.</span></span> <span data-ttu-id="3d06e-116">Sformatowane nowy styl i nazwę nowego stylu 'Code'.</span><span class="sxs-lookup"><span data-stu-id="3d06e-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="3d06e-117">Na koniec wybierz cały wiersz, który zawiera dane wyjściowe i sformatować go przy użyciu `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="3d06e-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="3d06e-118">Zapisz dokument i nadaj mu nazwę SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="3d06e-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3d06e-119">Jeśli korzystasz z programu Microsoft Word 2003, wybierz **dokument programu Word 2007** w **Zapisz jako typ** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="3d06e-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d06e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d06e-120">See Also</span></span>  
 [<span data-ttu-id="3d06e-121">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d06e-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
