---
title: 'Porady: ładowanie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345557"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Porady: ładowanie pliku w Visual Basic

Metoda <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> może służyć do przekazywania pliku i przechowywania go w lokalizacji zdalnej. Jeśli `ShowUI` parametr jest `True`ustawiony na , zostanie wyświetlone okno dialogowe, które pokazuje postęp przekazywania i umożliwia użytkownikom anulowanie operacji.  
  
### <a name="to-upload-a-file"></a>Aby przesłać plik  
  
- Użyj `UploadFile` metody przekazywania pliku, określając lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI (jednolity identyfikator zasobu). W tym przykładzie `Order.txt` `http://www.cohowinery.com/uploads.aspx`przesyła plik do pliku .  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Aby przesłać plik i wyświetlić postęp operacji  
  
- Użyj `UploadFile` metody przekazywania pliku, określając lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI. W tym przykładzie `Order.txt` `http://www.cohowinery.com/uploads.aspx` przekazuje plik bez podaniem nazwy użytkownika lub hasła, pokazuje postęp przekazywania i ma limit czasu 500 milisekund.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Aby przekazać plik, podając nazwę użytkownika i hasło  
  
- Użyj `UploadFile` metody przekazywania pliku, określania lokalizacji pliku źródłowego i lokalizacji katalogu docelowego jako ciągu lub identyfikatora URI oraz określania nazwy użytkownika i hasła. W tym przykładzie `Order.txt` `http://www.cohowinery.com/uploads.aspx`plik przesyła do `anonymous` , podając nazwę użytkownika i puste hasło.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  

 Następujące warunki mogą zgłaszać wyjątek:  
  
- Lokalna ścieżka pliku jest<xref:System.ArgumentException>nieprawidłowa ( ).  
  
- Uwierzytelnianie nie<xref:System.Security.SecurityException>powiodło się ( ).  
  
- Limit czasu połączenia<xref:System.TimeoutException>( ).  
  
## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Instrukcje: pobieranie pliku](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Porady: analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
