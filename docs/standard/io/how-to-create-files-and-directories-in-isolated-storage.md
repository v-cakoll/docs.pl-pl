---
title: 'Instrukcje: Tworzenie plików i katalogów w izolowanym magazynie'
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
ms.openlocfilehash: d5e086e77ab6309fa0757ef32b620e0fdbc1f627
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413044"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Instrukcje: Tworzenie plików i katalogów w izolowanym magazynie
Po uzyskaniu izolowanego magazynu można utworzyć katalogi i pliki do przechowywania danych. W magazynie nazwy plików i katalogów są określone w odniesieniu do katalogu głównego wirtualnego systemu plików.  
  
 Aby utworzyć katalog, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metody Instance. W przypadku określenia podkatalogu katalogu, który nie istnieje, tworzone są oba katalogi. Jeśli określisz katalog, który już istnieje, metoda zwraca bez tworzenia katalogu i nie zgłasza wyjątku. Jednak w przypadku określenia nazwy katalogu, która zawiera nieprawidłowe znaki, <xref:System.IO.IsolatedStorage.IsolatedStorageException> zostanie zgłoszony wyjątek.  
  
 Aby utworzyć plik, należy użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.  
  
 W systemie operacyjnym Windows, izolowany plik magazynu i nazwy katalogów nie uwzględnia wielkości liter. Oznacza to, że jeśli utworzysz plik o nazwie `ThisFile.txt` , a następnie utworzysz inny plik o nazwie `THISFILE.TXT` , zostanie utworzony tylko jeden plik. Nazwa pliku zachowuje pierwotną wielkość liter na potrzeby wyświetlania.  

 Utworzenie pliku magazynu izolowanego spowoduje zgłoszenie, <xref:System.IO.IsolatedStorage.IsolatedStorageException> czy ścieżka zawiera katalog, który nie istnieje.
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Magazyn izolowany](isolated-storage.md)
