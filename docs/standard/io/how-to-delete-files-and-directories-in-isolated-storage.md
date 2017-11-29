---
title: "Porady: usuwanie plików i katalogów w izolowanym magazynie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a>Porady: usuwanie plików i katalogów w izolowanym magazynie
Można usunąć katalogów i plików znajdujących się w pliku izolowanego magazynu. W sklepie nazw plików i katalogów są zależne od systemu operacyjnego i są określone jako względem katalogu głównego wirtualnego systemu plików. Nie są one z uwzględnieniem wielkości liter w systemach operacyjnych Windows.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Klasa zapewnia dwie metody usuwania plików i katalogów: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>. <xref:System.IO.IsolatedStorage.IsolatedStorageException> Wyjątek przy próbie usunięcia pliku lub katalogu, który nie istnieje. Jeśli dołączysz symbolu wieloznacznego w nazwie, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zgłasza <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> zgłasza <xref:System.ArgumentException> wyjątku.  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metody zakończy się niepowodzeniem, jeśli katalog zawiera wszystkie pliki i podkatalogi. Można użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> i <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody do pobierania istniejących plików i katalogów. Aby uzyskać więcej informacji na temat wyszukiwanie w wirtualnym systemie plików magazynu, zobacz [porady: znajdowanie istniejących plików i katalogów w izolowanym magazynie](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy, a następnie usuwa kilka plików i katalogów.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [Izolowany Magazyn](../../../docs/standard/io/isolated-storage.md)
