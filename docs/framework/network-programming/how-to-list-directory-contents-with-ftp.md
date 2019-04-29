---
title: 'Instrukcje: Wyświetlanie zawartości katalogu przy użyciu protokołu FTP'
description: W tym artykule przedstawiono przykładowy sposób wyświetlenia listy zawartości katalogu serwera FTP.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
ms.openlocfilehash: 924e6731ce585f127af319fdbfbdc8c12e61c46d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642623"
---
# <a name="how-to-list-directory-contents-with-ftp"></a><span data-ttu-id="1b185-103">Instrukcje: Wyświetlanie zawartości katalogu przy użyciu protokołu FTP</span><span class="sxs-lookup"><span data-stu-id="1b185-103">How to: List directory contents with FTP</span></span>

<span data-ttu-id="1b185-104">Ten przykład ilustruje sposób wyświetlenia listy zawartości katalogu serwera FTP.</span><span class="sxs-lookup"><span data-stu-id="1b185-104">This sample shows how to list the directory contents of an FTP server.</span></span>

## <a name="example"></a><span data-ttu-id="1b185-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b185-105">Example</span></span>

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
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;

            // This example assumes the FTP site uses anonymous logon.
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");

            FtpWebResponse response = (FtpWebResponse)request.GetResponse();

            Stream responseStream = response.GetResponseStream();
            StreamReader reader = new StreamReader(responseStream);
            Console.WriteLine(reader.ReadToEnd());

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}");

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
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)

            Dim responseStream As Stream = response.GetResponseStream()
            Dim reader As StreamReader = New StreamReader(responseStream)
            Console.WriteLine(reader.ReadToEnd())

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}")

            reader.Close()
            response.Close()
        End Sub
    End Module
End Namespace
```

<span data-ttu-id="1b185-106">Jeśli potrzebujesz wyświetlić listę określonego katalogu, wystarczy dodać katalog do końca identyfikatora URI jest używany w <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody:</span><span class="sxs-lookup"><span data-stu-id="1b185-106">If you need to list a specific directory, just add the directory to the end of the URI you're using in the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method:</span></span>

```csharp
FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/your_preferred_directory");
```

```vb
Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/your_preferred_directory"), FtpWebRequest)
```
