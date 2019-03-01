---
title: 'Instrukcje: Odczytywanie tekstu z plików za pomocą StreamReader (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 0ce3bffc151f149773c5279e1da08f74319b00f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968703"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Instrukcje: Odczytywanie tekstu z plików za pomocą StreamReader (Visual Basic)
`My.Computer.FileSystem` Obiektu udostępnia metody, aby otworzyć <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>. Te metody `OpenTextFileWriter` i `OpenTextFileReader`, są zaawansowane metody, które nie są wyświetlane w IntelliSense dopiero po wybraniu **wszystkich** kartę.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Aby odczytywać plik wiersz z czytnika tekstu  
  
-   Użyj `OpenTextFileReader` metodę, aby otworzyć <xref:System.IO.TextReader>, określenie pliku. W tym przykładzie otwiera plik o nazwie `testfile.txt`, odczytuje wiersz z niego i wyświetla wiersz w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Plik, który jest wczytywany musi być plikiem tekstowym.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby odczytać z pliku, zestaw wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission> klasy. Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md). Użytkownik musi również dostępu do pliku. Aby uzyskać więcej informacji, zobacz [Przegląd technologii ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog, składnik](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
