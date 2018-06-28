---
title: 'Porady: pobieranie plików przy użyciu FTP'
description: W tym artykule przedstawiono przykład sposobu pobierania pliku z serwera FTP.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
ms.openlocfilehash: 4e000aa149a9a02e6f12e9b184d9c43a065b673f
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028308"
---
# <a name="how-to-download-files-with-ftp"></a><span data-ttu-id="0ae01-103">Porady: pobieranie plików przy użyciu FTP</span><span class="sxs-lookup"><span data-stu-id="0ae01-103">How to: Download files with FTP</span></span>

<span data-ttu-id="0ae01-104">Ten przykład przedstawia sposób pobierania pliku z serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="0ae01-104">This sample shows how to download a file from an FTP server.</span></span>

## <a name="example"></a><span data-ttu-id="0ae01-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ae01-105">Example</span></span>

```csharp
using System;
using System.IO;
using System.Net;

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
            request.Credentials = new NetworkCredential("anonymous","janeDoe@contoso.com");

            FtpWebResponse response = (FtpWebResponse)request.GetResponse();

            Stream responseStream = response.GetResponseStream();
            StreamReader reader = new StreamReader(responseStream);
            Console.WriteLine(reader.ReadToEnd());

            Console.WriteLine($"Download Complete, status {response.StatusDescription}");

            reader.Close();
            response.Close();
        }
    }
}
```

```vb
Imports System.IO
Imports System.Net

Namespace Examples.System.Net
    Public Module WebRequestGetExample
        Public Sub Main()
            ' Get the object used to communicate with the server.
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/test.htm"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.DownloadFile

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)

            Dim responseStream As Stream = response.GetResponseStream()
            Dim reader As StreamReader = New StreamReader(responseStream)
            Console.WriteLine(reader.ReadToEnd())

            Console.WriteLine($"Download Complete, status {response.StatusDescription}")

            reader.Close()
            response.Close()
        End Sub
    End Module
End Namespace
```