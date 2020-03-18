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
# <a name="creating-the-source-office-open-xml-document-c"></a>Tworzenie dokumentu XML pakietu Source Office Open (C#)

W tym temacie pokazano, jak utworzyć dokument WordprocessingML języka XML pakietu Office, którego używają inne przykłady w tym samouczku. Jeśli postępujesz zgodnie z tymi instrukcjami, dane wyjściowe będą zgodne z danymi wyjściowymi podanymi w każdym przykładzie.

Jednak przykłady w tym samouczku będzie działać z dowolnego prawidłowego dokumentu WordprocessingML.

Aby utworzyć dokument, którego używa ten samouczek, musisz mieć zainstalowany pakiet Microsoft Office 2007 lub nowszy lub mieć pakiet Microsoft Office 2003 z pakietem zgodności pakietu Microsoft Office dla formatów plików programów Word, Excel i PowerPoint 2007.

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

4. Wybierz wiersze zawierające kod C#. Pierwszy wiersz zaczyna `using` się od słowa kluczowego. Ostatni wiersz jest ostatnim nawiasem zamykającym. Sformatuj wiersze za pomocą czcionki kuriera. Sformatuj je nowym stylem i nazwij nowy styl "Kod".

5. Na koniec zaznacz cały wiersz zawierający dane wyjściowe `Code` i sformatuj go za pomocą stylu.

6. Zapisz dokument i najmimij jego nazwę SampleDoc.docx.

    > [!NOTE]
    > Jeśli używasz programu Microsoft Word 2003, wybierz **pozycję Dokument programu Word 2007** z listy rozwijanej Zapisz jako **typ.**
