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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707860"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Porady: usuwanie plików i katalogów w izolowanym magazynie
Można usunąć katalogi i pliki w izolowanym pliku magazynu. W magazynie nazwy plików i katalogów są zależne od systemu operacyjnego i są określane jako względne dla katalogu głównego wirtualnego systemu plików. W systemach operacyjnych Windows nie jest rozróżniana wielkość liter.  
  
 Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> udostępnia dwie metody usuwania katalogów i plików: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. Wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException> jest generowany w przypadku próby usunięcia pliku lub katalogu, który nie istnieje. Jeśli w nazwie zostanie uwzględniony symbol wieloznaczny, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zgłasza wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException>, a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> zgłasza wyjątek <xref:System.ArgumentException>.  
  
 Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> kończy się niepowodzeniem, jeśli katalog zawiera jakiekolwiek pliki lub podkatalogi. Możesz użyć metod <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> do pobierania istniejących plików i katalogów. Aby uzyskać więcej informacji o przeszukiwaniu wirtualnego systemu plików w sklepie, zobacz [How to: find Existing Files i directorys in the izolowany magazyn](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy, a następnie usuwa kilka katalogów i plików.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
