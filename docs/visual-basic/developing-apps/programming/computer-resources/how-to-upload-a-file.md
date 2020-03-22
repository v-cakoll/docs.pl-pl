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
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="97bce-102">Porady: ładowanie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="97bce-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="97bce-103">Metoda <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> może służyć do przekazywania pliku i przechowywania go w lokalizacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="97bce-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="97bce-104">Jeśli `ShowUI` parametr jest `True`ustawiony na , zostanie wyświetlone okno dialogowe, które pokazuje postęp przekazywania i umożliwia użytkownikom anulowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="97bce-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="97bce-105">Aby przesłać plik</span><span class="sxs-lookup"><span data-stu-id="97bce-105">To upload a file</span></span>  
  
- <span data-ttu-id="97bce-106">Użyj `UploadFile` metody przekazywania pliku, określając lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI (jednolity identyfikator zasobu). W tym przykładzie `Order.txt` `http://www.cohowinery.com/uploads.aspx`przesyła plik do pliku .</span><span class="sxs-lookup"><span data-stu-id="97bce-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="97bce-107">Aby przesłać plik i wyświetlić postęp operacji</span><span class="sxs-lookup"><span data-stu-id="97bce-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="97bce-108">Użyj `UploadFile` metody przekazywania pliku, określając lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="97bce-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="97bce-109">W tym przykładzie `Order.txt` `http://www.cohowinery.com/uploads.aspx` przekazuje plik bez podaniem nazwy użytkownika lub hasła, pokazuje postęp przekazywania i ma limit czasu 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="97bce-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="97bce-110">Aby przekazać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="97bce-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="97bce-111">Użyj `UploadFile` metody przekazywania pliku, określania lokalizacji pliku źródłowego i lokalizacji katalogu docelowego jako ciągu lub identyfikatora URI oraz określania nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="97bce-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="97bce-112">W tym przykładzie `Order.txt` `http://www.cohowinery.com/uploads.aspx`plik przesyła do `anonymous` , podając nazwę użytkownika i puste hasło.</span><span class="sxs-lookup"><span data-stu-id="97bce-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="97bce-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="97bce-113">Robust Programming</span></span>  

 <span data-ttu-id="97bce-114">Następujące warunki mogą zgłaszać wyjątek:</span><span class="sxs-lookup"><span data-stu-id="97bce-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="97bce-115">Lokalna ścieżka pliku jest<xref:System.ArgumentException>nieprawidłowa ( ).</span><span class="sxs-lookup"><span data-stu-id="97bce-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="97bce-116">Uwierzytelnianie nie<xref:System.Security.SecurityException>powiodło się ( ).</span><span class="sxs-lookup"><span data-stu-id="97bce-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="97bce-117">Limit czasu połączenia<xref:System.TimeoutException>( ).</span><span class="sxs-lookup"><span data-stu-id="97bce-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97bce-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97bce-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="97bce-119">Instrukcje: pobieranie pliku</span><span class="sxs-lookup"><span data-stu-id="97bce-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="97bce-120">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="97bce-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
