---
title: "Porady: ładowanie pliku w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a0fab9b812ddff1f56e9fa203bd297fd70bc47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Porady: pobieranie pliku](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [Porady: analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
