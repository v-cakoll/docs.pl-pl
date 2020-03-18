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
ms.openlocfilehash: dfebcc9acf0b699f898c106921d15ce0294bc5d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707136"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie

Aby wyszukać katalog w izolowanym <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> magazynie, użyj tej metody. Ta metoda przyjmuje ciąg, który reprezentuje wzorzec wyszukiwania. We wzorcu wyszukiwania można używać zarówno jednoznakowych (?), jak i wieloznakowych (\*) symboli wieloznacznych, ale symbole wieloznaczne muszą pojawić się w końcowej części nazwy. Na przykład `directory1/*ect*` jest prawidłowyciąg `*ect*/directory2` wyszukiwania, ale nie jest.  
  
 Aby wyszukać plik, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> użyj tej metody. Ograniczenie dla znaków wieloznacznych w ciągach <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> wyszukiwania, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>które mają zastosowanie również do .  
  
 Żadna z tych metod nie jest rekurencyjne; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> klasa nie dostarcza żadnych metod wyświetlania wszystkich katalogów lub plików w sklepie. Jednak metody cykliczne są wyświetlane w poniższym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono sposób tworzenia plików i katalogów w izolowanym magazynie. Po pierwsze magazyn, który jest izolowany dla użytkownika, domeny `isoStore` i zestawu jest pobierana i umieszczana w zmiennej. Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> jest używana do konfigurowania kilku różnych <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> katalogów, a konstruktor tworzy niektóre pliki w tych katalogach. Kod następnie pętli za pośrednictwem `GetAllDirectories` wyników metody. Ta metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> służy do znajdowania wszystkich nazw katalogów w bieżącym katalogu. Nazwy te są przechowywane w `GetAllDirectories` tablicy, a następnie wywołuje się, przekazując w każdym katalogu, który znalazł. W rezultacie wszystkie nazwy katalogów są zwracane w tablicy. Następnie kod wywołuje `GetAllFiles` metodę. Ta metoda `GetAllDirectories` wywołuje, aby dowiedzieć się nazwy wszystkich katalogów, a następnie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> sprawdza każdy katalog dla plików przy użyciu metody. Wynik jest zwracany w tablicy do wyświetlenia.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
