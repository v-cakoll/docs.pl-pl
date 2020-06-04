---
title: 'Instrukcje: przekazywanie pliku'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: cee6811d6b6d295c28eb683c5d2f7bcbb5fe94ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401813"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="e1ef8-102">Porady: ładowanie pliku w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1ef8-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="e1ef8-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>Metoda ta umożliwia przekazanie pliku i zapisanie go w lokalizacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="e1ef8-104">Jeśli `ShowUI` parametr jest ustawiony na `True` , wyświetlane jest okno dialogowe, które pokazuje postęp przekazywania i umożliwia użytkownikom anulowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="e1ef8-105">Aby przekazać plik</span><span class="sxs-lookup"><span data-stu-id="e1ef8-105">To upload a file</span></span>  
  
- <span data-ttu-id="e1ef8-106">Za pomocą `UploadFile` metody Przekaż plik, określając lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI (Uniform Resource Identifier). Ten przykład przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx` .</span><span class="sxs-lookup"><span data-stu-id="e1ef8-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="e1ef8-107">Aby przekazać plik i wyświetlić postęp operacji</span><span class="sxs-lookup"><span data-stu-id="e1ef8-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="e1ef8-108">Użyj `UploadFile` metody, aby przekazać plik, określając lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="e1ef8-109">Ten przykład przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez podawania nazwy użytkownika lub hasła, pokazuje postęp przekazywania i ma interwał limitu czasu wynoszący 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="e1ef8-110">Aby przekazać plik, należy podać nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="e1ef8-111">Użyj `UploadFile` metody, aby przekazać plik, określić lokalizację pliku źródłowego i lokalizację katalogu docelowego jako ciąg lub identyfikator URI oraz określić nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="e1ef8-112">Ten przykład przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx` , podając nazwę użytkownika `anonymous` i puste hasło.</span><span class="sxs-lookup"><span data-stu-id="e1ef8-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e1ef8-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e1ef8-113">Robust Programming</span></span>  

 <span data-ttu-id="e1ef8-114">Następujące warunki mogą zgłosić wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e1ef8-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="e1ef8-115">Lokalna ścieżka pliku jest nieprawidłowa ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="e1ef8-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="e1ef8-116">Uwierzytelnianie nie powiodło się ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="e1ef8-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="e1ef8-117">Przekroczono limit czasu połączenia ( <xref:System.TimeoutException> ).</span><span class="sxs-lookup"><span data-stu-id="e1ef8-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ef8-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1ef8-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="e1ef8-119">Instrukcje: pobieranie pliku</span><span class="sxs-lookup"><span data-stu-id="e1ef8-119">How to: Download a File</span></span>](how-to-download-a-file.md)
- [<span data-ttu-id="e1ef8-120">Instrukcje: Analizowanie ścieżek plików</span><span class="sxs-lookup"><span data-stu-id="e1ef8-120">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
