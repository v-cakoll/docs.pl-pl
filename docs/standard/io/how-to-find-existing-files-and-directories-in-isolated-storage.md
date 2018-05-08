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
ms.openlocfilehash: 866be7970c43051dd7e2bf8d45ae779aca130a45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie
Aby wyszukać katalog w magazynie izolowanym, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metody. Ta metoda przyjmuje ciąg, który reprezentuje wzorzec wyszukiwania. Można użyć zarówno jednoznakowym (?) i wielu znaków (*) znaki symboli wieloznacznych we wzorcu wyszukiwania, ale symboli wieloznacznych musi występować w końcowa część nazwy. Na przykład `directory1/*ect*` jest prawidłowy ciąg wyszukiwania, ale `*ect*/directory2` nie jest.  
  
 Aby wyszukać plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metody. Ograniczenie dla symbole wieloznaczne w ciągach wyszukiwania, których dotyczy <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> dotyczą również <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Żadna z tych metod jest rekursywny; <xref:System.IO.IsolatedStorage.IsolatedStorageFile> klasa nie dostarcza żadnych metod do wyświetlania listy wszystkich katalogów lub plików w magazynie. Jednak rekursywny metod przedstawiono w poniższym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie. Najpierw należy pobrać i umieszczane w sklepu, która jest odizolowana dla użytkownika, domena i zestawu `isoStore` zmiennej. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda jest używana do konfigurowania kilku różnych katalogach i <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> Konstruktor tworzy niektóre pliki w tych katalogach. Kod następnie pętli wyniki `GetAllDirectories` metody. Ta metoda używa <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> można znaleźć nazwy katalogów w bieżącym katalogu. Te nazwy są przechowywane w tablicy, a następnie `GetAllDirectories` wywołuje, przekazując każdego katalogu znaleziono. W związku z tym zwracane są wszystkie nazwy katalogów w tablicy. Następnie kod wywołuje `GetAllFiles` metody. Ta metoda wywołuje `GetAllDirectories` Aby dowiedzieć się, nazwy wszystkich katalogów, a następnie sprawdza każdy katalog dla plików przy użyciu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody. Wynik jest zwracany w tablicy do wyświetlenia.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
