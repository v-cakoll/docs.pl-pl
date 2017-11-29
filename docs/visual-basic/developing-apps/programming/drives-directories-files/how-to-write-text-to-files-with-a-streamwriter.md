---
title: "Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic
W tym przykładzie otwiera <xref:System.IO.StreamWriter> obiekt z `My.Computer.FileSystem.OpenTextFileWriter` — metoda i używa go do zapisu do pliku tekstowego z ciągiem <xref:System.IO.TextWriter.WriteLine%2A> metody <xref:System.IO.StreamWriter> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).  
  
-   Dysk jest pełny (<xref:System.IO.IOException>).  
  
-   Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, że aplikacja musi `Create` dostępu do folderu. Jeśli plik już istnieje, aplikacja musi tylko `Write` dostępu niższego poziomu uprawnień. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` dostęp do jednego pliku, a nie `Create` dostępu dla folderu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [Porady: Odczyt z plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
