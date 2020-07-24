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
# <a name="creating-the-source-office-open-xml-document-c"></a>Tworzenie źródłowego dokumentu Office Open XML (C#)

W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, który jest używany przez inne przykłady w tym samouczku. Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne z danymi wyjściowymi podanymi w każdym przykładzie.

Jednak przykłady w tym samouczku będą działały z dowolnym prawidłowym dokumentem WordprocessingML.

Aby utworzyć dokument, który jest wykorzystywany przez ten samouczek, musisz mieć zainstalowany Microsoft Office 2007 lub nowszy lub mieć Microsoft Office 2003 z pakietem zgodności Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.

## <a name="creating-the-wordprocessingml-document"></a>Tworzenie dokumentu WordprocessingML

#### <a name="to-create-the-wordprocessingml-document"></a>Aby utworzyć dokument WordprocessingML

1. Utwórz nowy dokument programu Microsoft Word.

2. Wklej następujący tekst do nowego dokumentu:

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

3. Sformatuj pierwszy wiersz za pomocą stylu "Nagłówek 1".

4. Wybierz wiersze zawierające kod w języku C#. Pierwszy wiersz rozpoczyna się od `using` słowa kluczowego. Ostatnim wierszem jest ostatni zamykający nawias klamrowy. Sformatuj linie przy użyciu czcionki Courier. Sformatuj je przy użyciu nowego stylu i nazwij nowy styl "Code".

5. Na koniec zaznacz cały wiersz zawierający dane wyjściowe i sformatuj go przy użyciu `Code` stylu.

6. Zapisz dokument i nadaj mu nazwę SampleDoc.docx.

    > [!NOTE]
    > Jeśli używasz programu Microsoft Word 2003, wybierz pozycję **dokument programu Word 2007** na liście rozwijanej **Zapisz jako typ** .
