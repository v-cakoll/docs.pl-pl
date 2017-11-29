---
title: 'Porady: pobieranie pliku w Visual Basic'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc67d28b870f86c6464e86f7682f71e6e36ea9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="4f7db-102">Porady: pobieranie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f7db-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="4f7db-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metody można użyć do pobrania pliku zdalnego i zapisz go w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4f7db-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="4f7db-104">Jeśli `ShowUI` ustawiono parametr `True`, jest wyświetlane okno dialogowe pokazujące postęp pobierania, dzięki czemu użytkownicy anulować operację.</span><span class="sxs-lookup"><span data-stu-id="4f7db-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="4f7db-105">Domyślnie nie są zastępowane istniejące pliki o tej samej nazwie; Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`.</span><span class="sxs-lookup"><span data-stu-id="4f7db-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="4f7db-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="4f7db-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="4f7db-107">Nazwa dysku jest nieprawidłowa (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="4f7db-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="4f7db-108">Nie został podany niezbędne uwierzytelniania (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="4f7db-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="4f7db-109">Serwer nie odpowie w ciągu określonego `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="4f7db-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="4f7db-110">Żądanie zostało odrzucone przez witrynę sieci Web (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="4f7db-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f7db-111">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4f7db-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="4f7db-112">Na przykład plik Form1.vb nie może być plik źródłowy języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4f7db-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="4f7db-113">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f7db-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="4f7db-114">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="4f7db-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="4f7db-115">Aby pobrać plik</span><span class="sxs-lookup"><span data-stu-id="4f7db-115">To download a file</span></span>  
  
-   <span data-ttu-id="4f7db-116">Użyj `DownloadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI i określając lokalizację, w której do przechowywania pliku.</span><span class="sxs-lookup"><span data-stu-id="4f7db-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="4f7db-117">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="4f7db-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="4f7db-118">Aby pobrać plik, określając interwał limitu czasu</span><span class="sxs-lookup"><span data-stu-id="4f7db-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="4f7db-119">Użyj `DownloadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI, określając lokalizację, w której chcesz przechowywać plik i Określanie limitu czasu w milisekundach (wartość domyślna to 1000).</span><span class="sxs-lookup"><span data-stu-id="4f7db-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="4f7db-120">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`, określając limitu czasu w milisekundach czas oczekiwania, 500:</span><span class="sxs-lookup"><span data-stu-id="4f7db-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="4f7db-121">Aby pobrać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="4f7db-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="4f7db-122">Użyj `DownLoadFile` metodę, aby pobrać plik Określanie lokalizacji pliku docelowego jako ciągu lub identyfikator URI i określając lokalizację, w którym ma być przechowywany plik, nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="4f7db-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="4f7db-123">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje ją `C:\Documents and Settings\All Users\Documents`, nazwą użytkownika `anonymous` i pustego hasła.</span><span class="sxs-lookup"><span data-stu-id="4f7db-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4f7db-124">Protokół FTP używany przez `DownLoadFile` metoda wysyła informacje, w tym hasła w postaci zwykłego tekstu i nie powinna być używana do przesyłania poufnych informacji.</span><span class="sxs-lookup"><span data-stu-id="4f7db-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7db-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4f7db-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [<span data-ttu-id="4f7db-126">Porady: ładowanie pliku</span><span class="sxs-lookup"><span data-stu-id="4f7db-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [<span data-ttu-id="4f7db-127">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="4f7db-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
