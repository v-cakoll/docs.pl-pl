---
title: 'Instrukcje: zapisywanie plików za pomocą kontrolki RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: 4784ddd563ccec0f7e6271700781ee1b5d3ac105
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318419"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a>Instrukcje: zapisywanie plików za pomocą kontrolki RichTextBox formularzy systemu Windows
Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontroli można zapisać informacji wyświetlanych w jednym z kilku formatów:  
  
-   Zwykły tekst  
  
-   Zwykły tekst w formacie Unicode  
  
-   Format tekstu sformatowanego (RTF)  
  
-   RTF spacji zamiast obiektów OLE  
  
-   Zwykły tekst z reprezentacji tekstowej obiektów OLE  
  
 Aby zapisać plik, należy wywołać <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody. Można również użyć **SaveFile** metody, aby zapisać dane w strumieniu. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a>Aby zapisać zawartości formantu w pliku  
  
1. Określ ścieżkę do pliku do zapisania.  
  
     Aby to zrobić w aplikacji rzeczywistych, zazwyczaj używasz <xref:System.Windows.Forms.SaveFileDialog> składnika. Aby uzyskać przegląd, zobacz [savefiledialog — informacje o składniku](savefiledialog-component-overview-windows-forms.md).  
  
2. Wywołaj <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody <xref:System.Windows.Forms.RichTextBox> kontrolki, określając plik, aby zapisać i opcjonalnie typu pliku. Jeśli chcesz wywołać metodę z nazwą pliku jako argument tylko, plik zostanie zapisany jako RTF. Aby określić inny typ pliku, należy wywołać metodę z wartością <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenia jako swój drugi argument.  
  
     W poniższym przykładzie ścieżkę zestawu dla lokalizacji pliku RTF jest **Moje dokumenty** folderu. Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego folderu. Wybranie tej lokalizacji również umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji. W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.RichTextBox> formant został już dodany.  
  
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
    >  W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć dostęp do tworzenia folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi jedynie dostęp do zapisu, mniejsze uprawnienia. W przypadku, gdy jest to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i tylko przyznać dostęp do odczytu do pojedynczego pliku zamiast tworzyć dostępu do folderu. Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub do folderu Program Files.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
