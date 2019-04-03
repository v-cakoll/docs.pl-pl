---
title: 'Instrukcje: Przekaż plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 486351bc140a2bbf18bb8f85f761fc491f028bba
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840357"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Instrukcje: Przekaż plik w języku Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metoda może służyć do przekazywania pliku i zapisz go w lokalizacji zdalnej. Jeśli `ShowUI` parametr ma wartość `True`, wyświetlane jest okno dialogowe, której jest przedstawiony postęp przekazywania, która umożliwia użytkownikom anulować operację.  
  
### <a name="to-upload-a-file"></a>Aby przekazać plik  
  
-   Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI (Uniform Resource Identifier). Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Aby przekazać plik i wyświetlić postęp operacji  
  
-   Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI. Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez podawania nazwy użytkownika ani hasła, której jest przedstawiony postęp przekazywania i ma interwał limitu czasu 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Aby przekazać plik, podając nazwę użytkownika i hasło  
  
-   Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI i określając nazwę użytkownika i hasło. Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx`, podając nazwę użytkownika `anonymous` i pustego hasła.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą zgłosić wyjątek:  
  
-   Ścieżka pliku lokalnego jest nieprawidłowa (<xref:System.ArgumentException>).  
  
-   Uwierzytelnianie nie powiodło się (<xref:System.Security.SecurityException>).  
  
-   Upłynął limit czasu połączenia (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Instrukcje: Pobierz plik](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Instrukcje: Analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
