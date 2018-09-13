---
title: 'Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09c112374458b70a464291e898e9a880c8679773
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705868"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie
Aby wyszukać katalogu w wydzielonej pamięci masowej, należy użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metody. Ta metoda przyjmuje ciąg, który reprezentuje wzorzec wyszukiwania. Można użyć zarówno pojedynczych znaków (?), jak i wielu znaków (*) znaki symboli wieloznacznych w wzorzec wyszukiwania, ale znaki symboli wieloznacznych, musi znajdować się w końcowej części nazwy. Na przykład `directory1/*ect*` jest prawidłowy ciąg wyszukiwania, ale `*ect*/directory2` nie jest.  
  
 Aby wyszukać plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metody. Ograniczenie dla symboli wieloznacznych w ciągów wyszukiwania, których dotyczy <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> dotyczy także <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Żadna z tych metod jest cykliczna; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> klasy nie dostarcza żadnych metod do wyświetlania listy wszystkich katalogów lub plików w magazynie. Jednak cyklicznego metod przedstawiono w poniższym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia plików i katalogów w izolowanym magazynie. Najpierw pobrać i umieszczane w magazynie, która jest odizolowana dla użytkownika, domeny i zestawu `isoStore` zmiennej. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda służy do konfigurowania kilkoma różnymi katalogami i <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Konstruktor tworzy kilka plików w katalogach. Kod następnie przetwarza w pętli wyniki `GetAllDirectories` metody. Ta metoda używa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> można znaleźć nazwy katalogów w bieżącym katalogu. Te nazwy są przechowywane w tablicy, a następnie `GetAllDirectories` wywołuje sam siebie, przekazując każdy katalog odnalezieniu. W rezultacie wszystkie nazwy katalogów są zwracane w tablicy. Następnie kod wywołuje `GetAllFiles` metody. Ta metoda wywołuje `GetAllDirectories` Aby dowiedzieć się, nazwy wszystkich katalogów, a następnie sprawdza każdy katalog dla plików przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody. Wynik jest zwracany w tablicy, do wyświetlenia.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
