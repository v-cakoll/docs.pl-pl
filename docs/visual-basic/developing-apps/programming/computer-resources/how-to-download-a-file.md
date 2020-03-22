---
title: 'Porady: pobieranie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4923feb46ff638de9514a4d70fc00367491a6f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345622"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="e14c6-102">Porady: pobieranie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e14c6-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="e14c6-103">Metoda <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> ta może służyć do pobierania pliku zdalnego i przechowywania go w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e14c6-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="e14c6-104">Jeśli `ShowUI` parametr jest `True`ustawiony na , zostanie wyświetlone okno dialogowe pokazujące postęp pobierania i umożliwiające użytkownikom anulowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="e14c6-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="e14c6-105">Domyślnie istniejące pliki o tej samej nazwie nie są zastępowane; jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr `True`na .</span><span class="sxs-lookup"><span data-stu-id="e14c6-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="e14c6-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e14c6-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="e14c6-107">Nazwa dysku jest<xref:System.ArgumentException>nieprawidłowa ( ).</span><span class="sxs-lookup"><span data-stu-id="e14c6-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="e14c6-108">Nie dostarczono niezbędnego<xref:System.UnauthorizedAccessException> <xref:System.Security.SecurityException>uwierzytelnienia ( lub ).</span><span class="sxs-lookup"><span data-stu-id="e14c6-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="e14c6-109">Serwer nie odpowiada w `connectionTimeout` ramach<xref:System.TimeoutException>określonego ( ).</span><span class="sxs-lookup"><span data-stu-id="e14c6-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="e14c6-110">Żądanie jest odrzucane przez<xref:System.Net.WebException>witrynę sieci Web ( ).</span><span class="sxs-lookup"><span data-stu-id="e14c6-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="e14c6-111">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="e14c6-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e14c6-112">Na przykład plik Form1.vb może nie być plikiem źródłowym języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e14c6-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="e14c6-113">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e14c6-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="e14c6-114">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="e14c6-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="e14c6-115">Aby pobrać plik</span><span class="sxs-lookup"><span data-stu-id="e14c6-115">To download a file</span></span>

- <span data-ttu-id="e14c6-116">Użyj `DownloadFile` metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w której ma być przechowywany plik.</span><span class="sxs-lookup"><span data-stu-id="e14c6-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="e14c6-117">W tym przykładzie `WineList.txt` `http://www.cohowinery.com/downloads` plik jest pobierany i zapisywany w: `C:\Documents and Settings\All Users\Documents`</span><span class="sxs-lookup"><span data-stu-id="e14c6-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="e14c6-118">Aby pobrać plik, określanie przedziału przesuwu</span><span class="sxs-lookup"><span data-stu-id="e14c6-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="e14c6-119">Użyj `DownloadFile` metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI, określając lokalizację, w której plik ma być przechowywany, i określając przedział limitów czasu w milisekundach (wartość domyślna to 1000).</span><span class="sxs-lookup"><span data-stu-id="e14c6-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="e14c6-120">W tym przykładzie `WineList.txt` `http://www.cohowinery.com/downloads` pobiera plik i `C:\Documents and Settings\All Users\Documents`zapisuje go do , określając przedział limit czasu 500 milisekund:</span><span class="sxs-lookup"><span data-stu-id="e14c6-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="e14c6-121">Aby pobrać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="e14c6-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="e14c6-122">Użyj `DownLoadFile` metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w której ma być przechowywany plik, nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="e14c6-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="e14c6-123">W tym przykładzie `WineList.txt` `http://www.cohowinery.com/downloads` pobiera plik i `C:\Documents and Settings\All Users\Documents`zapisuje go `anonymous` do , z nazwą użytkownika i pustym hasłem.</span><span class="sxs-lookup"><span data-stu-id="e14c6-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="e14c6-124">Protokół FTP stosowany `DownLoadFile` w tej metodzie wysyła informacje, w tym hasła, w postaci zwykłego tekstu i nie powinien być używany do przekazywania informacji poufnych.</span><span class="sxs-lookup"><span data-stu-id="e14c6-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="e14c6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e14c6-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="e14c6-126">Instrukcje: przekazywanie pliku</span><span class="sxs-lookup"><span data-stu-id="e14c6-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="e14c6-127">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="e14c6-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
