---
title: Plik jest za duży, aby odczytać z tablicy bajtów
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831517"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Plik jest za duży, aby odczytać z tablicy bajtów
Rozmiar pliku, który chcesz odczytać do tablicy typu byte przekracza 4 GB. `My.Computer.FileSystem.ReadAllBytes` Metody nie można odczytać pliku, który przekroczy rozmiar.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj <xref:System.IO.StreamReader> można odczytać pliku. Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące programu .NET Framework We/Wy i System plików (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [Instrukcje: Odczytywanie tekstu z plików za pomocą StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
