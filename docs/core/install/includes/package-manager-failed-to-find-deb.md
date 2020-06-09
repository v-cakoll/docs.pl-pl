---
ms.openlocfilehash: 7d398df060c031ae891218b82a2712d74f4c33b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602986"
---

Jeśli zostanie wyświetlony komunikat o błędzie podobny do następującego: **nie można zlokalizować pakietu {servicecore-Package}**, uruchom następujące polecenia.

W poniższym zestawie poleceń znajdują się dwa symbole zastępcze.

- `{dotnet-package}`\
Reprezentuje pakiet .NET Core, który instalujesz, na przykład `aspnetcore-runtime-3.1` . Ta wartość jest używana w `sudo apt-get install` poniższym poleceniu.

- `{os-version}`\
Oznacza to, że wersja systemu Linux jest włączona. Ta wartość jest używana w `wget` poniższym poleceniu.

Spróbuj wyczyszczenie listy pakietów:

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {dotnet-package}
```

Jeśli to nie zadziała, można uruchomić instalację ręczną przy użyciu następujących poleceń:
