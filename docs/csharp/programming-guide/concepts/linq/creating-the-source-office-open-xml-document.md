---
title: Tworzenie źródłowego dokumentu Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: da93791432c45b5e7ee69b69fa716610ac349377
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486181"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Tworzenie źródłowego dokumentu Office Open XML (C#)
W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, używanego przez inne przykłady w tym samouczku. Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne dane wyjściowe w każdym przykładzie.  
  
 Jednak na potrzeby przykładów w tym samouczku będą działać z dowolny prawidłowy dokument WordprocessingML.  
  
 Aby utworzyć dokument, który korzysta z tego samouczka, musi mieć pakietu Microsoft Office 2007 lub nowszy zainstalowany lub konieczne jest posiadanie programu Microsoft Office 2003 za pomocą pakietu Microsoft Office zgodności dla programu Word, Excel i PowerPoint 2007 formatów.  
  
## <a name="creating-the-wordprocessingml-document"></a>Tworzenie dokumentu WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Aby utworzyć dokument WordprocessingML  
  
1. Utwórz nowy dokument programu Microsoft Word.  
  
2. Wklej następujący tekst do nowego dokumentu:  
  
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
  
3. Formatuj pierwszy wiersz ze stylem "Nagłówek 1".  
  
4. Wybierz wiersze, które zawierają kod C#. Pierwszy wiersz zaczyna się od `using` — słowo kluczowe. Ostatni wiersz jest ostatni nawias zamykający. Formatuj wierszy przy użyciu czcionki courier. Formatuj je przy użyciu nowego stylu i nazwę nowego stylu "Code".  
  
5. Na koniec zaznacz całą linię, która zawiera dane wyjściowe i sformatować je za pomocą `Code` stylu.  
  
6. Zapisz dokument, a następnie nadaj mu nazwę SampleDoc.docx.  
  
    > [!NOTE]
    >  Jeśli używasz programu Microsoft Word 2003, wybierz opcję **dokument programu Word 2007** w **Zapisz jako typ** listy rozwijanej.  
  
