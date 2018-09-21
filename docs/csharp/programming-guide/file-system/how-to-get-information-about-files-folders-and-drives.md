---
title: 'Porady: pobieranie informacji o plikach, folderach i dyskach (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 8ebacff0f3a1704ec001e3570d0df136f54baf9d
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529184"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Porady: pobieranie informacji o plikach, folderach i dyskach (Przewodnik programowania w języku C#)
W .NET Framework uzyskujesz dostęp do informacji o systemie plików, przy użyciu następujących klas:  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> klasy reprezentują pliku lub katalogu, a także zawierają właściwości, które udostępniają wiele atrybutów plików, które są obsługiwane przez system plików NTFS. Zawierają one również metody do otwierania, zamykanie, przenoszenie i usuwanie plików i folderów. Można utworzyć wystąpień tych klas, przekazując ciąg reprezentujący nazwę pliku, folderu lub dysku w Konstruktorze:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Możesz również uzyskać nazwy plików, folderów lub dyski za pomocą wywołania <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, i <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> i <xref:System.IO.File?displayProperty=nameWithType> klasy zapewniają statyczne metody do pobierania informacji na temat plików i katalogów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje różne sposoby, aby uzyskać dostęp do informacji o plikach i folderach.  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Przetwarzanie ciągami ścieżki określonych przez użytkownika, należy również obsługiwać wyjątki dla następujących warunków:  
  
-   Nazwa pliku jest nieprawidłowo sformułowany. Na przykład zawiera nieprawidłowe znaki lub białych znaków.  
  
-   Nazwa pliku ma wartość null.  
  
-   Nazwa pliku jest większa niż zdefiniowana w systemie długość maksymalna.  
  
-   Nazwa pliku zawiera dwukropek (:).  
  
 Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku `Exists` metoda zwraca `false` niezależnie od tego, czy ścieżka istnieje; metody nie zgłasza wyjątku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
