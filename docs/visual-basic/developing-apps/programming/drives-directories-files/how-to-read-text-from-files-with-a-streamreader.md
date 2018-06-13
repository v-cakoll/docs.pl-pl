---
title: 'Porady: odczyt tekstu z plików za pomocą StreamReader (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: cd6f7b70f2ddabfc5a1476c45ca9813b9a4d949f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588658"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Porady: odczyt tekstu z plików za pomocą StreamReader (Visual Basic)
`My.Computer.FileSystem` Obiektu udostępnia metody, aby otworzyć <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>. Te metody `OpenTextFileWriter` i `OpenTextFileReader`, są zaawansowane metody, które nie są wyświetlane w IntelliSense dopiero po wybraniu **wszystkie** kartę.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Aby wiersz z pliku do odczytu z czytnika tekstu  
  
-   Użyj `OpenTextFileReader` metodę, aby otworzyć <xref:System.IO.TextReader>, określenie pliku. W tym przykładzie otwiera plik o nazwie `testfile.txt`odczytuje wiersz z niego i wyświetla wiersz w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Plik, który jest do odczytu musi być plikiem tekstowym.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Aby odczytać z pliku, używanemu zestawowi wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission> klasy. Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md). Użytkownik musi również dostęp do pliku. Aby uzyskać więcej informacji, zobacz [omówienie technologii ACL](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>  
 [SaveFileDialog, składnik](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)  
 [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
