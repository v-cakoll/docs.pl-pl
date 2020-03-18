---
title: Jak kopiować, usuwać i przenosić pliki i foldery - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712276"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Jak kopiować, usuwać i przenosić pliki i foldery (Przewodnik po programowaniu języka C#)
W poniższych przykładach przedstawiono sposób kopiowania, przenoszenia i usuwania plików <xref:System.IO.File?displayProperty=nameWithType>i <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.FileInfo?displayProperty=nameWithType>folderów <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> w <xref:System.IO?displayProperty=nameWithType> sposób synchroniczny przy użyciu programu , , i klas z obszaru nazw. Te przykłady nie zapewniają paska postępu ani żadnego innego interfejsu użytkownika. Jeśli chcesz podać standardowe okno dialogowe postępu, zobacz [Jak udostępnić okno dialogowe postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Służy <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> do dostarczania zdarzeń, które umożliwią obliczenie postępu podczas pracy na wielu plikach. Innym podejściem jest użycie wywołania platformy do wywołania odpowiednich metod związanych z plikami w powłoce systemu Windows. Aby uzyskać informacje dotyczące asynchronicznego wykonywania tych operacji plików, zobacz [Asynchroniczne we/wy pliku](../../../standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak kopiować pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak przenosić pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak usunąć pliki i katalogi.  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](index.md)
- [Dostarczanie okna dialogowego postępu dla operacji na plikach](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [We/Wy plików i strumieni](../../../standard/io/index.md)
- [Typowe zadania We/Wy](../../../standard/io/common-i-o-tasks.md)
