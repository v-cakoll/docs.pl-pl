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
ms.openlocfilehash: 4dd45ef70dbe3b1949e6d787748bbb27bb88d52c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046614"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="a9869-102">Instrukcje: Pobierz plik w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a9869-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="a9869-103">Metoda <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> ta umożliwia pobranie pliku zdalnego i zapisanie go w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="a9869-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="a9869-104">Jeśli parametr jest ustawiony na `True`, wyświetlane jest okno dialogowe pokazujące postęp pobierania i Zezwalanie użytkownikom na anulowanie operacji. `ShowUI`</span><span class="sxs-lookup"><span data-stu-id="a9869-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="a9869-105">Domyślnie istniejące pliki o tej samej nazwie nie są zastępowane. Jeśli chcesz zastąpić istniejące pliki, ustaw `overwrite` parametr na. `True`</span><span class="sxs-lookup"><span data-stu-id="a9869-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="a9869-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a9869-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="a9869-107">Nazwa dysku jest nieprawidłowa (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a9869-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="a9869-108">Nie podano niezbędnego uwierzytelniania (<xref:System.UnauthorizedAccessException> lub <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a9869-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="a9869-109">Serwer nie odpowiada w określonym `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="a9869-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="a9869-110">Żądanie jest odrzucane przez witrynę sieci Web<xref:System.Net.WebException>().</span><span class="sxs-lookup"><span data-stu-id="a9869-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="a9869-111">Nie należy podejmować decyzji dotyczących zawartości pliku na podstawie rozszerzenia nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="a9869-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="a9869-112">Na przykład plik Form1. vb nie może być plikiem źródłowym Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a9869-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="a9869-113">Sprawdź wszystkie dane wejściowe, zanim użyjesz danych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9869-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="a9869-114">Zawartość pliku może się różnić od oczekiwanej i metody odczytu z pliku nie zadziałają.</span><span class="sxs-lookup"><span data-stu-id="a9869-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="a9869-115">Aby pobrać plik</span><span class="sxs-lookup"><span data-stu-id="a9869-115">To download a file</span></span>

- <span data-ttu-id="a9869-116">`DownloadFile` Użyj metody, aby pobrać plik, określając lokalizację pliku docelowego jako ciąg lub identyfikator URI i określając lokalizację, w której ma zostać zapisany plik.</span><span class="sxs-lookup"><span data-stu-id="a9869-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="a9869-117">Ten przykład pobiera plik `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisuje go w `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="a9869-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="a9869-118">Aby pobrać plik, określając interwał limitu czasu</span><span class="sxs-lookup"><span data-stu-id="a9869-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="a9869-119">`DownloadFile` Użyj metody, aby pobrać plik, określić lokalizację pliku docelowego jako ciąg lub identyfikator URI, określić lokalizację, w której ma zostać zapisany plik, a także określić interwał limitu czasu w milisekundach (wartość domyślna to 1000).</span><span class="sxs-lookup"><span data-stu-id="a9869-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="a9869-120">Ten przykład umożliwia pobranie pliku `WineList.txt` z `http://www.cohowinery.com/downloads` i zapisanie go `C:\Documents and Settings\All Users\Documents`do, określenie interwału limitu czasu wynoszącego 500 milisekund:</span><span class="sxs-lookup"><span data-stu-id="a9869-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="a9869-121">Aby pobrać plik, podaj nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="a9869-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="a9869-122">`DownLoadFile` Użyj metody, aby pobrać plik, określić lokalizację pliku docelowego jako ciąg lub identyfikator URI oraz określić lokalizację, w której ma zostać zapisany plik, nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="a9869-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="a9869-123">Ten przykład pobiera `WineList.txt` plik z `http://www.cohowinery.com/downloads` i zapisuje go w usłudze `C:\Documents and Settings\All Users\Documents`, przy użyciu nazwy `anonymous` użytkownika i pustego hasła.</span><span class="sxs-lookup"><span data-stu-id="a9869-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="a9869-124">Protokół FTP używany przez `DownLoadFile` metodę wysyła informacje, w tym hasła, w postaci zwykłego tekstu i nie powinien być używany do przesyłania poufnych informacji.</span><span class="sxs-lookup"><span data-stu-id="a9869-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9869-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9869-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="a9869-126">Instrukcje: Przekaż plik</span><span class="sxs-lookup"><span data-stu-id="a9869-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="a9869-127">Instrukcje: Analizowanie ścieżek plików</span><span class="sxs-lookup"><span data-stu-id="a9869-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
