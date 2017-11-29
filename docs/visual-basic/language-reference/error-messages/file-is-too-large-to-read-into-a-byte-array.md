---
title: "Plik jest za duży, aby odczytać z tablicy bajtów"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bbdb5a4dcaa22ca84428ef28c8838a6d9a0ee1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Plik jest za duży, aby odczytać z tablicy bajtów
Rozmiar pliku, który próbujesz odczytu tablicy bajtów przekracza 4 GB. `My.Computer.FileSystem.ReadAllBytes` — Metoda nie może odczytać pliku, który przekracza rozmiar.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Użyj <xref:System.IO.StreamReader> do odczytu pliku. Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące programu .NET Framework We/Wy plików i systemu plików (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [Dostęp do plików za pomocą Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [Porady: Odczyt tekstu z plików za pomocą StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
