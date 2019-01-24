---
title: Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 124f22e3a4b3e43dd454aca9389691a89debcf6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617450"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a>Tworzenie źródłowego dokumentu Office Open XML (Visual Basic)
W tym temacie przedstawiono sposób tworzenia dokumentu Office Open XML WordprocessingML, używanego przez inne przykłady w tym samouczku. Jeśli wykonasz te instrukcje, dane wyjściowe będą zgodne dane wyjściowe w każdym przykładzie.  
  
 Jednak na potrzeby przykładów w tym samouczku będą działać z dowolny prawidłowy dokument WordprocessingML.  
  
 Aby utworzyć dokument, który korzysta z tego samouczka, musi mieć pakietu Microsoft Office 2007 lub nowszy zainstalowany lub konieczne jest posiadanie programu Microsoft Office 2003 za pomocą pakietu Microsoft Office zgodności dla programu Word, Excel i PowerPoint 2007 formatów.  
  
## <a name="creating-the-wordprocessingml-document"></a>Tworzenie dokumentu WordprocessingML  
  
#### <a name="to-create-the-wordprocessingml-document"></a>Aby utworzyć dokument WordprocessingML  
  
1.  Utwórz nowy dokument programu Microsoft Word.  
  
2.  Wklej następujący tekst do nowego dokumentu:  
  
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
  
3.  Formatuj pierwszy wiersz ze stylem "Nagłówek 1".  
  
4.  Wybierz wiersze, które zawierają kod języka Visual Basic. Pierwszy wiersz zaczyna się od `Imports` — słowo kluczowe. Ostatni wiersz jest "End Class". Formatuj wierszy przy użyciu czcionki courier. Formatuj je przy użyciu nowego stylu i nazwę nowego stylu "Code".  
  
5.  Na koniec zaznacz całą linię, która zawiera dane wyjściowe i sformatować je za pomocą `Code` stylu.  
  
6.  Zapisz dokument, a następnie nadaj mu nazwę SampleDoc.docx.  
  
    > [!NOTE]
    >  Jeśli używasz programu Microsoft Word 2003, wybierz opcję **dokument programu Word 2007** w **Zapisz jako typ** listy rozwijanej.  
  
## <a name="see-also"></a>Zobacz także
- [Samouczek: Manipulowanie zawartością w dokumencie WordprocessingML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
