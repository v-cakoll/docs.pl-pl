---
title: Kopiowanie, usuwanie i przenoszenie plików i folderów — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712276"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)
W poniższych przykładach pokazano, jak kopiować, przenosić i usuwać pliki i foldery w sposób synchroniczny przy użyciu klas <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z przestrzeni nazw <xref:System.IO?displayProperty=nameWithType>. Te przykłady nie zapewniają paska postępu ani żadnego innego interfejsu użytkownika. Jeśli chcesz podać standardowe okno dialogowe postępu, zobacz, [jak zapewnić postęp dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType>, aby podać zdarzenia, które pozwolą obliczyć postęp podczas działania na wielu plikach. Innym podejściem jest użycie wywołania platformy w celu wywołania odpowiednich metod związanych z plikiem w powłoce systemu Windows. Aby uzyskać informacje o tym, jak wykonywać te operacje na plikach asynchronicznie, zobacz [asynchroniczne we/wy pliku](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak kopiować pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przenieść pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak usunąć pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](index.md)
- [Jak zapewnić okno dialogowe postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [We/Wy plików i strumieni](../../../standard/io/index.md)
- [Typowe zadania We/Wy](../../../standard/io/common-i-o-tasks.md)
