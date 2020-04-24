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

`My.Computer.FileSystem` Obiekt zawiera metody umożliwiające otwarcie <xref:System.IO.TextReader> a i <xref:System.IO.TextWriter>. Te metody `OpenTextFileWriter` i `OpenTextFileReader`są metodami zaawansowanymi, które nie są wyświetlane w technologii IntelliSense, chyba że zostanie wybrana karta **wszystkie** .  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Aby odczytać wiersz z pliku za pomocą czytnika tekstu  
  
- Użyj `OpenTextFileReader` metody <xref:System.IO.TextReader>, aby otworzyć, określając plik. Ten przykład otwiera plik o nazwie `testfile.txt`, odczytuje z niego wiersz i wyświetla wiersz w oknie komunikatu.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Odczytywany plik musi być plikiem tekstowym.  
  
 Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.  
  
 Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Aby odczytywać dane z pliku, zestaw wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.FileIOPermission> klasę. Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md). Użytkownik musi również mieć dostęp do pliku. Aby uzyskać więcej informacji, zobacz [Omówienie technologii list ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [SaveFileDialog, składnik](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Odczyt z plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
