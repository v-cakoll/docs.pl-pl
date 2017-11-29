---
title: "Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c8970994f3ac4e34dfdf4af3e28100e2d009855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Porady: zapisywanie tekstu do plików w katalogu Moje dokumenty w Visual Basic
`My.Computer.FileSystem.SpecialDirectories` Obiekt umożliwia dostęp do specjalnych katalogi, takich jak **Moje dokumenty** katalogu.  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Aby zapisać nowe pliki tekstowe w katalogu Moje dokumenty  
  
1.  Użyj `My.Computer.FileSystem.SpecialDirectories.MyDocuments` właściwość, aby podać ścieżkę.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Użyj `WriteAllText` metodę zapisywanie tekstu do określonego pliku.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Zastąp `test.txt` z nazwą pliku, który chcesz zapisać.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Ten kod ponownie zgłasza wszystkie wyjątki, które mogą wystąpić podczas zapisywania do pliku tekstowego. Można zmniejszyć prawdopodobieństwo wyjątków za pomocą formantów formularzy systemu Windows, takich jak [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) i [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) składników, które ograniczyć wybór użytkownika prawidłowe nazwy. Za pomocą tych kontrolek nie jest niezawodna, jednak. System plików, można zmienić między czasem użytkownik wybierze pliku i czasu, która wykonuje kod. Obsługa wyjątków jest niemal zawsze gdy o pracy z plikami.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Jeśli używasz w kontekście częściowego zaufania, kod może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](https://msdn.microsoft.com/library/33tceax8).  
  
 W tym przykładzie tworzy nowy plik. Jeśli aplikacja musi utworzyć plik, tego aplikacja wymaga uprawnień tworzenia folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi uprawnienie, niższego poziomu uprawnień tylko do zapisu. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i przyznać uprawnienia odczytu do jednego pliku, a nie do przyznawania uprawnień tworzenia folderu. Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż do folderu głównego lub **Program Files** folderu. Aby uzyskać więcej informacji, zobacz [omówienie technologii ACL](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
