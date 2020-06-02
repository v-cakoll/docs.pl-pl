---
title: 'Instrukcje: Wyszukiwanie istniejących plików i katalogów w izolowanym magazynie'
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
ms.openlocfilehash: ec1d1fbdefdad3ec0dd2c07fbc1278e4d1d217c6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291854"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Instrukcje: Wyszukiwanie istniejących plików i katalogów w izolowanym magazynie

Aby wyszukać katalog w izolowanym magazynie, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metody. Ta metoda pobiera ciąg, który reprezentuje wzorzec wyszukiwania. W wzorcu wyszukiwania można używać znaków wieloznacznych (?) i wieloznakowych ( \* ), ale symbole wieloznaczne muszą pojawić się w końcowej części nazwy. Na przykład, `directory1/*ect*` jest prawidłowym ciągiem wyszukiwania, ale `*ect*/directory2` nie jest.  
  
 Aby wyszukać plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metody. Ograniczenie symboli wieloznacznych w ciągach wyszukiwania, które mają zastosowanie <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> również do <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> .  
  
 Żadna z tych metod nie jest cykliczna; <xref:System.IO.IsolatedStorage.IsolatedStorageFile>Klasa nie dostarcza żadnych metod wyświetlania wszystkich katalogów lub plików w sklepie. Jednak metody cykliczne są wyświetlane w poniższym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie. Po pierwsze magazyn, który jest izolowany dla użytkownika, domeny i zestawu, jest pobierany i umieszczany w `isoStore` zmiennej. Ta <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda służy do konfigurowania kilku różnych katalogów, a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Konstruktor tworzy niektóre pliki w tych katalogach. Kod następnie pętle przez wyniki `GetAllDirectories` metody. Ta metoda używa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> do znajdowania wszystkich nazw katalogów w bieżącym katalogu. Te nazwy są przechowywane w tablicy, a następnie `GetAllDirectories` wywołują się do siebie, przekazując w każdy znaleziony katalog. W związku z tym wszystkie nazwy katalogów są zwracane w tablicy. Następnie kod wywołuje `GetAllFiles` metodę. Ta metoda wywołuje `GetAllDirectories` wszystkie nazwy katalogów, a następnie sprawdza każdy katalog dla plików przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody. Wynik jest zwracany w tablicy do wyświetlenia.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Magazyn izolowany](isolated-storage.md)
