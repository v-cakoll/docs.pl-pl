---
title: Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 83cb7d0a325e11c9669f1331e57bed7bf09f27c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333694"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="0497b-102">Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0497b-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="0497b-103">W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, używanego przez inne przykłady w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="0497b-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="0497b-104">Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne dane wyjściowe w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0497b-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="0497b-105">Jednak na potrzeby przykładów w tym samouczku będą działać z dowolny prawidłowy dokument WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="0497b-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="0497b-106">Aby utworzyć dokument, który korzysta z tego samouczka, musi mieć pakietu Microsoft Office 2007 lub nowszy zainstalowany lub konieczne jest posiadanie programu Microsoft Office 2003 za pomocą pakietu Microsoft Office zgodności dla programu Word, Excel i PowerPoint 2007 formatów.</span><span class="sxs-lookup"><span data-stu-id="0497b-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="0497b-107">Tworzenie dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="0497b-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="0497b-108">Aby utworzyć dokument WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="0497b-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="0497b-109">Utwórz nowy dokument programu Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="0497b-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="0497b-110">Wklej następujący tekst do nowego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="0497b-110">Paste the following text into the new document:</span></span>  
  
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
  
3. <span data-ttu-id="0497b-111">Formatuj pierwszy wiersz ze stylem "Nagłówek 1".</span><span class="sxs-lookup"><span data-stu-id="0497b-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="0497b-112">Wybierz wiersze, które zawierają kod języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0497b-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="0497b-113">Pierwszy wiersz zaczyna się od `Imports` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0497b-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="0497b-114">Ostatni wiersz jest "End Class".</span><span class="sxs-lookup"><span data-stu-id="0497b-114">The last line is "End Class".</span></span> <span data-ttu-id="0497b-115">Formatuj wierszy przy użyciu czcionki courier.</span><span class="sxs-lookup"><span data-stu-id="0497b-115">Format the lines with the courier font.</span></span> <span data-ttu-id="0497b-116">Formatuj je przy użyciu nowego stylu i nazwę nowego stylu "Code".</span><span class="sxs-lookup"><span data-stu-id="0497b-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="0497b-117">Na koniec zaznacz całą linię, która zawiera dane wyjściowe i sformatować je za pomocą `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="0497b-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="0497b-118">Zapisz dokument, a następnie nadaj mu nazwę SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="0497b-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0497b-119">Jeśli używasz programu Microsoft Word 2003, wybierz opcję **dokument programu Word 2007** w **Zapisz jako typ** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="0497b-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0497b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0497b-120">See also</span></span>

- [<span data-ttu-id="0497b-121">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0497b-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
