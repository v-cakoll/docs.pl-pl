---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540117"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="bc42a-101">Instalowanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="bc42a-101">Install the global tool</span></span>

<span data-ttu-id="bc42a-102">Zasoby pakietu powinny być instalowane w chronionej lokalizacji przy użyciu `--tool-path` tej opcji.</span><span class="sxs-lookup"><span data-stu-id="bc42a-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="bc42a-103">Ta separacja pozwala uniknąć udostępniania ograniczonego środowiska użytkownika z podwyższonym poziomem ochrony środowiska.</span><span class="sxs-lookup"><span data-stu-id="bc42a-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="bc42a-104">`/usr/local/share/dotnet-tools`zostanie utworzony za `drwxr-xr-x`zgodą .</span><span class="sxs-lookup"><span data-stu-id="bc42a-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="bc42a-105">Jeśli katalog już istnieje, `ls -l` użyj polecenia, aby sprawdzić, czy użytkownik z ograniczeniami nie ma uprawnień do edytowania katalogu.</span><span class="sxs-lookup"><span data-stu-id="bc42a-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="bc42a-106">Jeśli tak, `sudo chmod o-w -R /usr/share/dotnet-tools` użyj polecenia, aby usunąć dostęp.</span><span class="sxs-lookup"><span data-stu-id="bc42a-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="bc42a-107">Uruchamianie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="bc42a-107">Run the global tool</span></span>

<span data-ttu-id="bc42a-108">**Wariant 1** Użyj pełnej ścieżki z sudo:</span><span class="sxs-lookup"><span data-stu-id="bc42a-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="bc42a-109">**Wariant 2** Dodaj link symbolu narzędzia raz na narzędzie:</span><span class="sxs-lookup"><span data-stu-id="bc42a-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="bc42a-110">I uruchomić z:</span><span class="sxs-lookup"><span data-stu-id="bc42a-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="bc42a-111">Odinstalowywanie narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="bc42a-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="bc42a-112">Jeśli nawiązałeś link do symbolu, musisz go usunąć:</span><span class="sxs-lookup"><span data-stu-id="bc42a-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
