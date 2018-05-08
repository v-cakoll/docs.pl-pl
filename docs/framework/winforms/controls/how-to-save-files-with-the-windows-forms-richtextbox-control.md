---
title: 'Porady: zapisywanie plików za pomocą formantu RichTextBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: c50b2f3309c1f811b29e824327a709e2cc4bd791
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Porady: zapisywanie plików za pomocą formantu RichTextBox formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant może zapisać informacji wyświetlanych w jednym z kilku formatów:  
  
-   Zwykły tekst  
  
-   Unicode zwykłego tekstu  
  
-   Format tekstu sformatowanego (RTF)  
  
-   RTF spacji zamiast obiektów OLE  
  
-   Zwykły tekst z reprezentacji tekstowej obiektów OLE  
  
 Aby zapisać plik, należy wywołać <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody. Można również użyć **SaveFile** metody w celu zapisywania do strumienia danych. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Aby zapisać zawartość formantu w pliku  
  
1.  Określ ścieżkę pliku do zapisania.  
  
     Aby to zrobić w rzeczywistych aplikacjach, należy zwykle użyć <xref:System.Windows.Forms.SaveFileDialog> składnika. Aby uzyskać ogólne informacje, zobacz [savefiledialog — informacje o składniku](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).  
  
2.  Wywołanie <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody <xref:System.Windows.Forms.RichTextBox> kontroli określenie pliku do zapisania i opcjonalnie typu pliku. Jeśli należy wywołać metodę jako jej argument tylko nazwą pliku, plik zostanie zapisany jako RTF. Aby określić plik innego typu, należy wywołać metodę o wartości <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenie jako drugi argument.  
  
     W poniższym przykładzie ścieżka ustawiona dla lokalizacji pliku RTF jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów z systemem operacyjnym Windows. Wybranie tej lokalizacji również umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.RichTextBox> kontroli już dodany.  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja wymaga dostępu Tworzenie folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi tylko dostęp do zapisu, niższego poziomu uprawnień. Jeśli to możliwe, jest bezpieczniejsza do utworzenia pliku podczas wdrażania i tylko dostęp do jednego pliku, zamiast tworzyć dostępu dla folderu. Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox, kontrolka](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
