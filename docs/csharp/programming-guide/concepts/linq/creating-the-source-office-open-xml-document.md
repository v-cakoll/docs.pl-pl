---
title: Tworzenie dokumentu źródłowego Office Open XML (C#)
ms.date: 07/20/2015
ms.assetid: 653c8cdb-73be-4dc2-927f-924cfb4ed9ed
ms.openlocfilehash: c5884d1e34558d01be4c873c3f44222396e588ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324502"
---
# <a name="creating-the-source-office-open-xml-document-c"></a>Tworzenie dokumentu źródłowego Office Open XML (C#)
W tym temacie przedstawiono sposób tworzenia dokumentu schemat WordprocessingML Office Open XML używanego przez inne przykłady w tym samouczku. Jeśli wykonaj te instrukcje, danych wyjściowych będzie zgodny w każdym przykładzie danych wyjściowych.  
  
 Jednak przykłady w tym samouczku będzie działać z dowolnego prawidłowego dokumentu schemat WordprocessingML.  
  
 Aby utworzyć dokument, który korzysta z tego samouczka, muszą mieć Microsoft Office 2007 lub nowszej lub Microsoft Office 2003 z pakietu Microsoft Office zgodności musi mieć dla programów Word, Excel i PowerPoint 2007.  
  
## <a name="creating-the-wordprocessingml-document"></a>Tworzenie dokumentu schemat WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Aby utworzyć schemat WordprocessingML dokumentu  
  
1.  Utwórz nowy dokument programu Microsoft Word.  
  
2.  Wklej poniższy tekst do nowego dokumentu:  
  
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
  
3.  Pierwszy wiersz należy sformatować przy użyciu stylu "Nagłówek 1".  
  
4.  Wybierz wiersze, które zawierają kod C#. Pierwszy wiersz rozpoczyna się od `using` — słowo kluczowe. Ostatni wiersz jest ostatnim zamykający nawias klamrowy. Formatuj linie czcionką courier. Sformatowane nowy styl i nazwę nowego stylu 'Code'.  
  
5.  Na koniec wybierz cały wiersz, który zawiera dane wyjściowe i sformatować go przy użyciu `Code` stylu.  
  
6.  Zapisz dokument i nadaj mu nazwę SampleDoc.docx.  
  
    > [!NOTE]
    >  Jeśli korzystasz z programu Microsoft Word 2003, wybierz **dokument programu Word 2007** w **Zapisz jako typ** listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
