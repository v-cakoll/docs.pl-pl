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
Utwórz plik tekstowy o nazwie `azureauth.json`. Wklej dane wyjściowe JSON z programu podczas tworzenia jednostki usługi.

Zapisz ten plik w bezpiecznej lokalizacji w systemie, w której kod może go odczytać. Użyj programu PowerShell, aby ustawić zmienną środowiskową o nazwie `AZURE_AUTH_LOCATION` z pełną ścieżką do pliku, na przykład:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
