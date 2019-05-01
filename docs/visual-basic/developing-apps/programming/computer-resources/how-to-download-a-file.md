---
title: 'Instrukcje: Pobierz plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: bebb40a732415312742116b0b94743495049c477
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014014"
---
# <a name="how-to-download-a-file-in-visual-basic"></a>Instrukcje: Pobierz plik w języku Visual Basic
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metoda może służyć do pobrania pliku zdalnego i zapisz go do określonej lokalizacji. Jeśli `ShowUI` parametr ma wartość `True`, pojawia się okno dialogowe pokazujące postęp pobierania oraz zezwalanie użytkownikom na anulowanie operacji. Domyślnie nie są zastępowane istniejące pliki o tej samej nazwie; Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa dysku nie jest prawidłowa (<xref:System.ArgumentException>).  
  
- Wymagane uwierzytelnienie nie został podany (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).  
  
- Serwer nie odpowiada w ramach określonych `connectionTimeout` (<xref:System.TimeoutException>).  
  
- Żądanie zostanie odrzucone przez witrynę sieci Web (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku. Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic. Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji. Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.  
  
### <a name="to-download-a-file"></a>Aby pobrać plik  
  
- Użyj `DownloadFile` metody do pobierania plików, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w którym będzie przechowywany plik. W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go do `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Aby pobrać plik, określając interwał limitu czasu  
  
- Użyj `DownloadFile` metody do pobierania plików, określanie lokalizacji pliku docelowego jako ciąg lub identyfikator URI, określając lokalizację, w którym będzie przechowywany plik i określanie interwału limitu czasu w milisekundach (wartość domyślna to 1000). W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go do `C:\Documents and Settings\All Users\Documents`, określając 500 milisekund interwał limitu czasu:  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Aby pobrać plik, podając nazwę użytkownika i hasło  
  
- Użyj `DownLoadFile` metody do pobierania plików, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w którym będzie przechowywany w pliku, nazwę użytkownika i hasło. W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go do `C:\Documents and Settings\All Users\Documents`, z nazwą użytkownika `anonymous` i pustego hasła.  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  Protokół FTP, używany przez `DownLoadFile` metoda wysyła informacje, w tym hasła w postaci zwykłego tekstu i nie powinny być używane do przesyłania informacji poufnych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [Instrukcje: Przekaż plik](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [Instrukcje: Analizowanie ścieżek pliku](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
