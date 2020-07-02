---
title: Instalowanie platformy .NET Core na platformie Alpine-.NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core na platformie Alpine.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 0efe3bbacbe573b77eae8818ea29b5a3867e4570
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619523"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a>Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core na platformie Alpine

W tym artykule opisano sposób instalowania programu .NET Core w witrynie Alpine. Gdy wersja Alpine nie jest objęta pomocą techniczną, program .NET Core nie jest już obsługiwany w tej wersji. Te instrukcje mogą jednak ułatwić uzyskanie programu .NET Core działającego w tych wersjach, chociaż nie jest to obsługiwane.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

Brak instalatorów dla Alpine. Musisz użyć [skryptu instalacji](#scripted-install) lub instrukcji [instalacji ręcznej](#manual-install) .

## <a name="supported-distributions"></a>Obsługiwane dystrybucje

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core i wersje Alpine, w których są obsługiwane. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Alp osiągnie koniec cyklu życia](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- ✔️ wskazuje, że wersja Alpine lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja Alpine lub .NET Core nie jest obsługiwana w tej wersji Alpine.
- Gdy wersja Alpine i wersja platformy .NET Core ma ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| Alpine                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) |
|--------------------------|---------------|---------------|----------------|
| ✔️ 3,12  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ 3,11  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ 3,10  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ 3,9   | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌3,8   | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |

Następujące wersje programu .NET Core nie są już obsługiwane. Pliki do pobrania dla tych nadal są publikowane:

- 3.0
- 2.2
- 2.0

## <a name="dependencies"></a>Zależności

Platforma .NET Core w systemie Alpine Linux wymaga zainstalowanych następujących zależności:

- ICU — libs
- krb5 — libs
- libgcc
- libintl
- libssl 1.1 (Alpine v lub nowszy)
- libssl 1.0 (Alpine v 3.8 lub Lower)
- libstdc + +
- zlib

## <a name="scripted-install"></a>Instalacja z skryptami

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalacja ręczna

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Następne kroki

- [Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md)
