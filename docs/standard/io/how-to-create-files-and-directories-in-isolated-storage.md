---
title: 'Porady: tworzenie plików i katalogów w izolowanym magazynie'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
ms.openlocfilehash: 83e8c800dc74d9689f1bfdb506a6b454e87b36ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707873"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Porady: tworzenie plików i katalogów w izolowanym magazynie
Po uzyskaniu izolowanego magazynu można utworzyć katalogi i pliki do przechowywania danych. W magazynie nazwy plików i katalogów są określone w odniesieniu do katalogu głównego wirtualnego systemu plików.  
  
 Aby utworzyć katalog, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> należy użyć metody wystąpienia. Jeśli określisz podkatalog katalogu, który nie istnieje, zostaną utworzone oba katalogi. Jeśli określisz katalog, który już istnieje, metoda zwraca bez tworzenia katalogu i nie jest zgłaszany żaden wyjątek. Jeśli jednak określisz nazwę katalogu zawierającą <xref:System.IO.IsolatedStorage.IsolatedStorageException> nieprawidłowe znaki, zostanie zgłoszony wyjątek.  
  
 Aby utworzyć plik, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> użyj tej metody.  
  
 W systemie operacyjnym Windows izolowane nazwy plików magazynu i katalogów są niewrażliwe. Oznacza to, że jeśli `ThisFile.txt`utworzysz plik `THISFILE.TXT`o nazwie , a następnie utworzysz inny plik o nazwie , zostanie utworzony tylko jeden plik. Nazwa pliku zachowuje oryginalną obudowę do celów wyświetlania.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono sposób tworzenia plików i katalogów w izolowanym magazynie.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Izolowany magazyn](../../../docs/standard/io/isolated-storage.md)
