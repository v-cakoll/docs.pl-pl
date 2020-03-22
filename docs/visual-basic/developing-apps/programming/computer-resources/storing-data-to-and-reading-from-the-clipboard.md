---
title: Przechowywanie danych i odczytywanie ze Schowka
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349735"
---
# <a name="storing-data-to-and-reading-from-the-clipboard-visual-basic"></a>Przechowywanie danych i odczytywanie ze Schowka (Visual Basic)

Schowek może służyć do przechowywania danych, takich jak tekst i obrazy. Ponieważ Schowek jest współużytkowane przez wszystkie aktywne procesy, może służyć do przesyłania danych między nimi. Obiekt `My.Computer.Clipboard` umożliwia łatwy dostęp do Schowka oraz odczyt i zapis do niego.  
  
## <a name="reading-from-the-clipboard"></a>Czytanie ze Schowka  

 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetText%2A> tej metody, aby odczytać tekst w Schowku. Poniższy kod odczytuje tekst i wyświetla go w oknie komunikatu. Aby przykład działał poprawnie, musi być przechowywany tekst.  
  
 [!code-vb[VbVbcnMyClipboard#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#4)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > Schowek**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetImage%2A> tej metody, aby pobrać obraz ze Schowka. W tym przykładzie sprawdza, czy w Schowku znajduje się `PictureBox1`obraz przed pobraniem go i przypisaniem go do programu .  
  
 [!code-vb[VbResourceTasks#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#16)]  
  
 W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense. W selektorze fragmentów kodu znajduje się w **aplikacji windows formularzy > Schowek**. Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).  
  
 Elementy umieszczone w Schowku będą zachowywać się nawet po zamknięciu aplikacji.  
  
## <a name="determining-the-type-of-file-stored-in-the-clipboard"></a>Określanie typu pliku przechowywanego w Schowku  

 Dane w Schowku mogą przybierać różne formy, takie jak tekst, plik audio lub obraz. Aby określić, jaki rodzaj pliku znajduje się w Schowku, można użyć takich metod, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsAudio%2A>jak <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsFileDropList%2A>, <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsImage%2A>, i <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsText%2A>. Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.ContainsData%2A> może być używana, jeśli masz format niestandardowy, który chcesz sprawdzić.  
  
 Użyj `ContainsImage` tej funkcji, aby określić, czy dane zawarte w Schowku są obrazem. Poniższy kod sprawdza, czy dane są obrazem i odpowiednio raportuje.  
  
 [!code-vb[VbResourceTasks#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#13)]  
  
## <a name="clearing-the-clipboard"></a>Czyszczenie Schowka  

 Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.Clear%2A> czyści Schowek. Ponieważ Schowek jest współużytkowane przez inne procesy, wyczyszczenie może mieć wpływ na te procesy.  
  
 Poniższy kod pokazuje, `Clear` jak używać metody.  
  
 [!code-vb[VbVbcnMyClipboard#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#3)]  
  
## <a name="writing-to-the-clipboard"></a>Pisanie do Schowka  

 Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetText%2A> pisania tekstu w Schowku służy do pisania tekstu. Poniższy kod zapisuje ciąg "To jest ciąg testowy" do Schowka.  
  
 [!code-vb[VbVbcnMyClipboard#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#1)]  
  
 Metoda `SetText` może zaakceptować parametr formatu, <xref:System.Windows.Forms.TextDataFormat>który zawiera typ . Poniższy kod zapisuje ciąg "To jest ciąg testowy" do Schowka jako tekst RTF.  
  
 [!code-vb[VbVbcnMyClipboard#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#2)]  
  
 Metoda <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetData%2A> zapisywania danych w Schowku służy do zapisywania danych. W tym przykładzie `DataObject` `dataChunk` zapisuje do Schowka w formacie `specialFormat`niestandardowym .  
  
 [!code-vb[VbVbcnMyClipboard#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyClipboard/VB/Class1.vb#7)]  
  
 Użyj <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetAudio%2A> tej metody, aby zapisać dane audio w Schowku. W tym przykładzie `musicReader`tworzy tablicę `cool.wav` bajtów , odczytuje plik do niego, a następnie zapisuje go w Schowku.  
  
 [!code-vb[VbResourceTasks#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#5)]  
  
> [!IMPORTANT]
> Ponieważ Schowek jest dostępny dla innych użytkowników, nie należy go używać do przechowywania poufnych informacji, takich jak hasła lub poufne dane.  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.GetAudioStream%2A>
- <xref:Microsoft.VisualBasic.MyServices.ClipboardProxy.SetDataObject%2A>
- [Jak: Odczyt danych obiektu z pliku XML](../../../programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [Jak: Zapisywanie danych obiektów w pliku XML](../../../programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
