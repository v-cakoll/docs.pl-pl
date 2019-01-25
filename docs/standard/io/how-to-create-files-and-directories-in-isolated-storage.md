---
title: 'Instrukcje: Tworzenie plików i katalogów w wydzielonej pamięci masowej'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92f4b686a5a2bdc74ff3f0f68de4c6b2048da5a1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709016"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Instrukcje: Tworzenie plików i katalogów w wydzielonej pamięci masowej
Po uzyskaniu izolowanym magazynie, można utworzyć katalogów i plików do przechowywania danych. W magazynie i nazw plików i katalogów są określane względem katalogu głównego w wirtualnym systemie plików.  
  
 Aby utworzyć katalog, należy użyć <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodę wystąpienia. Jeśli określisz podkatalogiem katalogu, który nie istnieje, oba katalogi są tworzone. Jeśli określisz katalogu, który już istnieje, metoda zwraca bez tworzenia katalogu, a jest zgłaszany żaden wyjątek. Jednakże, jeśli określisz nazwę katalogu, zawiera nieprawidłowe znaki <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku.  
  
 Aby utworzyć plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.  
  
 W systemie operacyjnym Windows, wydzielona pamięć masowa plików i katalogów nazw jest rozróżniana wielkość liter. Oznacza to jeśli utworzysz plik o nazwie `ThisFile.txt`, a następnie utwórz inny plik o nazwie `THISFILE.TXT`, jest tworzony tylko jeden plik. Nazwa pliku przechowuje swoje oryginalne wielkość liter w wyrazie w celach wyświetlania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia plików i katalogów w izolowanym magazynie.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
