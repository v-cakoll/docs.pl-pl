---
title: 'Instrukcje: Usuwanie plików i katalogów w izolowanym magazynie'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797179"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Instrukcje: Usuwanie plików i katalogów w izolowanym magazynie
Można usunąć katalogów i plików w pliku wydzielonej pamięci masowej. W magazynie i nazw plików i katalogów jest zależna od systemu operacyjnego i są określane względem katalogu głównego w wirtualnym systemie plików. Nie są one wielkość liter w systemach operacyjnych Windows.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Klasa zapewnia dwie metody usuwania plików i katalogów: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. <xref:System.IO.IsolatedStorage.IsolatedStorageException> Wyjątek jest generowany, jeśli zostanie podjęta próba usunięcia pliku lub katalogu, który nie istnieje. Jeśli dołączysz symbolu wieloznacznego w nazwie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zgłasza <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątek, i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> zgłasza <xref:System.ArgumentException> wyjątku.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metoda kończy się niepowodzeniem, jeśli katalog zawiera wszystkie pliki i podkatalogi. Możesz użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody pobierania istniejących plików i katalogów. Aby uzyskać więcej informacji na temat wyszukiwania w wirtualnym systemie plików magazynu, zobacz [jak: Wyszukiwanie istniejących plików i katalogów w wydzielonej pamięci masowej](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy i usuwa kilka plików i katalogów.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
