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
ms.openlocfilehash: 927f2598e064ddcda30a13d811bc4a986207b23d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969014"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="b2c2b-102">Instrukcje: Pobierz plik w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2c2b-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="b2c2b-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metoda może służyć do pobrania pliku zdalnego i zapisz go do określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="b2c2b-104">Jeśli `ShowUI` parametr ma wartość `True`, pojawia się okno dialogowe pokazujące postęp pobierania oraz zezwalanie użytkownikom na anulowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="b2c2b-105">Domyślnie nie są zastępowane istniejące pliki o tej samej nazwie; Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="b2c2b-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="b2c2b-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b2c2b-107">Nazwa dysku nie jest prawidłowa (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b2c2b-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b2c2b-108">Wymagane uwierzytelnienie nie został podany (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b2c2b-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="b2c2b-109">Serwer nie odpowiada w ramach określonych `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="b2c2b-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="b2c2b-110">Żądanie zostanie odrzucone przez witrynę sieci Web (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="b2c2b-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2c2b-111">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="b2c2b-112">Na przykład plik Form1.vb może nie być plik źródłowy w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="b2c2b-113">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="b2c2b-114">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="b2c2b-115">Aby pobrać plik</span><span class="sxs-lookup"><span data-stu-id="b2c2b-115">To download a file</span></span>  
  
-   <span data-ttu-id="b2c2b-116">Użyj `DownloadFile` metody do pobierania plików, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w którym będzie przechowywany plik.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="b2c2b-117">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go do `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="b2c2b-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="b2c2b-118">Aby pobrać plik, określając interwał limitu czasu</span><span class="sxs-lookup"><span data-stu-id="b2c2b-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="b2c2b-119">Użyj `DownloadFile` metody do pobierania plików, określanie lokalizacji pliku docelowego jako ciąg lub identyfikator URI, określając lokalizację, w którym będzie przechowywany plik i określanie interwału limitu czasu w milisekundach (wartość domyślna to 1000).</span><span class="sxs-lookup"><span data-stu-id="b2c2b-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="b2c2b-120">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go do `C:\Documents and Settings\All Users\Documents`, określając 500 milisekund interwał limitu czasu:</span><span class="sxs-lookup"><span data-stu-id="b2c2b-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="b2c2b-121">Aby pobrać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="b2c2b-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="b2c2b-122">Użyj `DownLoadFile` metody do pobierania plików, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w którym będzie przechowywany w pliku, nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="b2c2b-123">W tym przykładzie pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go do `C:\Documents and Settings\All Users\Documents`, z nazwą użytkownika `anonymous` i pustego hasła.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="b2c2b-124">Protokół FTP, używany przez `DownLoadFile` metoda wysyła informacje, w tym hasła w postaci zwykłego tekstu i nie powinny być używane do przesyłania informacji poufnych.</span><span class="sxs-lookup"><span data-stu-id="b2c2b-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c2b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2c2b-125">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="b2c2b-126">Instrukcje: Przekaż plik</span><span class="sxs-lookup"><span data-stu-id="b2c2b-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="b2c2b-127">Instrukcje: Analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="b2c2b-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
