---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: bfa7bcefff45bc325d7bba3aa2b9b3a8f0d439fa
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071935"
---
<span data-ttu-id="b5dc0-101">Tworzenie pliku tekstowego o nazwie `azureauth.json`.</span><span class="sxs-lookup"><span data-stu-id="b5dc0-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="b5dc0-102">Wklej dane wyjściowe JSON z podczas tworzenia jednostki usługi.</span><span class="sxs-lookup"><span data-stu-id="b5dc0-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="b5dc0-103">Zapisz ten plik w bezpiecznej lokalizacji w systemie, w której kod może go odczytać.</span><span class="sxs-lookup"><span data-stu-id="b5dc0-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="b5dc0-104">Użyj programu PowerShell, aby `AZURE_AUTH_LOCATION` ustawić zmienną środowiskową o nazwie z pełną ścieżką do pliku, na przykład:</span><span class="sxs-lookup"><span data-stu-id="b5dc0-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
