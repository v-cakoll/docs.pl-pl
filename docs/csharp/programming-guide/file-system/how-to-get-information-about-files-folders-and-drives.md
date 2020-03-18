---
title: Jak uzyskać informacje o plikach, folderach i dyskach - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705213"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Jak uzyskać informacje o plikach, folderach i dyskach (Przewodnik po programowaniu języka C#)
W programie .NET Framework można uzyskać dostęp do informacji o systemie plików przy użyciu następujących klas:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 I <xref:System.IO.FileInfo> <xref:System.IO.DirectoryInfo> klasy reprezentują plik lub katalog i zawierają właściwości, które udostępniają wiele atrybutów plików, które są obsługiwane przez system plików NTFS. Zawierają one również metody otwierania, zamykania, przenoszenia i usuwania plików i folderów. Wystąpienia tych klas można utworzyć, przekazując do konstruktora ciąg reprezentujący nazwę pliku, folderu lub dysku:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Można również uzyskać nazwy plików, folderów lub dysków <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>za <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>pomocą połączeń do , i .  
  
 I <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.File?displayProperty=nameWithType> klasy zapewniają statyczne metody pobierania informacji o katalogach i plikach.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne sposoby uzyskiwania dostępu do informacji o plikach i folderach.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Podczas przetwarzania ciągów ścieżek określonych przez użytkownika należy również obsługiwać wyjątki dla następujących warunków:  
  
- Nazwa pliku jest nieprawidłowo sformułowana. Na przykład zawiera nieprawidłowe znaki lub tylko biały znak.  
  
- Nazwa pliku ma wartość null.  
  
- Nazwa pliku jest dłuższa niż maksymalna długość zdefiniowana przez system.  
  
- Nazwa pliku zawiera dwukropek (:).  
  
 Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku, `Exists` metoda zwraca `false` niezależnie od tego, czy istnieje ścieżka; metoda nie zgłasza wyjątku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
