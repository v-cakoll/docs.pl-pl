---
title: 'Porady: zapis w plikach binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: 72d019f5f49868bd84d0507535e8ebc547b50e25
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334428"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Porady: zapis w plikach binarnych w Visual Basic

The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file. If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.

If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown. If the path is valid but the file does not exist, the file will be created.

## <a name="to-write-to-a-binary-file"></a>To write to a binary file

Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written. This example appends the data array `CustomerData` to the file named `CollectedData.dat`.

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Niezawodne programowanie

The following conditions may create an exception:

- The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters. (<xref:System.ArgumentException>).

- The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).

- `File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).

- The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).

- The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).

- A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).

- The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Instrukcje: zapisywanie tekstu w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
