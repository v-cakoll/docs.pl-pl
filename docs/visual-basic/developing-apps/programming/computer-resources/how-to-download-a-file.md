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
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="166f2-102">Porady: pobieranie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="166f2-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="166f2-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metody można użyć do pobrania pliku zdalnego i zapisz go w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="166f2-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="166f2-104">Jeśli `ShowUI` ustawiono parametr `True`, jest wyświetlane okno dialogowe pokazujące postęp pobierania, dzięki czemu użytkownicy anulować operację.</span><span class="sxs-lookup"><span data-stu-id="166f2-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="166f2-105">Domyślnie nie są zastępowane istniejące pliki o tej samej nazwie; Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`.</span><span class="sxs-lookup"><span data-stu-id="166f2-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="166f2-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="166f2-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="166f2-107">Nazwa dysku jest nieprawidłowa (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="166f2-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="166f2-108">Nie został podany niezbędne uwierzytelniania (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="166f2-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="166f2-109">Serwer nie odpowie w ciągu określonego `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="166f2-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="166f2-110">Żądanie zostało odrzucone przez witrynę sieci Web (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="166f2-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="166f2-111">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="166f2-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="166f2-112">Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="166f2-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="166f2-113">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="166f2-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="166f2-114">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="166f2-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="166f2-115">Aby pobrać plik</span><span class="sxs-lookup"><span data-stu-id="166f2-115">To download a file</span></span>  
  
-   <span data-ttu-id="166f2-116">Użyj `DownloadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI i określając lokalizację, w której do przechowywania pliku.</span><span class="sxs-lookup"><span data-stu-id="166f2-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="166f2-117">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="166f2-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="166f2-118">Aby pobrać plik, określając interwał limitu czasu</span><span class="sxs-lookup"><span data-stu-id="166f2-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="166f2-119">Użyj `DownloadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI, określając lokalizację, w której chcesz przechowywać plik i Określanie limitu czasu w milisekundach (wartość domyślna to 1000).</span><span class="sxs-lookup"><span data-stu-id="166f2-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="166f2-120">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`, określając limitu czasu w milisekundach czas oczekiwania, 500:</span><span class="sxs-lookup"><span data-stu-id="166f2-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="166f2-121">Aby pobrać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="166f2-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="166f2-122">Użyj `DownLoadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI i określając lokalizację, w którym ma być przechowywany plik, nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="166f2-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="166f2-123">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`, nazwą użytkownika `anonymous` i pustego hasła.</span><span class="sxs-lookup"><span data-stu-id="166f2-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="166f2-124">Protokół FTP używany przez `DownLoadFile` metoda wysyła informacje, w tym hasła w postaci zwykłego tekstu i nie powinna być używana do przesyłania poufnych informacji.</span><span class="sxs-lookup"><span data-stu-id="166f2-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166f2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="166f2-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [<span data-ttu-id="166f2-126">Instrukcje: przekazywanie pliku</span><span class="sxs-lookup"><span data-stu-id="166f2-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [<span data-ttu-id="166f2-127">Instrukcje: analizowanie ścieżek plików</span><span class="sxs-lookup"><span data-stu-id="166f2-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
