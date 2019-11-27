---
title: Przechowywanie danych i odczytywanie ich ze schowka
ms.date: 07/20/2015
helpviewer_keywords:
- Clipboard, storing data to (My.Computer.Clipboard)
- Clipboard, reading from (My.Computer.Clipboard)
- Clipboard
- My.Computer.Clipboard object, tasks
- data [Visual Basic], Clipboard
- reading data, from Clipboard
ms.assetid: f690119a-4378-4f7d-b20e-d9377ef49496
ms.openlocfilehash: 243fb237f3f9ba53f8b29079df08531c102c78dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349735"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Przechowywanie danych i odczytywanie ich ze schowka (Visual Basic)

Schowek może służyć do przechowywania danych, takich jak tekst i obrazy. Ze względu na to, że Schowek jest współużytkowany przez wszystkie aktywne procesy, można go użyć do transferowania danych między nimi. Obiekt `My.Computer.Clipboard` umożliwia łatwe uzyskiwanie dostępu do schowka oraz odczytywanie i zapisywanie w nim.  
  
## <a name="reading-from-the-clipboard"></a>Odczytywanie ze schowka  

 Użyj metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A>, aby odczytać tekst w Schowku. Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu. Aby przykład mógł działać poprawnie, musi być zapisany tekst w Schowku.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > schowka**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Użyj metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A>, aby pobrać obraz ze schowka. Ten przykład sprawdza, czy na schowku znajduje się obraz przed pobraniem go i przypisanie do `PictureBox1`.  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **Windows Forms aplikacje > schowka**. Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Elementy umieszczone w schowku będą przechowywane nawet po zamknięciu aplikacji.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Określanie typu pliku przechowywanego w schowku  

 Dane w schowku mogą przyjmować różne formy, takie jak tekst, plik dźwiękowy lub obraz. Aby określić, jakie sortowanie plików znajduje się w schowku, możesz użyć metod, takich jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. Metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> można użyć, jeśli masz format niestandardowy, który chcesz sprawdzić.  
  
 Użyj funkcji `ContainsImage`, aby określić, czy dane zawarte w schowku są obrazem. Poniższy kod sprawdza, czy dane są odpowiednio obrazem i raportami.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Czyszczenie schowka  

 Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> czyści zawartość schowka. Ze względu na to, że Schowek jest współużytkowany przez inne procesy, jego czyszczenie może mieć wpływ na te procesy.  
  
 Poniższy kod pokazuje, jak używać metody `Clear`.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Zapisywanie w schowku  

 Użyj metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A>, aby zapisać tekst do Schowka. Poniższy kod zapisuje ciąg "to jest ciąg testowy" do Schowka.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Metoda `SetText` może akceptować parametr formatu, który zawiera typ <xref:System.Windows.Forms.TextDataFormat>. Poniższy kod zapisuje ciąg "to jest ciąg testowy" do Schowka jako tekst RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Użyj metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A>, aby zapisać dane do Schowka. Ten przykład zapisuje `DataObject` `dataChunk` do Schowka w `specialFormat`formacie niestandardowym.  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Użyj metody <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A>, aby napisać dane audio do Schowka. Ten przykład tworzy tablicę bajtową `musicReader`, odczytuje `cool.wav` do niej plik, a następnie zapisuje ją w Schowku.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Ze względu na to, że można uzyskać dostęp do schowka przez innych użytkowników, nie należy używać go do przechowywania poufnych informacji, takich jak hasła lub dane poufne.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Instrukcje: odczytywanie danych o obiektach z pliku XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Instrukcje: wpisywanie danych o obiektach do pliku XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
