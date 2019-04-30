---
title: 'Instrukcje: Kopiowania, usuwania, przenoszenia i pliki — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 609e14141538543c9318efbd4899ec16967cc23f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710748"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Programming Guide)
W poniższych przykładach pokazano, jak skopiować, przenieść i usunąć pliki i foldery w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klasy z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw. Te przykłady nie zapewniają pasek postępu lub innych interfejsu użytkownika. Jeśli chcesz udostępnić okno dialogowe postępu standardowego, zobacz [jak: Dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwią obliczania postępu podczas pracy w wielu plikach. Innym rozwiązaniem jest użycie platformy wywołania do wywoływania odpowiednich metod związanych z plikami w usłudze Windows Shell. Aby uzyskać informacji dotyczących sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skopiować pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przenieść pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak usuwać pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [System plików i rejestr (C# Programming Guide)](index.md)
- [Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [We/Wy plików i strumieni](../../../standard/io/index.md)
- [Typowe zadania We/Wy](../../../standard/io/common-i-o-tasks.md)
