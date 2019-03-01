---
title: 'Instrukcje: Przekaż plik w języku Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 4e2c7a37f8d8a0fc71e0fd80d04dc5e24ad498ed
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972368"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="55ec4-102">Instrukcje: Przekaż plik w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55ec4-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="55ec4-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metoda może służyć do przekazywania pliku i zapisz go w lokalizacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="55ec4-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="55ec4-104">Jeśli `ShowUI` parametr ma wartość `True`, wyświetlane jest okno dialogowe, której jest przedstawiony postęp przekazywania, która umożliwia użytkownikom anulować operację.</span><span class="sxs-lookup"><span data-stu-id="55ec4-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="55ec4-105">Aby przekazać plik</span><span class="sxs-lookup"><span data-stu-id="55ec4-105">To upload a file</span></span>  
  
-   <span data-ttu-id="55ec4-106">Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI (Uniform Resource Identifier). Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="55ec4-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="55ec4-107">Aby przekazać plik i wyświetlić postęp operacji</span><span class="sxs-lookup"><span data-stu-id="55ec4-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="55ec4-108">Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="55ec4-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="55ec4-109">Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez podawania nazwy użytkownika ani hasła, której jest przedstawiony postęp przekazywania i ma interwał limitu czasu 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="55ec4-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="55ec4-110">Aby przekazać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="55ec4-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="55ec4-111">Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI i określając nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="55ec4-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="55ec4-112">Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx`, podając nazwę użytkownika `anonymous` i pustego hasła.</span><span class="sxs-lookup"><span data-stu-id="55ec4-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="55ec4-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="55ec4-113">Robust Programming</span></span>  
 <span data-ttu-id="55ec4-114">Następujące warunki mogą zgłosić wyjątek:</span><span class="sxs-lookup"><span data-stu-id="55ec4-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="55ec4-115">Ścieżka pliku lokalnego jest nieprawidłowa (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="55ec4-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="55ec4-116">Uwierzytelnianie nie powiodło się (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="55ec4-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="55ec4-117">Upłynął limit czasu połączenia (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="55ec4-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55ec4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55ec4-118">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="55ec4-119">Instrukcje: Pobierz plik</span><span class="sxs-lookup"><span data-stu-id="55ec4-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="55ec4-120">Instrukcje: Analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="55ec4-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
