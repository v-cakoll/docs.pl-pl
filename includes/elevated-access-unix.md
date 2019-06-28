---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424708"
---
### <a name="install-the-global-tool"></a>Zainstaluj narzędzie globalne

Zasoby pakietu, powinien być zainstalowany w lokacji chronionej przy użyciu `--tool-path` opcji. Ta separacja pozwala uniknąć, udostępnianie środowiska użytkowników z ograniczeniami przy użyciu środowiska o podniesionych uprawnieniach.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools` zostanie utworzona z uprawnieniem `drwxr-xr-x`. Jeśli katalog już istnieje, użyj `ls -l` polecenie, aby sprawdzić, ograniczeniami użytkownik nie ma uprawnień do edytowania katalogu. Jeśli tak, użyj `sudo chmod o-w -R /usr/share/dotnet-tools` polecenie, aby usunąć dostęp.

### <a name="run-the-global-tool"></a>Uruchom narzędzie globalnej

**Opcja 1** użycie pełnej ścieżki przy użyciu programu sudo:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Opcja 2** symbol Link do narzędzia, raz na narzędzie:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

A następnie uruchom za pomocą:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstaluj narzędzie globalne

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Jeśli utworzono łącze symboli, należy ją usunąć:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```