---
title: 'Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: dd32798062dbfc9a10acd27ce51d8d5dd3b164f6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590091"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Przewodnik programowania)
W poniższych przykładach pokazano, jak kopiować, przenosić i usuwać <xref:System.IO.File?displayProperty=nameWithType>pliki i foldery w sposób synchroniczny przy użyciu klas <xref:System.IO.FileInfo?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw. Te przykłady nie zapewniają paska postępu ani żadnego innego interfejsu użytkownika. Jeśli chcesz podać standardowe okno dialogowe postępu, zobacz [How to: Udostępnianie okna dialogowego postępu dla operacji](how-to-provide-a-progress-dialog-box-for-file-operations.md)na plikach.  
  
 Służy <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> do dostarczania zdarzeń, które umożliwią obliczenie postępu podczas działania na wielu plikach. Innym podejściem jest użycie wywołania platformy w celu wywołania odpowiednich metod związanych z plikiem w powłoce systemu Windows. Aby uzyskać informacje o tym, jak wykonywać te operacje na plikach asynchronicznie, zobacz [asynchroniczne we/wy pliku](../../../standard/io/asynchronous-file-i-o.md).  
  
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
- [Instrukcje: Udostępnianie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [We/Wy plików i strumieni](../../../standard/io/index.md)
- [Typowe zadania We/Wy](../../../standard/io/common-i-o-tasks.md)
