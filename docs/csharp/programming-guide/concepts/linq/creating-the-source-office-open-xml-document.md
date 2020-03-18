---
title: Tworzenie dokumentu XML pakietu Source Office Open (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: d6c4d8866bba58e86735099a62041894a9faa9b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204152"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="12a92-102">Tworzenie dokumentu XML pakietu Source Office Open (C#)</span><span class="sxs-lookup"><span data-stu-id="12a92-102">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="12a92-103">W tym temacie pokazano, jak utworzyć dokument WordprocessingML języka XML pakietu Office, którego używają inne przykłady w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="12a92-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="12a92-104">Jeśli postępujesz zgodnie z tymi instrukcjami, dane wyjściowe będą zgodne z danymi wyjściowymi podanymi w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="12a92-104">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="12a92-105">Jednak przykłady w tym samouczku będzie działać z dowolnego prawidłowego dokumentu WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="12a92-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="12a92-106">Aby utworzyć dokument, którego używa ten samouczek, musisz mieć zainstalowany pakiet Microsoft Office 2007 lub nowszy lub mieć pakiet Microsoft Office 2003 z pakietem zgodności pakietu Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="12a92-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="12a92-107">Tworzenie dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="12a92-107">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="12a92-108">Aby utworzyć dokument WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="12a92-108">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="12a92-109">Utwórz nowy dokument programu Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="12a92-109">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="12a92-110">Wklej następujący tekst do nowego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="12a92-110">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="12a92-111">Sformatuj pierwszy wiersz za pomocą stylu "Nagłówek 1".</span><span class="sxs-lookup"><span data-stu-id="12a92-111">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="12a92-112">Wybierz wiersze zawierające kod C#.</span><span class="sxs-lookup"><span data-stu-id="12a92-112">Select the lines that contain the C# code.</span></span> <span data-ttu-id="12a92-113">Pierwszy wiersz zaczyna `using` się od słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="12a92-113">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="12a92-114">Ostatni wiersz jest ostatnim nawiasem zamykającym.</span><span class="sxs-lookup"><span data-stu-id="12a92-114">The last line is the last closing brace.</span></span> <span data-ttu-id="12a92-115">Sformatuj wiersze za pomocą czcionki kuriera.</span><span class="sxs-lookup"><span data-stu-id="12a92-115">Format the lines with the courier font.</span></span> <span data-ttu-id="12a92-116">Sformatuj je nowym stylem i nazwij nowy styl "Kod".</span><span class="sxs-lookup"><span data-stu-id="12a92-116">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="12a92-117">Na koniec zaznacz cały wiersz zawierający dane wyjściowe `Code` i sformatuj go za pomocą stylu.</span><span class="sxs-lookup"><span data-stu-id="12a92-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="12a92-118">Zapisz dokument i najmimij jego nazwę SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="12a92-118">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="12a92-119">Jeśli używasz programu Microsoft Word 2003, wybierz **pozycję Dokument programu Word 2007** z listy rozwijanej Zapisz jako **typ.**</span><span class="sxs-lookup"><span data-stu-id="12a92-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
