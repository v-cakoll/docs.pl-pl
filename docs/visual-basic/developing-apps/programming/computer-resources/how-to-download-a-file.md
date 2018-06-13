---
title: 'Porady: pobieranie pliku w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: b0dc95674e17a7aba9b04a8b7e0b82c9c97c4180
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590734"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Porady: pobieranie pliku w Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metody można użyć do pobrania pliku zdalnego i zapisz go w określonej lokalizacji. Jeśli `ShowUI` ustawiono parametr `True`, jest wyświetlane okno dialogowe pokazujące postęp pobierania, dzięki czemu użytkownicy anulować operację. Domyślnie nie są zastępowane istniejące pliki o tej samej nazwie; Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa dysku jest nieprawidłowa (<xref:System.ArgumentException>).  
  
-   Nie został podany niezbędne uwierzytelniania (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).  
  
-   Serwer nie odpowie w ciągu określonego `connectionTimeout` (<xref:System.TimeoutException>).  
  
-   Żądanie zostało odrzucone przez witrynę sieci Web (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
### <a name="to-download-a-file"></a>Aby pobrać plik  
  
-   Użyj `DownloadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI i określając lokalizację, w której do przechowywania pliku. W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Aby pobrać plik, określając interwał limitu czasu  
  
-   Użyj `DownloadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI, określając lokalizację, w której chcesz przechowywać plik i Określanie limitu czasu w milisekundach (wartość domyślna to 1000). W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`, określając limitu czasu w milisekundach czas oczekiwania, 500:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Aby pobrać plik, podając nazwę użytkownika i hasło  
  
-   Użyj `DownLoadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI i określając lokalizację, w którym ma być przechowywany plik, nazwę użytkownika i hasło. W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`, nazwą użytkownika `anonymous` i pustego hasła.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  Protokół FTP używany przez `DownLoadFile` metoda wysyła informacje, w tym hasła w postaci zwykłego tekstu i nie powinna być używana do przesyłania poufnych informacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [Instrukcje: przekazywanie pliku](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [Instrukcje: analizowanie ścieżek plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
