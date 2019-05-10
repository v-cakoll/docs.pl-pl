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
ms.openlocfilehash: b2c313078e3438c84068b6cc54d787b567a768b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662701"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="a4624-102">Instrukcje: Przekaż plik w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4624-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="a4624-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metoda może służyć do przekazywania pliku i zapisz go w lokalizacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="a4624-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="a4624-104">Jeśli `ShowUI` parametr ma wartość `True`, wyświetlane jest okno dialogowe, której jest przedstawiony postęp przekazywania, która umożliwia użytkownikom anulować operację.</span><span class="sxs-lookup"><span data-stu-id="a4624-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="a4624-105">Aby przekazać plik</span><span class="sxs-lookup"><span data-stu-id="a4624-105">To upload a file</span></span>  
  
- <span data-ttu-id="a4624-106">Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI (Uniform Resource Identifier). Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="a4624-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="a4624-107">Aby przekazać plik i wyświetlić postęp operacji</span><span class="sxs-lookup"><span data-stu-id="a4624-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="a4624-108">Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="a4624-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="a4624-109">Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez podawania nazwy użytkownika ani hasła, której jest przedstawiony postęp przekazywania i ma interwał limitu czasu 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="a4624-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="a4624-110">Aby przekazać plik, podając nazwę użytkownika i hasło</span><span class="sxs-lookup"><span data-stu-id="a4624-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="a4624-111">Użyj `UploadFile` metodę, aby przekazać plik, określając lokalizację pliku źródłowego i docelowego lokalizację katalogu jako ciąg lub identyfikator URI i określając nazwę użytkownika i hasło.</span><span class="sxs-lookup"><span data-stu-id="a4624-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="a4624-112">Ten przykładowy przekazuje plik `Order.txt` do `http://www.cohowinery.com/uploads.aspx`, podając nazwę użytkownika `anonymous` i pustego hasła.</span><span class="sxs-lookup"><span data-stu-id="a4624-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a4624-113">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a4624-113">Robust Programming</span></span>  
 <span data-ttu-id="a4624-114">Następujące warunki mogą zgłosić wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a4624-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="a4624-115">Ścieżka pliku lokalnego jest nieprawidłowa (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="a4624-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="a4624-116">Uwierzytelnianie nie powiodło się (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a4624-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="a4624-117">Upłynął limit czasu połączenia (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="a4624-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4624-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4624-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="a4624-119">Instrukcje: Pobierz plik</span><span class="sxs-lookup"><span data-stu-id="a4624-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="a4624-120">Instrukcje: Analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="a4624-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
