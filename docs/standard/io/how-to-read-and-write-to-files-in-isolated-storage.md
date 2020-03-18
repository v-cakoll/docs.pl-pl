---
title: 'Porady: odczyt i zapis w plikach w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
ms.openlocfilehash: a1ea65b0b8280faf51595b2fe9edcbf17eaabd8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706689"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Porady: odczyt i zapis w plikach w izolowanym magazynie
Aby odczytać lub zapisać plik w izolowanym magazynie, użyj obiektu <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> <xref:System.IO.StreamReader> z czytnikiem strumienia (obiekt) lub modułem zapisu strumienia (obiekt).<xref:System.IO.StreamWriter>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu uzyskuje izolowany magazyn i sprawdza, czy plik o nazwie TestStore.txt istnieje w magazynie. Jeśli nie istnieje, tworzy plik i zapisuje "Hello Isolated Storage" do pliku. Jeśli TestStore.txt już istnieje, przykładowy kod odczytuje z pliku.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
