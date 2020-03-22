---
title: 'Porady: zapisywanie tekstu do plików za pomocą StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334497"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic

W tym <xref:System.IO.StreamWriter> przykładzie `My.Computer.FileSystem.OpenTextFileWriter` otwiera obiekt z metodą i używa go <xref:System.IO.TextWriter.WriteLine%2A> do zapisu ciągu do pliku tekstowego z metodą <xref:System.IO.StreamWriter> klasy.  
  
## <a name="example"></a>Przykład  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą spowodować wyjątek:  
  
- Plik istnieje i jest tylko<xref:System.IO.IOException>do odczytu ( ).  
  
- Dysk jest zapełniony (<xref:System.IO.IOException>).  
  
- Nazwa ścieżki jest za<xref:System.IO.PathTooLongException>długa ( ).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  

 W tym przykładzie tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta `Create` aplikacja potrzebuje dostępu do folderu. Jeśli plik już istnieje, aplikacja `Write` potrzebuje tylko dostępu, mniejsze uprawnienia. Tam, gdzie to możliwe, jest bardziej bezpieczne, `Read` aby utworzyć plik podczas `Create` wdrażania i tylko udzielić dostępu do jednego pliku, a nie dostęp do folderu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Jak: Odczyt z plików tekstowych](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Zapisywanie w plikach](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
