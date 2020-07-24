---
title: Tworzenie źródłowego dokumentu Office Open XML (C#)
description: Utwórz dokument pakietu Office Open XML WordprocessingML do użycia z samouczkami języka C#. Ten artykuł wymaga Microsoft Office.
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: e6d6908ee6560218793454f3871705e74095f543
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103997"
---
# <a name="creating-the-source-office-open-xml-document-c"></a><span data-ttu-id="35493-104">Tworzenie źródłowego dokumentu Office Open XML (C#)</span><span class="sxs-lookup"><span data-stu-id="35493-104">Creating the Source Office Open XML Document (C#)</span></span>

<span data-ttu-id="35493-105">W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, który jest używany przez inne przykłady w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="35493-105">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="35493-106">Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne z danymi wyjściowymi podanymi w każdym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="35493-106">If you follow these instructions, your output will match the output provided in each example.</span></span>

<span data-ttu-id="35493-107">Jednak przykłady w tym samouczku będą działały z dowolnym prawidłowym dokumentem WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="35493-107">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>

<span data-ttu-id="35493-108">Aby utworzyć dokument, który jest wykorzystywany przez ten samouczek, musisz mieć zainstalowany Microsoft Office 2007 lub nowszy lub mieć Microsoft Office 2003 z pakietem zgodności Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.</span><span class="sxs-lookup"><span data-stu-id="35493-108">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>

## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="35493-109">Tworzenie dokumentu WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="35493-109">Creating the WordprocessingML Document</span></span>

#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="35493-110">Aby utworzyć dokument WordprocessingML</span><span class="sxs-lookup"><span data-stu-id="35493-110">To create the WordprocessingML document</span></span>

1. <span data-ttu-id="35493-111">Utwórz nowy dokument programu Microsoft Word.</span><span class="sxs-lookup"><span data-stu-id="35493-111">Create a new Microsoft Word document.</span></span>

2. <span data-ttu-id="35493-112">Wklej następujący tekst do nowego dokumentu:</span><span class="sxs-lookup"><span data-stu-id="35493-112">Paste the following text into the new document:</span></span>

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

3. <span data-ttu-id="35493-113">Sformatuj pierwszy wiersz za pomocą stylu "Nagłówek 1".</span><span class="sxs-lookup"><span data-stu-id="35493-113">Format the first line with the style "Heading 1".</span></span>

4. <span data-ttu-id="35493-114">Wybierz wiersze zawierające kod w języku C#.</span><span class="sxs-lookup"><span data-stu-id="35493-114">Select the lines that contain the C# code.</span></span> <span data-ttu-id="35493-115">Pierwszy wiersz rozpoczyna się od `using` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="35493-115">The first line starts with the `using` keyword.</span></span> <span data-ttu-id="35493-116">Ostatnim wierszem jest ostatni zamykający nawias klamrowy.</span><span class="sxs-lookup"><span data-stu-id="35493-116">The last line is the last closing brace.</span></span> <span data-ttu-id="35493-117">Sformatuj linie przy użyciu czcionki Courier.</span><span class="sxs-lookup"><span data-stu-id="35493-117">Format the lines with the courier font.</span></span> <span data-ttu-id="35493-118">Sformatuj je przy użyciu nowego stylu i nazwij nowy styl "Code".</span><span class="sxs-lookup"><span data-stu-id="35493-118">Format them with a new style, and name the new style "Code".</span></span>

5. <span data-ttu-id="35493-119">Na koniec zaznacz cały wiersz zawierający dane wyjściowe i sformatuj go przy użyciu `Code` stylu.</span><span class="sxs-lookup"><span data-stu-id="35493-119">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>

6. <span data-ttu-id="35493-120">Zapisz dokument i nadaj mu nazwę SampleDoc.docx.</span><span class="sxs-lookup"><span data-stu-id="35493-120">Save the document, and name it SampleDoc.docx.</span></span>

    > [!NOTE]
    > <span data-ttu-id="35493-121">Jeśli używasz programu Microsoft Word 2003, wybierz pozycję **dokument programu Word 2007** na liście rozwijanej **Zapisz jako typ** .</span><span class="sxs-lookup"><span data-stu-id="35493-121">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>
