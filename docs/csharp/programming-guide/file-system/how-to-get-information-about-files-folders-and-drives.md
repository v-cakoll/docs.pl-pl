---
title: Jak uzyskać informacje o plikach, folderach i dyskach — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 6024b1be4ce826900c6f9b367323fb19ac55d2c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705213"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Jak uzyskać informacje o plikach, folderach i dyskach (C# Przewodnik programowania)
W .NET Framework można uzyskać dostęp do informacji o systemie plików przy użyciu następujących klas:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 Klasy <xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> reprezentują plik lub katalog i zawierają właściwości, które uwidaczniają wiele atrybutów plików obsługiwanych przez system plików NTFS. Zawierają również metody otwierania, zamykania, przechodzenia i usuwania plików i folderów. Wystąpienia tych klas można utworzyć, przekazując ciąg, który reprezentuje nazwę pliku, folderu lub dysku w konstruktorze:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Możesz również uzyskać nazwy plików, folderów lub dysków, korzystając z wywołań do <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType>i <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType>.  
  
 Klasy <xref:System.IO.Directory?displayProperty=nameWithType> i <xref:System.IO.File?displayProperty=nameWithType> zapewniają metody statyczne do pobierania informacji o katalogach i plikach.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne sposoby uzyskiwania dostępu do informacji o plikach i folderach.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Podczas przetwarzania ciągów ścieżki określonych przez użytkownika należy również obsługiwać wyjątki dla następujących warunków:  
  
- Nazwa pliku jest źle sformułowana. Na przykład zawiera nieprawidłowe znaki lub tylko odstęp.  
  
- Nazwa pliku ma wartość null.  
  
- Nazwa pliku jest dłuższa niż zdefiniowana w systemie długość maksymalna.  
  
- Nazwa pliku zawiera dwukropek (:).  
  
 Jeśli aplikacja nie ma wystarczających uprawnień do odczytu określonego pliku, Metoda `Exists` zwraca `false` niezależnie od tego, czy ścieżka istnieje; Metoda nie zgłasza wyjątku.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
