---
title: Plik jest za duży, aby odczytać z tablicy bajtów
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: b81fc9332d5f1347404fcdd73bce72b6b09778b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363127"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Plik jest za duży, aby odczytać z tablicy bajtów
Rozmiar pliku, który próbujesz odczytać do tablicy bajtów, przekracza 4 GB. `My.Computer.FileSystem.ReadAllBytes`Metoda nie może odczytać pliku, który przekracza ten rozmiar.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Użyj <xref:System.IO.StreamReader> pliku, aby odczytać plik. Aby uzyskać więcej informacji, zobacz podstawowe informacje na temat operacji [we/wy pliku .NET Framework i systemu plików (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Dostęp do plików za pomocą Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
- [Instrukcje: Odczyt tekstu z plików za pomocą StreamReader](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
