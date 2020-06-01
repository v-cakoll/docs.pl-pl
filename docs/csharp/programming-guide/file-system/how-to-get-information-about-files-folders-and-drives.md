---
title: Jak uzyskać informacje o plikach, folderach i dyskach — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 32aced17634a1406e2fce0af9c2a92f7a5eb9b40
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241620"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Jak uzyskać informacje o plikach, folderach i dyskach (Przewodnik programowania w języku C#)
W programie .NET można uzyskać dostęp do informacji o systemie plików przy użyciu następujących klas:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 <xref:System.IO.FileInfo>Klasy i <xref:System.IO.DirectoryInfo> reprezentują plik lub katalog i zawierają właściwości, które uwidaczniają wiele atrybutów plików, które są obsługiwane przez system plików NTFS. Zawierają również metody otwierania, zamykania, przechodzenia i usuwania plików i folderów. Wystąpienia tych klas można utworzyć, przekazując ciąg, który reprezentuje nazwę pliku, folderu lub dysku w konstruktorze:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Można również uzyskać nazwy plików, folderów lub dysków przy użyciu wywołań do <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType> , <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> i <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> .  
  
 <xref:System.IO.Directory?displayProperty=nameWithType>Klasy i <xref:System.IO.File?displayProperty=nameWithType> zapewniają statyczne metody pobierania informacji o katalogach i plikach.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne sposoby uzyskiwania dostępu do informacji o plikach i folderach.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Podczas przetwarzania ciągów ścieżki określonych przez użytkownika należy również obsługiwać wyjątki dla następujących warunków:  
  
- Nazwa pliku jest źle sformułowana. Na przykład zawiera nieprawidłowe znaki lub tylko odstęp.  
  
- Nazwa pliku ma wartość null.  
  
- Nazwa pliku jest dłuższa niż zdefiniowana w systemie długość maksymalna.  
  
- Nazwa pliku zawiera dwukropek (:).  
  
 Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku, `Exists` Metoda zwraca `false` bez względu na to, czy ścieżka istnieje; metoda nie zgłasza wyjątku.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
