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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707873"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Porady: tworzenie plików i katalogów w izolowanym magazynie
Po uzyskaniu izolowanego magazynu można utworzyć katalogi i pliki do przechowywania danych. W magazynie nazwy plików i katalogów są określone w odniesieniu do katalogu głównego wirtualnego systemu plików.  
  
 Aby utworzyć katalog, użyj metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance. W przypadku określenia podkatalogu katalogu, który nie istnieje, tworzone są oba katalogi. Jeśli określisz katalog, który już istnieje, metoda zwraca bez tworzenia katalogu i nie zgłasza wyjątku. Jednak w przypadku określenia nazwy katalogu, która zawiera nieprawidłowe znaki, zostanie zgłoszony wyjątek <xref:System.IO.IsolatedStorage.IsolatedStorageException>.  
  
 Aby utworzyć plik, użyj metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType>.  
  
 W systemie operacyjnym Windows, izolowany plik magazynu i nazwy katalogów nie uwzględnia wielkości liter. Oznacza to, że w przypadku utworzenia pliku o nazwie `ThisFile.txt`, a następnie utworzenia innego pliku o nazwie `THISFILE.TXT`zostanie utworzony tylko jeden plik. Nazwa pliku zachowuje pierwotną wielkość liter na potrzeby wyświetlania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
