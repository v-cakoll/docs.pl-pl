---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540117"
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
