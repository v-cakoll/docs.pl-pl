---
title: 'Porady: odczyt tekstu z plików za pomocą StreamReader'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 572463d1f03d768fb133f2dac59b012051f053bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334562"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Porady: odczyt tekstu z plików za pomocą StreamReader (Visual Basic)

Obiekt `My.Computer.FileSystem` zawiera metody otwierania <xref:System.IO.TextReader> <xref:System.IO.TextWriter>a i . Te metody `OpenTextFileWriter` `OpenTextFileReader`i , są zaawansowane metody, które nie są wyświetlane w IntelliSense, chyba że wybierzesz **Wszystkie** kartę.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Aby odczytać wiersz z pliku z czytnikiem tekstu  
  
- Użyj `OpenTextFileReader` metody, aby <xref:System.IO.TextReader>otworzyć , określając plik. W tym przykładzie `testfile.txt`otwiera się plik o nazwie , odczytuje wiersz z niego i wyświetla wiersz w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Plik, który jest odczytywany musi być plik tekstowy.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plikiem źródłowym języka Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Do odczytu z pliku zestawu wymaga poziomu uprawnień przyznanego przez <xref:System.Security.Permissions.FileIOPermission> klasę. Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md). Użytkownik potrzebuje również dostępu do pliku. Aby uzyskać więcej informacji, zobacz [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog, składnik](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
