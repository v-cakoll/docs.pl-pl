---
title: "Porady: pobieranie informacji o plikach, folderach i dyskach (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5652dda53a0192ce39be497b6e8ad3c97bef042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Porady: pobieranie informacji o plikach, folderach i dyskach (Przewodnik programowania w języku C#)
W programie .NET Framework aby dostęp do informacji o systemie plików przy użyciu następujących klas:  
  
-   <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
-   <xref:System.IO.Directory?displayProperty=nameWithType>  
  
-   <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> klasy reprezentują pliku lub katalogu i zawierają właściwości, które udostępniają wiele atrybutów plików, które są obsługiwane przez system plików NTFS. Zawierają one również metody do otwierania, zamykania, przenoszenie i usuwanie plików i folderów. Można utworzyć wystąpieniami tych klas przez przekazanie ciąg reprezentujący nazwę pliku, folderu lub dysku w Konstruktorze:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Możesz również uzyskać nazwy plików, folderów lub stacji dysków przy użyciu wywołania <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>, i <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 <xref:System.IO.Directory?displayProperty=nameWithType> i <xref:System.IO.File?displayProperty=nameWithType> klasy Podaj metody statyczne do pobierania informacji o katalogów i plików.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia różne sposoby dostęp do informacji dotyczących plików i folderów.  
  
 [!code-csharp[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W przypadku przetwarzania ciągów ścieżka określona przez użytkownika również powinna obsługiwać wyjątki dla następujących warunków:  
  
-   Nazwa pliku jest nieprawidłowo sformułowany. Na przykład zawiera nieprawidłowe znaki lub białych znaków.  
  
-   Nazwa pliku ma wartość null.  
  
-   Nazwa pliku jest dłuższa niż zdefiniowana w systemie długość maksymalna.  
  
-   Nazwa pliku zawiera dwukropek (:).  
  
 Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku `Exists` metoda zwraca `false` niezależnie od tego, czy ścieżka istnieje; metoda zgłosiła wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)
