---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540117"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="1c5a9-101">Zainstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="1c5a9-101">Install the global tool</span></span>

<span data-ttu-id="1c5a9-102">Zasoby pakietu, powinien być zainstalowany w lokacji chronionej przy użyciu `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="1c5a9-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="1c5a9-103">Ta separacja pozwala uniknąć, udostępnianie środowiska użytkowników z ograniczeniami przy użyciu środowiska o podniesionych uprawnieniach.</span><span class="sxs-lookup"><span data-stu-id="1c5a9-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="1c5a9-104">`/usr/local/share/dotnet-tools` zostanie utworzona z uprawnieniem `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="1c5a9-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="1c5a9-105">Jeśli katalog już istnieje, użyj `ls -l` polecenie, aby sprawdzić, ograniczeniami użytkownik nie ma uprawnień do edytowania katalogu.</span><span class="sxs-lookup"><span data-stu-id="1c5a9-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="1c5a9-106">Jeśli tak, użyj `sudo chmod o-w -R /usr/share/dotnet-tools` polecenie, aby usunąć dostęp.</span><span class="sxs-lookup"><span data-stu-id="1c5a9-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="1c5a9-107">Uruchom narzędzie globalnej</span><span class="sxs-lookup"><span data-stu-id="1c5a9-107">Run the global tool</span></span>

<span data-ttu-id="1c5a9-108">**Opcja 1** użycie pełnej ścieżki przy użyciu programu sudo:</span><span class="sxs-lookup"><span data-stu-id="1c5a9-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="1c5a9-109">**Opcja 2** symbol Link do narzędzia, raz na narzędzie:</span><span class="sxs-lookup"><span data-stu-id="1c5a9-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="1c5a9-110">A następnie uruchom za pomocą:</span><span class="sxs-lookup"><span data-stu-id="1c5a9-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="1c5a9-111">Odinstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="1c5a9-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="1c5a9-112">Jeśli utworzono łącze symboli, należy ją usunąć:</span><span class="sxs-lookup"><span data-stu-id="1c5a9-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
