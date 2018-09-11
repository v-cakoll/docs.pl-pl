---
title: 'Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 894458ad6d69b8bb2836518b90723703733208b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264522"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic
`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do specjalnych katalogi, takich jak **Moje dokumenty** katalogu.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Aby zapisać nowych plików tekstowych w katalogu Moje dokumenty  
  
1.  Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwość, aby podać ścieżkę.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Użyj `WriteAllText` metodę, aby wpisać tekst w określonym pliku.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Zastąp `test.txt` nazwę pliku, o których mają zostać zapisane.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ten kod ponownie zgłasza wyjątki, które mogą wystąpić podczas zapisywania w pliku tekstowym. Można zmniejszyć prawdopodobieństwo wyjątków za pomocą kontrolek formularzy Windows Forms, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) składników, które ograniczyć wybór użytkownika z nazwami plików prawidłowe. Za pomocą tych kontrolek nie jest niezawodne, jednak. System plików można przełączać się między czasie użytkownik wybierze plik i czas, jaki kod jest wykonywany. Obsługa wyjątków jest niemal zawsze z pracy z plikami.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
 Ten przykład tworzy nowy plik. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć uprawnienia do tworzenia folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi uprawnienie, mniejsze uprawnienia tylko do zapisu. W przypadku, gdy jest to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić uprawnień do odczytu do pojedynczego pliku, a nie do przyznawania uprawnień Tworzenie folderu. Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub **Program Files** folderu. Aby uzyskać więcej informacji, zobacz [Przegląd technologii ACL](https://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
