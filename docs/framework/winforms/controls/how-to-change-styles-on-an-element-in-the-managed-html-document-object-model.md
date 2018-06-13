---
title: 'Porady: zmienianie stylu elementu w modelu DOM (Document Object Model) zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 9ecb6b90508ca53e3801a633ac2444426e2f8113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531254"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Porady: zmienianie stylu elementu w modelu DOM (Document Object Model) zarządzanych dokumentów HTML
Aby sterować wyglądem dokumentu i jego elementów, można użyć style w formacie HTML. <xref:System.Windows.Forms.HtmlDocument> i <xref:System.Windows.Forms.HtmlElement> obsługuje <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwości, które pobierają ciągi styl następujący format:  
  
 `name1:value1;...;nameN:valueN;`  
  
 Oto `DIV` ciągiem styl, który ustawia czcionkę Arial i cały tekst, które mają zostać pogrubione:  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 Problem z manipulowanie stylów za pomocą <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwość jest, że może okazać skomplikowane, aby dodać do, a następnie usuń ustawień stylu z ciągu. Na przykład go staje się złożona procedura umożliwiające renderowanie poprzedniego tekstu kursywą zawsze, gdy użytkownik umieszcza kursor nad `DIV`i podjąć kursywa poza gdy kursor opuszcza `DIV`. Czas może stać się problemem, jeśli potrzebujesz do manipulowania dużą liczbę style w ten sposób.  
  
 Poniższa procedura zawiera kod, który umożliwia łatwe manipulowania style dla dokumentów HTML i elementów. Procedura wymaga się, że wiesz, jak wykonać podstawowe zadania w formularzach systemu Windows, takie jak tworzenie nowego projektu i dodawanie formantu do formularza.  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Aby przetwarzać zmiany stylu w aplikacji formularzy systemu Windows  
  
1.  Utwórz nowy projekt formularzy systemu Windows.  
  
2.  Utwórz nowy plik klasy końcowy w rozszerzeniu właściwe dla języka programowania.  
  
3.  Kopiuj `StyleGenerator` klasy kodu w przykładzie sekcji tego tematu w pliku klasy, a następnie zapisz kod.  
  
4.  Zapisz plik o nazwie Test.htm poniższy kod HTML.  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  Dodaj <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1` w formularzu głównym projektu.  
  
6.  Dodaj następujący kod do pliku kodu projektu.  
  
    > [!IMPORTANT]
    >  Upewnij się, że `webBrowser1_DocumentCompleted` programu obsługi zdarzeń jest skonfigurowany jako odbiornika dla <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń. W programie Visual Studio, kliknij dwukrotnie <xref:System.Windows.Forms.WebBrowser> kontrolować; w edytorze tekstów, skonfiguruj odbiornik programowo.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Uruchom projekt. Uruchom kursor nad pierwszy `DIV` obserwować efekty kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia pełny kod `StyleGenerator` obsługuje klasy, która analizuje istniejącej wartości stylu, dodawanie, zmienianie i usuwanie style i zwraca nową wartość stylu z żądanych zmian.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.HtmlElement>
