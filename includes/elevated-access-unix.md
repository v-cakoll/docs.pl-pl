---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "67540117"
---
### <a name="install-the-global-tool"></a>Instalowanie narzędzia globalnego

Zasoby pakietu powinny być instalowane w chronionej lokalizacji przy użyciu `--tool-path` tej opcji. Ta separacja pozwala uniknąć udostępniania ograniczonego środowiska użytkownika z podwyższonym poziomem ochrony środowiska.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools`zostanie utworzony za `drwxr-xr-x`zgodą . Jeśli katalog już istnieje, `ls -l` użyj polecenia, aby sprawdzić, czy użytkownik z ograniczeniami nie ma uprawnień do edytowania katalogu. Jeśli tak, `sudo chmod o-w -R /usr/share/dotnet-tools` użyj polecenia, aby usunąć dostęp.

### <a name="run-the-global-tool"></a>Uruchamianie narzędzia globalnego

**Wariant 1** Użyj pełnej ścieżki z sudo:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Wariant 2** Dodaj link symbolu narzędzia raz na narzędzie:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

I uruchomić z:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalowywanie narzędzia globalnego

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Jeśli nawiązałeś link do symbolu, musisz go usunąć:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
