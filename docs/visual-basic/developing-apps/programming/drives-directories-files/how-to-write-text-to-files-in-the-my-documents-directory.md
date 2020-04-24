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

`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do katalogów specjalnych, takich jak katalog **WebDocuments** .  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Aby napisać nowe pliki tekstowe w katalogu Moje dokumenty  
  
1. Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwości, aby podać ścieżkę.  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. Użyj metody `WriteAllText` , aby zapisać tekst do określonego pliku.  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  

 Zamień `test.txt` na nazwę pliku, do którego chcesz pisać.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Ten kod ponownie generuje wszystkie wyjątki, które mogą wystąpić podczas zapisywania tekstu do pliku. Możliwe jest zmniejszenie prawdopodobieństwa wyjątków za pomocą kontrolek Windows Forms, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i składniki [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) , które ograniczają Opcje użytkownika do prawidłowych nazw plików. Korzystanie z tych kontrolek nie jest jednak foolproof. System plików można zmienić między czasem, gdy użytkownik wybierze plik i czas wykonywania kodu. Obsługa wyjątków jest w związku z tym niemal zawsze niepotrzebna podczas pracy z plikami.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).  
  
 Ten przykład tworzy nowy plik. Jeśli aplikacja musi utworzyć plik, aplikacja musi mieć uprawnienie Tworzenie dla tego folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja wymaga tylko uprawnienia Zapis, ale ma mniejsze uprawnienia. Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie uprawnień do odczytu tylko do jednego pliku, a nie do przyznawania uprawnień do tworzenia folderów. Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder **Program Files** . Aby uzyskać więcej informacji, zobacz [Omówienie technologii list ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
