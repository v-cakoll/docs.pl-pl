---
title: 'Porady: ładowanie pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 769c04430f8323dfde680fca45cfcd67809bdab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Porady: ładowanie pliku w Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metoda może służyć do przekazania pliku i zapisz go w lokalizacji zdalnej. Jeśli `ShowUI` ustawiono parametr `True`, wyświetlane jest okno dialogowe, będzie wyświetlany postęp przekazywania, który umożliwia użytkownikom anulować operację.  
  
### <a name="to-upload-a-file"></a>Aby przekazać plik  
  
-   Użyj `UploadFile` metody, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizacji katalogu jako ciągu lub identyfikator URI (Uniform Resource Identifier). W tym przykładzie powoduje przekazanie pliku `Order.txt` do `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Aby przekazać plik i wyświetlić postęp operacji  
  
-   Użyj `UploadFile` metody, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizacji katalogu jako ciągu lub identyfikator URI. W tym przykładzie powoduje przekazanie pliku `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez podawania nazwy użytkownika ani hasła, będzie wyświetlany postęp przekazywania i ma limit czasu 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Aby przekazać plik, podając nazwę użytkownika i hasło  
  
-   Użyj `UploadFile` metody, aby przekazać plik, określić lokalizację pliku źródłowego i docelowego lokalizacji katalogu jako ciągu lub identyfikator URI, a następnie określając nazwę użytkownika i hasło. W tym przykładzie powoduje przekazanie pliku `Order.txt` do `http://www.cohowinery.com/uploads.aspx`, podanie nazwy użytkownika `anonymous` i pustego hasła.  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Poniższe warunki mogą zgłosić wyjątek:  
  
-   Ścieżka pliku lokalnego jest nieprawidłowa (<xref:System.ArgumentException>).  
  
-   Uwierzytelnianie nie powiodło się (<xref:System.Security.SecurityException>).  
  
-   Upłynął limit czasu połączenia (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>  
 [Instrukcje: pobieranie pliku](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [Instrukcje: analizowanie ścieżek plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
