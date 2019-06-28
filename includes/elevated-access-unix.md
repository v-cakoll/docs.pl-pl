---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424708"
---
### <a name="install-the-global-tool"></a><span data-ttu-id="8484a-101">Zainstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="8484a-101">Install the global tool</span></span>

<span data-ttu-id="8484a-102">Zasoby pakietu, powinien być zainstalowany w lokacji chronionej przy użyciu `--tool-path` opcji.</span><span class="sxs-lookup"><span data-stu-id="8484a-102">Package assets should be installed in a protected location using the `--tool-path` option.</span></span> <span data-ttu-id="8484a-103">Ta separacja pozwala uniknąć, udostępnianie środowiska użytkowników z ograniczeniami przy użyciu środowiska o podniesionych uprawnieniach.</span><span class="sxs-lookup"><span data-stu-id="8484a-103">This separation avoids sharing a restricted user environment with an elevated environment.</span></span>

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="8484a-104">`/usr/local/share/dotnet-tools` zostanie utworzona z uprawnieniem `drwxr-xr-x`.</span><span class="sxs-lookup"><span data-stu-id="8484a-104">`/usr/local/share/dotnet-tools` will be created with permission `drwxr-xr-x`.</span></span> <span data-ttu-id="8484a-105">Jeśli katalog już istnieje, użyj `ls -l` polecenie, aby sprawdzić, ograniczeniami użytkownik nie ma uprawnień do edytowania katalogu.</span><span class="sxs-lookup"><span data-stu-id="8484a-105">If the directory already exists, use the `ls -l` command to verify the restricted user doesn't have permission to edit the directory.</span></span> <span data-ttu-id="8484a-106">Jeśli tak, użyj `sudo chmod o-w -R /usr/share/dotnet-tools` polecenie, aby usunąć dostęp.</span><span class="sxs-lookup"><span data-stu-id="8484a-106">If so, use the `sudo chmod o-w -R /usr/share/dotnet-tools` command to remove the access.</span></span>

### <a name="run-the-global-tool"></a><span data-ttu-id="8484a-107">Uruchom narzędzie globalnej</span><span class="sxs-lookup"><span data-stu-id="8484a-107">Run the global tool</span></span>

<span data-ttu-id="8484a-108">**Opcja 1** użycie pełnej ścieżki przy użyciu programu sudo:</span><span class="sxs-lookup"><span data-stu-id="8484a-108">**Option 1** Use the full path with sudo:</span></span>

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

<span data-ttu-id="8484a-109">**Opcja 2** symbol Link do narzędzia, raz na narzędzie:</span><span class="sxs-lookup"><span data-stu-id="8484a-109">**Option 2** Add the symbol link of the tool, once per tool:</span></span>

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

<span data-ttu-id="8484a-110">A następnie uruchom za pomocą:</span><span class="sxs-lookup"><span data-stu-id="8484a-110">And run with:</span></span>

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="8484a-111">Odinstaluj narzędzie globalne</span><span class="sxs-lookup"><span data-stu-id="8484a-111">Uninstall the global tool</span></span>

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

<span data-ttu-id="8484a-112">Jeśli utworzono łącze symboli, należy ją usunąć:</span><span class="sxs-lookup"><span data-stu-id="8484a-112">If you made a symbol link, you also need to remove it:</span></span>

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```