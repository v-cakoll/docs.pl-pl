---
title: Publikowanie .NET Core z aplikacji przy użyciu interfejsu wiersza polecenia
description: Dowiedz się opublikować aplikację platformy .NET Core za pomocą narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core SDK.
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: a72e5e557cd3aa098b674bffd277e3cc6da99d33
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663228"
---
# <a name="publish-net-core-apps-with-the-cli"></a>Publikowanie .NET Core z aplikacji przy użyciu interfejsu wiersza polecenia

W tym artykule przedstawiono, jak opublikować aplikację .NET Core z poziomu wiersza polecenia. .NET core udostępnia trzy sposoby na publikowanie własnych aplikacji. Wdrożenie zależny od struktury tworzy plik .dll dla wielu platform, który używa zainstalowane lokalnie środowisko uruchomieniowe platformy .NET Core. Plik wykonywalny zależny od struktury tworzy specyficzne dla platformy plik wykonywalny, który używa zainstalowane lokalnie środowisko uruchomieniowe platformy .NET Core. Plik wykonywalny niezależna tworzy wykonywalnej specyficzne dla platformy i obejmuje lokalną kopię środowisko uruchomieniowe platformy .NET Core.

Omówienie tych trybów publikowania, zobacz [wdrożenie aplikacji programu .NET Core](index.md).

Szukasz szybkiego pomocy przy użyciu interfejsu wiersza polecenia? W poniższej tabeli przedstawiono kilka przykładów sposobu publikowania aplikacji. Można określić platformę docelową z `-f <TFM>` parametru lub przez edycję pliku projektu. Aby uzyskać więcej informacji, zobacz [publikowania podstawy](#publishing-basics).

| Tryb publikowania | Wersja zestawu SDK | Polecenie |
| ------------ | ----------- | ------- |
| Wdrożenie zależny od struktury | 2.x | `dotnet publish -c Release` |
| Plik wykonywalny zależny od struktury | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Niezależne wdrożenia      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\* Korzystając z zestawu SDK w wersji 3.0 lub nowszej, plik wykonywalny zależny od struktury jest to domyślny tryb publikowania, podczas uruchamiania podstawowego `dotnet publish` polecenia. To tylko wtedy, gdy projekt jest przeznaczony dla jednej **platformy .NET Core 2.1** lub **.NET Core 3.0 to**.

## <a name="publishing-basics"></a>Podstawy publikowania

`<TargetFramework>` Ustawienie pliku projektu określa platformę docelową domyślne podczas publikowania aplikacji. Możesz zmienić platformę docelową na dowolne, prawidłowe [Moniker Framework docelowych (TFM)](../../standard/frameworks.md). Na przykład, jeśli projekt używa `<TargetFramework>netcoreapp2.2</TargetFramework>`, zostanie utworzony plik binarny, który jest przeznaczony dla platformy .NET Core 2.2. TFM określone w tym ustawieniu jest używany przez domyślny element docelowy [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.

Jeśli chcesz przeanalizować więcej niż jednej struktury, możesz ustawić `<TargetFrameworks>` ustawienie do więcej niż jednego elementu TFM wartości, rozdzielając je średnikiem. Możesz opublikować jedną z platform z `dotnet publish -f <TFM>` polecenia. Na przykład, jeśli masz `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` i uruchom `dotnet publish -f netcoreapp2.1`, zostanie utworzony plik binarny, który jest przeznaczony dla platformy .NET Core 2.1.

Chyba że inaczej ustawiony, katalog wyjściowy [ `dotnet publish` ](../tools/dotnet-publish.md) polecenie jest `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Wartość domyślna **konfigurację kompilacji** tryb jest **debugowania** , chyba że zmieniono za pomocą `-c` parametru. Na przykład `dotnet publish -c Release -f netcoreapp2.1` publikuje `myfolder/bin/Release/netcoreapp2.1/publish/`.

Jeśli używasz platformy .NET Core SDK 3.0, domyślnie opublikować tryb dla aplikacji, czy docelowej platformy .NET Core w wersji 2.1, 2.2 lub 3.0 jest zależny od struktury pliku wykonywalnego.

Jeśli używasz platformy .NET Core SDK 2.1, domyślnie opublikować tryb dla wersji docelowej platformy .NET Core 2.1, 2.2 to wdrożenie zależny od struktury aplikacji.

### <a name="native-dependencies"></a>Natywne zależności

Jeśli aplikacja ma zależności natywnych, może nie działać w innym systemie operacyjnym. Na przykład jeśli aplikacja używa natywnego interfejsu API Windows, nie będzie uruchomić w systemie macOS lub Linux. Będzie konieczne podanie kodu specyficznego dla platformy i skompiluj plik wykonywalny dla każdej platformy.

Rozważ również, jeśli biblioteka odwołaniu ma zależności natywnych, aplikacja może nie działać na każdej platformie. Jednak jest możliwe, pakietu NuGet, który jest odwołanie do pakietu wersji specyficzne dla platformy do obsługi wymaganych zależności natywnych dla Ciebie.

Podczas dystrybucji aplikacji za pomocą natywnego zależności, może być konieczne użycie `dotnet publish -r <RID>` platformy docelowej, który chcesz opublikować dla przełącznika. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych, zobacz [katalog identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md).

Więcej informacji na temat pliki binarne specyficzne dla platformy są omówione w [zależny od struktury pliku wykonywalnego](#framework-dependent-executable) i [niezależna wdrożenia](#self-contained-deployment) sekcje.

## <a name="sample-app"></a>Przykładowa aplikacja

Eksplorowanie publikowania poleceń, można użyć następującej aplikacji. Aplikacja zostanie utworzona, uruchamiając następujące polecenia w terminalu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

`Program.cs` Lub `Program.vb` pliku, który jest generowany przez szablon konsoli musi być zmieniony na następujący:

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Po uruchomieniu aplikacji ([`dotnet run`](../tools/dotnet-run.md)), zostaną wyświetlone następujące dane wyjściowe:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Wdrożenie zależny od struktury

Dla zestawu .NET Core SDK 2.x interfejsu wiersza polecenia deployment zależny od struktury (stacje) jest to domyślny tryb dla podstawowego `dotnet publish` polecenia.

Po opublikowaniu aplikacji zgodnie z stacje `<PROJECT-NAME>.dll` plik zostanie utworzony w `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` folderu. Aby uruchomić aplikację, przejdź do folderu wyjściowego i użyj `dotnet <PROJECT-NAME>.dll` polecenia.

Aplikacja jest skonfigurowana pod kątem określonej wersji programu .NET Core. Docelowych .NET Core środowiska uruchomieniowego musi być na komputerze, na którym chcesz uruchomić aplikację. Na przykład jeśli aplikacja jest przeznaczony dla platformy .NET Core 2.2, dowolnym komputerze, który aplikacja działa w systemie musi mieć zainstalowanego środowiska uruchomieniowego platformy .NET Core 2.2. Jak wspomniano w [publikowania podstawy](#publishing-basics) sekcji można edytować plik projektu, aby zmienić platformę docelową domyślne lub pod kątem więcej niż jednej struktury.

Publikowanie z stacje tworzy aplikację, automatycznie ustala przekazywania dalej na najnowsze platformy .NET Core poprawki zabezpieczeń do dostępnej w systemie, który uruchamia aplikację. Aby uzyskać więcej informacji na temat wersji powiązania w czasie kompilacji, zobacz [wybierz wersję platformy .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Plik wykonywalny zależny od struktury

Dla zestawu .NET Core SDK 3.x interfejsu wiersza polecenia, zależny od struktury plik wykonywalny (FDE) to domyślny tryb podstawowy `dotnet publish` polecenia. Nie trzeba określić innych parametrów, tak długo, jak długo ma pod kątem bieżącego systemu operacyjnego.

W tym trybie hosta do pliku wykonywalnego specyficzne dla platformy jest tworzony do hostowania aplikacji dla wielu platform. Ten tryb jest podobny do Dyskietki, zgodnie z stacje wymaga hosta w formie `dotnet` polecenia. Nazwa pliku wykonywalnego hosta różni się dla danej platformy i nazwana w sposób podobny do `<PROJECT-FILE>.exe`. Możesz uruchomić plik wykonywalny bezpośrednio bez wywoływania `dotnet <PROJECT-FILE>.dll` która nadal jest akceptowany sposób, aby uruchomić aplikację.

Aplikacja jest skonfigurowana pod kątem określonej wersji programu .NET Core. Docelowych .NET Core środowiska uruchomieniowego musi być na komputerze, na którym chcesz uruchomić aplikację. Na przykład jeśli aplikacja jest przeznaczony dla platformy .NET Core 2.2, dowolnym komputerze, który aplikacja działa w systemie musi mieć zainstalowanego środowiska uruchomieniowego platformy .NET Core 2.2. Jak wspomniano w [publikowania podstawy](#publishing-basics) sekcji można edytować plik projektu, aby zmienić platformę docelową domyślne lub pod kątem więcej niż jednej struktury.

Publikowanie FDE tworzy aplikację, automatycznie ustala przekazywania dalej na najnowsze platformy .NET Core poprawki zabezpieczeń do dostępnej w systemie, który uruchamia aplikację. Aby uzyskać więcej informacji na temat wersji powiązania w czasie kompilacji, zobacz [wybierz wersję platformy .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

Należy najpierw (z wyjątkiem platformy .NET Core 3.x, gdy miejscem docelowym bieżącej platformie) Użyj następujących przełączników z `dotnet publish` polecenie w celu opublikowania FDE:

- `-r <RID>` Ten przełącznik używa identyfikatora (RID) w celu określenia platformy docelowej. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych, zobacz [katalog identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md).

- `--self-contained false` Ten przełącznik informuje zestawu .NET Core SDK, aby utworzyć plik wykonywalny jako FDE.

Zawsze, gdy używasz `-r` przełącznika, ścieżka folderu danych wyjściowych zmieni się na: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Jeśli używasz [Przykładowa aplikacja](#sample-app)Uruchom `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. To polecenie tworzy następujące pliku wykonywalnego: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Można zmniejszyć całkowity rozmiar wdrożenia, włączając **globalizacji niezmiennej tryb**. Ten tryb jest przydatne w przypadku aplikacji, które nie są wspierane i mogą używać konwencji formatowania Konwencji obudowy i ciąg porównywania i sortowania kolejności [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture). Aby uzyskać więcej informacji na temat **globalizacji niezmiennej tryb** i jak go włączyć, zobacz [trybie niezmiennej globalizacji platformy .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Niezależne wdrożenia

Podczas publikowania niezależna wdrożenia (— SCD), .NET Core SDK tworzy wykonywalnej specyficzne dla platformy. Publikowanie — SCD zawiera wszystkie wymagane pliki platformy .NET Core, aby uruchomić aplikację, ale nie zawiera [natywnych zależności platformy .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Te zależności musi znajdować się w systemie przed uruchomieniem aplikacji.

Publikowanie — SCD tworzy aplikację, która nie przodu do najnowszych dostępnych platformy .NET Core poprawki zabezpieczeń. Aby uzyskać więcej informacji na temat wersji powiązania w czasie kompilacji, zobacz [wybierz wersję platformy .NET Core do użycia](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Należy użyć następujących przełączników z `dotnet publish` polecenie w celu opublikowania — SCD:

- `-r <RID>` Ten przełącznik używa identyfikatora (RID) w celu określenia platformy docelowej. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych, zobacz [katalog identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md).

- `--self-contained true` Ten przełącznik informuje zestawu .NET Core SDK, aby utworzyć plik wykonywalny jako — SCD.

> [!NOTE]
> Można zmniejszyć całkowity rozmiar wdrożenia, włączając **globalizacji niezmiennej tryb**. Ten tryb jest przydatne w przypadku aplikacji, które nie są wspierane i mogą używać konwencji formatowania Konwencji obudowy i ciąg porównywania i sortowania kolejności [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture). Aby uzyskać więcej informacji na temat **globalizacji niezmiennej tryb** i jak go włączyć, zobacz [trybie niezmiennej globalizacji platformy .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="see-also"></a>Zobacz także

- [Przegląd wdrażania aplikacji programu .NET core](index.md)
- [Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)](../rid-catalog.md)
