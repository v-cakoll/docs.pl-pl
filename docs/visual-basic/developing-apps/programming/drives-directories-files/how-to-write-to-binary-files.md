---
title: 'Instrukcje: Zapisywanie w plikach binarnych'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
ms.openlocfilehash: b36da82060b930101cb54dd852d050ac0155bd10
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411554"
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Porady: zapis w plikach binarnych w Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>Metoda zapisuje dane do pliku binarnego. Jeśli `append` parametr ma wartość `True` , dołączy dane do pliku; w przeciwnym razie dane w pliku są zastępowane.

Jeśli określona ścieżka wykluczająca nazwę pliku jest nieprawidłowa, <xref:System.IO.DirectoryNotFoundException> zostanie zgłoszony wyjątek. Jeśli ścieżka jest prawidłowa, ale plik nie istnieje, plik zostanie utworzony.

## <a name="to-write-to-a-binary-file"></a>Aby zapisać w pliku binarnym

Użyj `WriteAllBytes` metody, podając ścieżkę i nazwę pliku oraz liczbę bajtów do zapisania. Ten przykład dołącza tablicę danych `CustomerData` do pliku o nazwie `CollectedData.dat` .

[!code-vb[VbVbcnMyFileSystem#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#27)]

## <a name="robust-programming"></a>Niezawodne programowanie

Następujące warunki mogą utworzyć wyjątek:

- Ścieżka jest nieprawidłowa z jednego z następujących powodów: jest to ciąg o zerowej długości; zawiera tylko białe znaki; lub zawiera nieprawidłowe znaki. (<xref:System.ArgumentException>).

- Ścieżka jest nieprawidłowa, ponieważ jest `Nothing` ( <xref:System.ArgumentNullException> ).

- `File`wskazuje ścieżkę, która nie istnieje ( <xref:System.IO.FileNotFoundException> lub <xref:System.IO.DirectoryNotFoundException> ).

- Plik jest używany przez inny proces lub wystąpił błąd we/wy ( <xref:System.IO.IOException> ).

- Ścieżka przekracza maksymalną długość zdefiniowaną przez system ( <xref:System.IO.PathTooLongException> ).

- Nazwa pliku lub katalogu w ścieżce zawiera dwukropek (:) lub ma nieprawidłowy format ( <xref:System.NotSupportedException> ).

- Użytkownik nie ma wystarczających uprawnień do wyświetlania ścieżki ( <xref:System.Security.SecurityException> ).

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Instrukcje: Zapisywanie tekstu w plikach](how-to-write-text-to-files.md)
