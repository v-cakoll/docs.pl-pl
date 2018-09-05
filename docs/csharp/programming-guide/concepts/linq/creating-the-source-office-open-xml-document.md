---
title: Tworzenie źródłowego dokumentu Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: 7941864e5dc2401a27df151c8c7806218609fcd4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558236"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="2ae99-102">Tworzenie źródłowego dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="2ae99-102">Creating the Source Office Open XML Document (C#)</span></span>
<span data-ttu-id="2ae99-103">W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, używanego przez inne przykłady w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="2ae99-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="2ae99-104">Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne dane wyjściowe w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2ae99-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="2ae99-105">Jednak na potrzeby przykładów w tym samouczku będą działać z dowolny prawidłowy dokument WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="2ae99-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="2ae99-106">Aby utworzyć dokument, który korzysta z tego samouczka, musi mieć pakietu Microsoft Office 2007 lub nowszy zainstalowany lub konieczne jest posiadanie programu Microsoft Office 2003 za pomocą pakietu Microsoft Office zgodności dla programu Word, Excel i PowerPoint 2007 formatów.</span><span class="sxs-lookup"><span data-stu-id="2ae99-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="2ae99-107">Tworzenie dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="2ae99-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="2ae99-108">Aby utworzyć dokument WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="2ae99-108">To create the WordprocessingML document</span></span>  
  
1.  <span data-ttu-id="2ae99-109">Utwórz nowy dokument programu Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="2ae99-109">Create a new Microsoft Word document.</span></span>  
  
2.  <span data-ttu-id="2ae99-110">Wklej następujący tekst do nowego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="2ae99-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    using System;  
  
    class Program {  
        public static void Main(string[] args) {  
            Console.WriteLine("Hello World");  
        }  
    }  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3.  <span data-ttu-id="2ae99-111">Formatuj pierwszy wiersz ze stylem "Nagłówek 1".</span><span class="sxs-lookup"><span data-stu-id="2ae99-111">Format the first line with the style "Heading 1".</span></span>  
  
4.  <span data-ttu-id="2ae99-112">Wybierz wiersze, które zawierają kod C#.</span><span class="sxs-lookup"><span data-stu-id="2ae99-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="2ae99-113">Pierwszy wiersz zaczyna się od `using` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="2ae99-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="2ae99-114">Ostatni wiersz jest ostatni nawias zamykający.</span><span class="sxs-lookup"><span data-stu-id="2ae99-114">The last line is the last closing brace.</span></span> <span data-ttu-id="2ae99-115">Formatuj wierszy przy użyciu czcionki courier.</span><span class="sxs-lookup"><span data-stu-id="2ae99-115">Format the lines with the courier font.</span></span> <span data-ttu-id="2ae99-116">Formatuj je przy użyciu nowego stylu i nazwę nowego stylu "Code".</span><span class="sxs-lookup"><span data-stu-id="2ae99-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5.  <span data-ttu-id="2ae99-117">Na koniec zaznacz całą linię, która zawiera dane wyjściowe i sformatować je za pomocą `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="2ae99-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6.  <span data-ttu-id="2ae99-118">Zapisz dokument, a następnie nadaj mu nazwę SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="2ae99-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2ae99-119">Jeśli używasz programu Microsoft Word 2003, wybierz opcję **dokument programu Word 2007** w **Zapisz jako typ** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="2ae99-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ae99-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ae99-120">See Also</span></span>

- [<span data-ttu-id="2ae99-121">Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (C#)</span><span class="sxs-lookup"><span data-stu-id="2ae99-121">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
