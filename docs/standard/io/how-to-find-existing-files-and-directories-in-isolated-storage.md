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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707136"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie

Aby wyszukać katalog w izolowanym magazynie, użyj metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>. Ta metoda pobiera ciąg, który reprezentuje wzorzec wyszukiwania. W wzorcu wyszukiwania można używać znaków wieloznacznych (?) i wieloznakowych (\*), ale symbole wieloznaczne muszą pojawić się w końcowej części nazwy. Na przykład `directory1/*ect*` jest prawidłowym ciągiem wyszukiwania, ale `*ect*/directory2` nie jest.  
  
 Aby wyszukać plik, użyj metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>. Ograniczenie symboli wieloznacznych w ciągach wyszukiwania odnoszące się do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> ma zastosowanie również do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Żadna z tych metod nie jest cykliczna; Klasa <xref:System.IO.IsolatedStorage.IsolatedStorageFile> nie dostarcza żadnych metod wyświetlania wszystkich katalogów lub plików w sklepie. Jednak metody cykliczne są wyświetlane w poniższym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie. Po pierwsze magazyn, który jest izolowany dla użytkownika, domeny i zestawu, jest pobierany i umieszczany w zmiennej `isoStore`. Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> służy do konfigurowania kilku różnych katalogów, a Konstruktor <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> tworzy niektóre pliki w tych katalogach. Kod następnie pętle przez wyniki metody `GetAllDirectories`. Ta metoda używa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> do znajdowania wszystkich nazw katalogów w bieżącym katalogu. Te nazwy są przechowywane w tablicy, a następnie `GetAllDirectories` wywołuje same, przekazując w każdy znaleziony katalog. W związku z tym wszystkie nazwy katalogów są zwracane w tablicy. Następnie kod wywołuje metodę `GetAllFiles`. Ta metoda wywołuje `GetAllDirectories`, aby znaleźć nazwy wszystkich katalogów, a następnie sprawdza każdy katalog dla plików przy użyciu metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>. Wynik jest zwracany w tablicy do wyświetlenia.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
