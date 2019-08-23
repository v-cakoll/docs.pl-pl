---
title: 'Instrukcje: Pobierz plik w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 9986a784e73f12698281f17a9d8e022e806504cb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957832"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Instrukcje: Pobierz plik w Visual Basic
Metoda <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> ta umożliwia pobranie pliku zdalnego i zapisanie go w określonej lokalizacji. Jeśli parametr jest ustawiony na `True`, wyświetlane jest okno dialogowe pokazujące postęp pobierania i Zezwalanie użytkownikom na anulowanie operacji. `ShowUI` Domyślnie istniejące pliki o tej samej nazwie nie są zastępowane. Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr na. `True`  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa dysku jest nieprawidłowa (<xref:System.ArgumentException>).  
  
- Nie podano niezbędnego uwierzytelniania (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).  
  
- Serwer nie odpowiada w określonym `connectionTimeout` (<xref:System.TimeoutException>).  
  
- Żądanie jest odrzucane przez witrynę sieci Web<xref:System.Net.WebException>().  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
> Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
### <a name="to-download-a-file"></a>Aby pobrać plik  
  
- `DownloadFile` Użyj metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w której ma zostać zapisany plik. Ten przykład pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go w `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Aby pobrać plik, określając interwał limitu czasu  
  
- `DownloadFile` Użyj metody, aby pobrać plik, określić lokalizację pliku docelowego jako ciąg lub identyfikator URI, określić lokalizację, w której ma zostać zapisany plik, a także określić interwał limitu czasu w milisekundach (wartość domyślna to 1000). Ten przykład umożliwia pobranie pliku `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisanie go `C:\Documents and Settings\All Users\Documents`do, określenie interwału limitu czasu wynoszącego 500 milisekund:  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Aby pobrać plik, podaj nazwę użytkownika i hasło  
  
- `DownLoadFile` Użyj metody, aby pobrać plik, określić lokalizację pliku docelowego jako ciąg lub identyfikator URI oraz określić lokalizację, w której ma zostać zapisany plik, nazwę użytkownika i hasło. Ten przykład pobiera `WineList.txt` plik z `http://www.cohowinery.com/downloads` i zapisuje go w usłudze `C:\Documents and Settings\All Users\Documents`, przy użyciu nazwy `anonymous` użytkownika i pustego hasła.  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  Protokół FTP używany przez `DownLoadFile` metodę wysyła informacje, w tym hasła, w postaci zwykłego tekstu i nie powinien być używany do przesyłania poufnych informacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Instrukcje: Przekaż plik](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Instrukcje: Analizowanie ścieżek plików](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
