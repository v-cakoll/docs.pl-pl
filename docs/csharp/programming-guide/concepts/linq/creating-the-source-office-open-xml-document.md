---
title: Tworzenie źródłowego dokumentu Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: d6c4d8866bba58e86735099a62041894a9faa9b1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204152"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="7ed76-102">Tworzenie źródłowego dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7ed76-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="7ed76-103">W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, który jest używany przez inne przykłady w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="7ed76-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="7ed76-104">Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne z danymi wyjściowymi podanymi w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7ed76-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="7ed76-105">Jednak przykłady w tym samouczku będą działały z dowolnym prawidłowym dokumentem WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="7ed76-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="7ed76-106">Aby utworzyć dokument, który jest wykorzystywany przez ten samouczek, musisz mieć zainstalowany Microsoft Office 2007 lub nowszy lub mieć Microsoft Office 2003 z pakietem zgodności Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="7ed76-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="7ed76-107">Tworzenie dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="7ed76-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="7ed76-108">Aby utworzyć dokument WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="7ed76-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="7ed76-109">Utwórz nowy dokument programu Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="7ed76-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="7ed76-110">Wklej następujący tekst do nowego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="7ed76-110">Paste the following text into the new document:</span></span>

    ```text
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

3. <span data-ttu-id="7ed76-111">Sformatuj pierwszy wiersz za pomocą stylu "Nagłówek 1".</span><span class="sxs-lookup"><span data-stu-id="7ed76-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="7ed76-112">Wybierz wiersze, które zawierają C# kod.</span><span class="sxs-lookup"><span data-stu-id="7ed76-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="7ed76-113">Pierwszy wiersz rozpoczyna `using` się od słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7ed76-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="7ed76-114">Ostatnim wierszem jest ostatni zamykający nawias klamrowy.</span><span class="sxs-lookup"><span data-stu-id="7ed76-114">The last line is the last closing brace.</span></span> <span data-ttu-id="7ed76-115">Sformatuj linie przy użyciu czcionki Courier.</span><span class="sxs-lookup"><span data-stu-id="7ed76-115">Format the lines with the courier font.</span></span> <span data-ttu-id="7ed76-116">Sformatuj je przy użyciu nowego stylu i nazwij nowy styl "Code".</span><span class="sxs-lookup"><span data-stu-id="7ed76-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="7ed76-117">Na koniec zaznacz cały wiersz zawierający dane wyjściowe i sformatuj go przy użyciu `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="7ed76-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="7ed76-118">Zapisz dokument i nadaj mu nazwę SampleDoc. docx.</span><span class="sxs-lookup"><span data-stu-id="7ed76-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ed76-119">Jeśli używasz programu Microsoft Word 2003, wybierz pozycję **dokument programu Word 2007** na liście rozwijanej **Zapisz jako typ** .</span><span class="sxs-lookup"><span data-stu-id="7ed76-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
