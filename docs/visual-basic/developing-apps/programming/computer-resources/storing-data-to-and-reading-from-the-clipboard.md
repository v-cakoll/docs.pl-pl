---
title: Zapisywanie danych i odczytywania ze Schowka (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: eb8ae25f260ed434c4aafcc064be8fb6bebaaac1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591382"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Zapisywanie danych i odczytywania ze Schowka (Visual Basic)
Schowek może służyć do przechowywania danych, takich jak tekst i obrazy. Ponieważ Schowka jest wspólna dla wszystkich aktywnych procesów, może służyć do transferu danych między nimi. `My.Computer.Clipboard` Obiektu pozwala łatwo uzyskiwać dostęp do Schowka i można odczytywać i zapisywać do niego.  
  
## <a name="reading-from-the-clipboard"></a>Odczytywanie ze Schowka  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> metody tekstu w Schowku. Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu. Musi to być tekstu w Schowku, na przykład aby działała poprawnie.  
  
 [!code-vb[VbVbcnMyClipboard#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_1.vb)]  
  
 W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > Schowka**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> metoda pobierania obraz ze Schowka. W tym przykładzie sprawdza, czy jest obraz w Schowku przed ich pobraniem i przypisywania go do `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_2.vb)]  
  
 W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **aplikacjach formularzy systemu Windows > Schowka**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
 Elementy umieszczane w Schowku pozostają, nawet po zamknięciu aplikacji.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Określanie typu pliku przechowywanych w Schowku  
 Dane w Schowku może zająć wiele różnych formularzy, takich jak tekst, plik dźwiękowy lub obraz. Aby określić, jaki rodzaj plików jest w Schowku, można użyć metody takie jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> Metody można użyć, jeśli masz formatu niestandardowego, który chcesz sprawdzić.  
  
 Użyj `ContainsImage` funkcji, aby określić, czy dane zawarte w Schowku jest obraz. Poniższy kod sprawdza, czy dane są obrazu i odpowiednio raportów.  
  
 [!code-vb[VbResourceTasks#13](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_3.vb)]  
  
## <a name="clearing-the-clipboard"></a>Wyczyszczenie Schowka  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> Metody czyści Schowka. Ponieważ Schowek jest współużytkowana przez inne procesy, czyszczenie może mieć wpływ na tych procesów.  
  
 Poniższy kod przedstawia sposób użycia `Clear` metody.  
  
 [!code-vb[VbVbcnMyClipboard#3](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_4.vb)]  
  
## <a name="writing-to-the-clipboard"></a>Zapisywanie do Schowka  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> metodę zapisywanie tekstu do Schowka. Poniższy kod zapisuje ciąg "To jest test ciąg" do Schowka.  
  
 [!code-vb[VbVbcnMyClipboard#1](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_5.vb)]  
  
 `SetText` Metody może akceptować parametr formatu, który zawiera typ <xref:System.Windows.Forms.TextDataFormat>. Poniższy kod zapisuje ciąg "To jest test ciąg" do Schowka jako tekst w formacie RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_6.vb)]  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> metody można zapisać danych do Schowka. W tym przykładzie zapisuje `DataObject``dataChunk` do Schowka w formatu niestandardowego `specialFormat`.  
  
 [!code-vb[VbVbcnMyClipboard#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_7.vb)]  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> metody można zapisać danych do Schowka. W tym przykładzie tworzy tablicę bajtów `musicReader`, odczytuje plik `cool.wav` i zapisuje go do Schowka.  
  
 [!code-vb[VbResourceTasks#5](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/storing-data-to-and-reading-from-the-clipboard_8.vb)]  
  
> [!IMPORTANT]
>  Ponieważ przez innych użytkowników można uzyskać dostępu do Schowka, nie jest używana do przechowywania poufne informacje, takie jak hasła lub poufnych danych.  
  
## <a name="see-also"></a>Zobacz także  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>  
 <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>  
 [Instrukcje: odczytywanie danych o obiektach z pliku XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [Instrukcje: wpisywanie danych o obiektach do pliku XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
