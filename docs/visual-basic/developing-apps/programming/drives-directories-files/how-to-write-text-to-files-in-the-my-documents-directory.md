---
title: 'Instrukcje: Zapisywanie tekstu do plików w katalogu Moje dokumenty w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: 4f9eb4c9e0eb92712b5ea1a4feef24f2bb95d70b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772570"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Instrukcje: Zapisywanie tekstu do plików w katalogu Moje dokumenty w języku Visual Basic
`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do specjalnych katalogi, takich jak **Moje dokumenty** katalogu.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Aby zapisać nowych plików tekstowych w katalogu Moje dokumenty  
  
1. Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwość, aby podać ścieżkę.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Użyj `WriteAllText` metodę, aby wpisać tekst w określonym pliku.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Zastąp `test.txt` nazwę pliku, o których mają zostać zapisane.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ten kod ponownie zgłasza wyjątki, które mogą wystąpić podczas zapisywania w pliku tekstowym. Można zmniejszyć prawdopodobieństwo wyjątków za pomocą kontrolek formularzy Windows Forms, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) składników, które ograniczyć wybór użytkownika z nazwami plików prawidłowe. Za pomocą tych kontrolek nie jest niezawodne, jednak. System plików można przełączać się między czasie użytkownik wybierze plik i czas, jaki kod jest wykonywany. Obsługa wyjątków jest niemal zawsze z pracy z plikami.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
 Ten przykład tworzy nowy plik. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć uprawnienia do tworzenia folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi uprawnienie, mniejsze uprawnienia tylko do zapisu. W przypadku, gdy jest to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić uprawnień do odczytu do pojedynczego pliku, a nie do przyznawania uprawnień Tworzenie folderu. Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub **Program Files** folderu. Aby uzyskać więcej informacji, zobacz [Przegląd technologii ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
