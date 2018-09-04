---
title: 'Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: ea7e23f03f4321644eb2484b3965a0de3f180c47
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504538"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)
W poniższych przykładach pokazano, jak skopiować, przenieść i usunąć pliki i foldery w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klasy z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw. Te przykłady nie zapewniają pasek postępu lub innych interfejsu użytkownika. Jeśli chcesz udostępnić okno dialogowe postępu standardowego, zobacz [porady: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwią obliczania postępu podczas pracy w wielu plikach. Innym rozwiązaniem jest użycie platformy wywołania do wywoływania odpowiednich metod związanych z plikami w usłudze Windows Shell. Aby uzyskać informacji dotyczących sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy](https://msdn.microsoft.com/library/kztecsys).  
  
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
- [Instrukcje: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
- [We/Wy plików i strumieni](https://msdn.microsoft.com/library/k3352a4t)  
- [Typowe zadania We/Wy](https://msdn.microsoft.com/library/ms404278)
