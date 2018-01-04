---
title: "Porady: tworzenie plików i katalogów w izolowanym magazynie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cf6295e7d58d03e7b4bf4e0a00cfc509d289e071
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Porady: tworzenie plików i katalogów w izolowanym magazynie
Po uzyskaniu izolowanego magazynu można utworzyć katalogów i plików do przechowywania danych. W sklepie nazwy plików i katalogów są określane względem katalogu głównego wirtualnego systemu plików.  
  
 Aby utworzyć katalog, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metody wystąpienia. Jeśli określisz podkatalogiem katalogu, który nie istnieje, obie katalogi są tworzone. Jeśli określisz katalogu, który już istnieje, metoda zwraca bez tworzenia katalogu, a nie wyjątek. Jednak jeśli określono nazwę katalogu zawiera nieprawidłowe znaki <xref:System.IO.IsolatedStorage.IsolatedStorageException> wyjątku.  
  
 Aby utworzyć plik, użyj <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.  
  
 W systemie operacyjnym Windows, izolowanego magazynu plików i katalogów nazwy jest rozróżniana wielkość liter. Oznacza to czy utworzony plik o nazwie `ThisFile.txt`, a następnie utwórz plik o nazwie `THISFILE.TXT`, tworzony jest tylko jeden plik. Nazwa pliku zachowuje jego oryginalnej wielkości liter podczas wyświetlania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod ilustruje sposób tworzenia plików i katalogów w izolowanym magazynie.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)
