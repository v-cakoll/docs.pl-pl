---
title: 'Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bc62f2bc63a2ea185b8ea4c8d271dd28d347d6f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334522"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic

Obiekt `My.Computer.FileSystem.SpecialDirectories` umożliwia dostęp do katalogów specjalnych, takich jak katalog **MyDocuments.**  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Aby zapisać nowe pliki tekstowe w katalogu Moje dokumenty  
  
1. Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwości, aby dostarczyć ścieżkę.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. `WriteAllText` Metoda pisania tekstu do określonego pliku służy do pisania tekstu.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Zamień `test.txt` na nazwę pliku, do którego chcesz napisać.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Ten kod ponownie powoduje wszystkie wyjątki, które mogą wystąpić podczas pisania tekstu do pliku. Można zmniejszyć prawdopodobieństwo wyjątków przy użyciu formantów windows forms, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) składników, które ograniczają wybór użytkownika do prawidłowych nazw plików. Korzystanie z tych formantów nie jest niezawodny, jednak. System plików może zmieniać się między czasem wyboru pliku przez użytkownika a czasem wykonywania kodu. Obsługa wyjątków jest zatem prawie zawsze konieczne podczas pracy z plikami.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).  
  
 W tym przykładzie tworzy nowy plik. Jeśli aplikacja musi utworzyć plik, ta aplikacja potrzebuje uprawnienia Utwórz dla folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja wymaga tylko uprawnienia zapisu, mniejsze uprawnienia. Tam, gdzie to możliwe, jest bardziej bezpieczne, aby utworzyć plik podczas wdrażania i tylko przyznać uprawnienia odczytu do jednego pliku, a nie do przyznania create uprawnień dla folderu. Ponadto bezpieczniej jest zapisywać dane w folderach użytkownika niż w folderze głównym lub folderze **Pliki programu.** Aby uzyskać więcej informacji, zobacz [ACL Technology Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
