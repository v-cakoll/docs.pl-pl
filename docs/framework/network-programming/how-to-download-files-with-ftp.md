---
title: 'Porady: pobieranie plików przy użyciu FTP'
ms.date: 03/30/2017
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a3e0b5773a98b42411e4dd76668dafb834b5cbd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394852"
---
# <a name="how-to-download-files-with-ftp"></a><span data-ttu-id="5f966-102">Porady: pobieranie plików przy użyciu FTP</span><span class="sxs-lookup"><span data-stu-id="5f966-102">How to: Download Files with FTP</span></span>
<span data-ttu-id="5f966-103">Ten przykład przedstawia sposób pobierania pliku z serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="5f966-103">This sample shows how to download a file from an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f966-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f966-104">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");  
            request.Method = WebRequestMethods.Ftp.DownloadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Download Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();    
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f966-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5f966-105">Compiling the Code</span></span>  
 <span data-ttu-id="5f966-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="5f966-106">This example requires:</span></span>  
  
-   <span data-ttu-id="5f966-107">Odwołuje się do **System.Net** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5f966-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5f966-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5f966-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5f966-109">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5f966-109">.NET Framework Security</span></span>
