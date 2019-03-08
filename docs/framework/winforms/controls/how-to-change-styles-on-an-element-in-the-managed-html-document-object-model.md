---
title: 'Instrukcje: Zmienianie stylu elementu w modelu obiektów zarządzanych dokumentów HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: ad91f7591e2fa07605fe4f7ac026b7c969ab7ef0
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678940"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Instrukcje: Zmienianie stylu elementu w modelu obiektów zarządzanych dokumentów HTML

Aby sterować wyglądem dokumentu i jej elementów, można użyć style w formacie HTML. <xref:System.Windows.Forms.HtmlDocument> i <xref:System.Windows.Forms.HtmlElement> obsługuje <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwości, które pobierają ciągi stylu następujący format:

`name1:value1;...;nameN:valueN;`

Oto `DIV` ciągiem styl, który ustawia czcionka Arial i cały tekst pogrubiony:

`<DIV style="font-face:arial;font-weight:bold;">`

`Hello, world!`

`</DIV>`

Problem dotyczący manipulowanie stylów za pomocą <xref:System.Windows.Forms.HtmlElement.Style%2A> właściwość jest, że można potwierdzić kłopotliwe dodać do, a następnie usuń ustawienia stylu pracy z ciągu. Na przykład stałyby złożonych procedurę renderowania poprzedni tekst kursywą zawsze wtedy, gdy użytkownik umieszcza kursor nad `DIV`i kursywa wyłączone, gdy kursor opuszcza `DIV`. Czas może stać się problemem, jeśli zachodzi potrzeba manipulowania dużej liczby style w ten sposób.

Poniższa procedura zawiera kod, który umożliwia łatwe manipulowanie stylów, dokumenty HTML i elementów. Procedura wymaga, że wiesz, jak wykonać podstawowe zadania w Windows Forms, takie jak tworzenie nowego projektu i dodawanie formantu do formularza.

### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Aby przetworzyć zmiany stylów w aplikacji Windows Forms

1. Utwórz nowy projekt Windows Forms.

2. Utwórz nowy plik klasy kończące się na rozszerzenie, które są odpowiednie dla języka programowania.

3. Kopiuj `StyleGenerator` klasy kod w sekcji przykład tego tematu w pliku klasy, a następnie zapisz kod.

4. Zapisz poniższy kod HTML w pliku o nazwie Test.htm.

    ```html
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

5. Dodaj <xref:System.Windows.Forms.WebBrowser> formantu o nazwie `webBrowser1` do formularza głównego projektu.

6. Dodaj następujący kod do pliku kodu projektu.

    > [!IMPORTANT]
    > Upewnij się, że `webBrowser1_DocumentCompleted` programu obsługi zdarzeń jest skonfigurowany jako odbiornika dla <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zdarzeń. W programie Visual Studio, kliknij dwukrotnie <xref:System.Windows.Forms.WebBrowser> formant; w edytorze tekstów, skonfiguruj odbiornik programowo.

    [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
    [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]

7. Uruchom projekt. Uruchom kursor nad pierwszym `DIV` aby obserwować wyniki kodu.

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje pełny kod `StyleGenerator` klasy, która analizuje istniejącą wartość stylu, obsługuje dodawanie, zmienianie i usuwanie stylów i zwraca nową wartość stylu z żądanych zmian.

[!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
[!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.HtmlElement>
