---
title: 'Instrukcje: Kopiowania, usuwania, przenoszenia i pliki — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 498f266597032a4c35dbc8783994095b5c08fc3d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240245"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Instrukcje: Kopiowanie, usuwanie i przenoszenie plików i folderów (C# Programming Guide)
W poniższych przykładach pokazano, jak skopiować, przenieść i usunąć pliki i foldery w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klasy z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw. Te przykłady nie zapewniają pasek postępu lub innych interfejsu użytkownika. Jeśli chcesz udostępnić okno dialogowe postępu standardowego, zobacz [jak: Dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwią obliczania postępu podczas pracy w wielu plikach. Innym rozwiązaniem jest użycie platformy wywołania do wywoływania odpowiednich metod związanych z plikami w usłudze Windows Shell. Aby uzyskać informacji dotyczących sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak skopiować pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przenieść pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak usuwać pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [System plików i rejestr (C# Programming Guide)](index.md)  
- [Instrukcje: Dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
- [We/Wy plików i strumieni](../../../standard/io/index.md)  
- [Typowe zadania We/Wy](../../../standard/io/common-i-o-tasks.md)
