---
title: 'Porady: usuwanie plików i katalogów w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
ms.openlocfilehash: ec4de3e3a139cfcf66f1f6252c03c467f4ccfbc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707860"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Porady: usuwanie plików i katalogów w izolowanym magazynie
Katalogi i pliki można usuwać w izolowanym pliku magazynu. W magazynie nazwy plików i katalogów są zależne od systemu operacyjnego i są określone jako względem katalogu głównego wirtualnego systemu plików. W systemach operacyjnych Windows nie są one uwzględniane wielkości liter.  
  
 Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> dostarcza dwie metody usuwania katalogów i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> plików: i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. Wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException> jest zgłaszany, jeśli spróbujesz usunąć plik lub katalog, który nie istnieje. Jeśli dodasz symbol wieloznaczny w <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> nazwie, <xref:System.IO.IsolatedStorage.IsolatedStorageException> zgłasza <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> wyjątek i <xref:System.ArgumentException> zgłasza wyjątek.  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> nie powiedzie się, jeśli katalog zawiera jakiekolwiek pliki lub podkatalogi. Można użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody, aby pobrać istniejące pliki i katalogi. Aby uzyskać więcej informacji na temat przeszukiwania wirtualnego systemu plików w magazynie, zobacz [Jak: Znajdowanie istniejących plików i katalogów w izolowanym magazynie](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy, a następnie usuwa kilka katalogów i plików.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
