---
title: 'Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 5debb2cbfa5ada45447e280169b9fe66d1a15a53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Porady: kopiowanie, usuwanie i przenoszenie plików i folderów (Przewodnik programowania w języku C#)
Poniższe przykłady pokazują, jak kopiowanie, przenoszenie i usuwanie plików i folderów w sposób synchronicznego przy użyciu <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, i <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> klas z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw. Poniższe przykłady nie zawierają pasek postępu lub inny interfejs użytkownika. Jeśli chcesz podać okno dialogowe postępu standardowego, zobacz [porady: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Użyj <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zapewnienie zdarzenia, które umożliwi obliczyć postęp działającego w wielu plików. Innym rozwiązaniem jest użycie platformy wywołania do wywołania odpowiednich metod związany z plikami w powłoce systemu Windows. Aby uzyskać informacje dotyczące sposobu wykonywania tych operacji na plikach asynchronicznie, zobacz [asynchroniczne We/Wy pliku](https://msdn.microsoft.com/library/kztecsys).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób kopiowania plików i katalogów.  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób przenoszenia plików i katalogów.  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób usuwania plików i katalogów.  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](index.md)  
 [Instrukcje: dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [We/Wy plików i strumieni](https://msdn.microsoft.com/library/k3352a4t)  
 [Typowe zadania We/Wy](https://msdn.microsoft.com/library/ms404278)
