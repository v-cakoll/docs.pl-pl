---
title: Publikowanie aplikacji platformy .NET Core za pomocą interfejsu wiersza polecenia
description: Dowiedz się, jak opublikować aplikację platformy .NET Core przy użyciu narzędzi interfejsu wiersza polecenia zestaw .NET Core SDK (CLI).
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: c8b4c60eb4ea09c8b10bd0b2fffc803d0a5fb6e0
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834279"
---
# <a name="publish-net-core-apps-with-the-cli"></a>Publikowanie aplikacji platformy .NET Core za pomocą interfejsu wiersza polecenia

W tym artykule pokazano, jak można opublikować aplikację .NET Core z poziomu wiersza polecenia. Platforma .NET Core oferuje trzy sposoby publikowania aplikacji. Wdrożenie zależne od platformy tworzy plik DLL dla wielu platform, który używa lokalnie zainstalowanego środowiska uruchomieniowego platformy .NET Core. Plik wykonywalny zależny od struktury tworzy plik wykonywalny specyficzny dla platformy, który używa zainstalowanego lokalnie środowiska uruchomieniowego platformy .NET Core. Samodzielny plik wykonywalny tworzy plik wykonywalny specyficzny dla platformy i zawiera kopię lokalną środowiska uruchomieniowego platformy .NET Core.

Aby zapoznać się z omówieniem tych trybów publikowania, zobacz [wdrażanie aplikacji .NET Core](index.md).

Szukasz jakiejś szybkiej pomocy przy korzystaniu z interfejsu wiersza polecenia? W poniższej tabeli przedstawiono kilka przykładów sposobu publikowania aplikacji. Możesz określić platformę docelową z parametrem `-f <TFM>` lub edytując plik projektu. Aby uzyskać więcej informacji, zobacz temat [Publikowanie podstawowych](#publishing-basics).

| Tryb publikowania | Wersja zestawu SDK | Polecenie |
| ------------ | ----------- | ------- |
| Wdrożenie zależne od platformy | 2.x | `dotnet publish -c Release` |
| Plik wykonywalny zależny od struktury | 2,2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 * | `dotnet publish -c Release` |
| Wdrażanie samodzielne      | 2,1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2,2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\* w przypadku używania zestawu SDK 3,0, zależny od struktury plik wykonywalny jest domyślnym trybem publikowania podczas uruchamiania polecenia Basic `dotnet publish`. Ma to zastosowanie tylko wtedy, gdy projekt jest przeznaczony dla **platformy .net core 2,1** lub **.NET Core 3,0**.

## <a name="publishing-basics"></a>Podstawowe informacje o publikowaniu

Ustawienie `<TargetFramework>` pliku projektu określa domyślną platformę docelową podczas publikowania aplikacji. Można zmienić platformę docelową na dowolną prawidłową [moniker platformy docelowej (TFM)](../../standard/frameworks.md). Na przykład jeśli projekt używa `<TargetFramework>netcoreapp2.2</TargetFramework>`, tworzony jest plik binarny, który jest przeznaczony dla programu .NET Core 2,2. TFM określony w tym ustawieniu jest domyślnym obiektem docelowym używanym przez polecenie [`dotnet publish`](../tools/dotnet-publish.md) .

Jeśli chcesz utworzyć więcej niż jedną strukturę, można ustawić ustawienie `<TargetFrameworks>` na więcej niż jedną wartość TFM oddzieloną średnikami. Jedną z platform można opublikować za pomocą polecenia `dotnet publish -f <TFM>`. Jeśli na przykład masz `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` i uruchomisz `dotnet publish -f netcoreapp2.1`, tworzony jest plik binarny, który jest przeznaczony dla programu .NET Core 2,1.

O ile nie określono inaczej, katalog wyjściowy polecenia [`dotnet publish`](../tools/dotnet-publish.md) jest `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Domyślny tryb **kompilacji — konfiguracja** jest **debugowany** , chyba że zostanie zmieniony przy użyciu parametru `-c`. Na przykład `dotnet publish -c Release -f netcoreapp2.1` publikuje w `myfolder/bin/Release/netcoreapp2.1/publish/`.

Jeśli używasz zestaw .NET Core SDK 3,0, domyślnym trybem publikowania dla aplikacji przeznaczonych dla platformy .NET Core w wersji 2,1, 2,2 lub 3,0 jest plik wykonywalny zależny od platformy.

Jeśli używasz zestaw .NET Core SDK 2,1, domyślnym trybem publikowania dla aplikacji przeznaczonych dla platformy .NET Core w wersji 2,1, 2,2 jest wdrożenie zależne od platformy.

### <a name="native-dependencies"></a>Zależności natywne

Jeśli aplikacja ma natywne zależności, może nie działać w innym systemie operacyjnym. Na przykład jeśli aplikacja używa natywnego interfejsu API systemu Windows, nie będzie działać w systemie macOS lub Linux. Należy dostarczyć kod specyficzny dla platformy i skompilować plik wykonywalny dla każdej platformy.

Należy również wziąć pod uwagę, że jeśli przywoływana Biblioteka ma natywną zależność, aplikacja może nie działać na każdej platformie. Jednak jest możliwe, że odwołanie do pakietu NuGet obejmuje wersje specyficzne dla platformy, które obsługują wymagane natywne zależności.

W przypadku dystrybucji aplikacji z natywnymi zależnościami może być konieczne użycie przełącznika `dotnet publish -r <RID>`, aby określić platformę docelową do opublikowania. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego, zobacz [wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md).

Więcej informacji na temat plików binarnych specyficznych dla platformy znajduje się w [plikach wykonywalnych zależnych od struktury](#framework-dependent-executable) i zawartych w nich sekcjach [wdrożenia](#self-contained-deployment) .

## <a name="sample-app"></a>Przykładowa aplikacja

Aby poznać polecenia publikowania, można użyć następującej aplikacji. Aplikacja zostanie utworzona, uruchamiając następujące polecenia w terminalu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

Plik `Program.cs` lub `Program.vb`, który jest generowany przez szablon konsoli, należy zmienić na następujący:

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

Po uruchomieniu aplikacji ([`dotnet run`](../tools/dotnet-run.md)) wyświetlane są następujące dane wyjściowe:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Wdrożenie zależne od platformy

W przypadku interfejsu wiersza polecenia zestaw .NET Core SDK 2. x wdrożenie zależne od platformy (FDD) jest domyślnym trybem dla poleceniu Basic `dotnet publish`.

Po opublikowaniu aplikacji jako FDD w folderze `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` zostanie utworzony plik `<PROJECT-NAME>.dll`. Aby uruchomić aplikację, przejdź do folderu danych wyjściowych i użyj polecenia `dotnet <PROJECT-NAME>.dll`.

Twoja aplikacja jest skonfigurowana pod kątem określonej wersji platformy .NET Core. Odpowiednie środowisko uruchomieniowe platformy .NET Core musi znajdować się na komputerze, na którym chcesz uruchomić aplikację. Na przykład jeśli aplikacja jest przeznaczona dla platformy .NET Core 2,2, na każdym komputerze, na którym działa aplikacja, musi być zainstalowany program .NET Core 2,2 Runtime. Zgodnie z opisem w sekcji [Informacje o publikowaniu](#publishing-basics) można edytować plik projektu, aby zmienić domyślną platformę docelową lub docelową więcej niż jedną strukturę.

Opublikowanie FDD powoduje utworzenie aplikacji, która automatycznie przeniesie do najnowszej wersji programu .NET Core w systemie, w której działa aplikacja. Aby uzyskać więcej informacji na temat powiązań wersji w czasie kompilacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Plik wykonywalny zależny od struktury

W przypadku interfejsu wiersza polecenia zestaw .NET Core SDK 3. x zależny od platformy plik wykonywalny (całego) jest domyślnym trybem dla poleceń Basic `dotnet publish`. Nie trzeba określać żadnych innych parametrów, o ile chcesz ustawić jako docelowy bieżący system operacyjny.

W tym trybie jest tworzony Host wykonywalny specyficzny dla platformy, który umożliwia hostowanie aplikacji dla wielu platform. Ten tryb jest podobny do FDD, ponieważ FDD wymaga hosta w postaci polecenia `dotnet`. Nazwa pliku wykonywalnego hosta różni się w zależności od platformy i ma nazwę podobną do `<PROJECT-FILE>.exe`. Można uruchomić ten plik wykonywalny bezpośrednio zamiast wywoływania `dotnet <PROJECT-FILE>.dll`, który jest nadal akceptowalnym sposobem uruchamiania aplikacji.

Twoja aplikacja jest skonfigurowana pod kątem określonej wersji platformy .NET Core. Odpowiednie środowisko uruchomieniowe platformy .NET Core musi znajdować się na komputerze, na którym chcesz uruchomić aplikację. Na przykład jeśli aplikacja jest przeznaczona dla platformy .NET Core 2,2, na każdym komputerze, na którym działa aplikacja, musi być zainstalowany program .NET Core 2,2 Runtime. Zgodnie z opisem w sekcji [Informacje o publikowaniu](#publishing-basics) można edytować plik projektu, aby zmienić domyślną platformę docelową lub docelową więcej niż jedną strukturę.

Opublikowanie całego powoduje utworzenie aplikacji, która automatycznie przeniesie do najnowszej wersji programu .NET Core w systemie, w której działa aplikacja. Aby uzyskać więcej informacji na temat powiązań wersji w czasie kompilacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

Musisz (z wyjątkiem programu .NET Core 3. x, gdy jest przeznaczony dla bieżącej platformy), użyj następujących przełączników z `dotnet publish` polecenia, aby opublikować całego:

- `-r <RID>` ten przełącznik używa identyfikatora (RID), aby określić platformę docelową. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego, zobacz [wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md).

- `--self-contained false` ten przełącznik instruuje zestaw .NET Core SDK, aby utworzył plik wykonywalny jako całego.

Za każdym razem, gdy używasz przełącznika `-r`, ścieżka folderu wyjściowego zmieni się na: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Jeśli używasz [przykładowej aplikacji](#sample-app), uruchom `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. To polecenie tworzy następujący plik wykonywalny: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Możesz zmniejszyć łączny rozmiar wdrożenia, włączając **tryb niezmienny globalizacji**. Ten tryb jest przydatny w przypadku aplikacji, które nie są ogólnie obsługiwane i mogą korzystać z Konwencji formatowania, konwencji dotyczących wielkości liter i porównywania ciągów oraz kolejności sortowania [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture). Aby uzyskać więcej informacji o **trybie niezmiennym globalizacji** i sposobie jego włączania, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Wdrażanie samodzielne

Po opublikowaniu wdrożenia samodzielnego (SCD), zestaw .NET Core SDK tworzy plik wykonywalny specyficzny dla platformy. Opublikowanie SCD obejmuje wszystkie wymagane pliki .NET Core do uruchomienia aplikacji, ale nie obejmuje [natywnych zależności programu .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Te zależności muszą być obecne w systemie przed uruchomieniem aplikacji.

Opublikowanie SCD tworzy aplikację, która nie przekazuje do najnowszej dostępnej poprawki zabezpieczeń platformy .NET Core. Aby uzyskać więcej informacji na temat powiązań wersji w czasie kompilacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Aby opublikować SCD, należy użyć następujących przełączników z poleceniem `dotnet publish`:

- `-r <RID>` ten przełącznik używa identyfikatora (RID), aby określić platformę docelową. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego, zobacz [wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md).

- `--self-contained true` ten przełącznik instruuje zestaw .NET Core SDK, aby utworzył plik wykonywalny jako SCD.

> [!NOTE]
> Możesz zmniejszyć łączny rozmiar wdrożenia, włączając **tryb niezmienny globalizacji**. Ten tryb jest przydatny w przypadku aplikacji, które nie są ogólnie obsługiwane i mogą korzystać z Konwencji formatowania, konwencji dotyczących wielkości liter i porównywania ciągów oraz kolejności sortowania [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture). Aby uzyskać więcej informacji o **trybie niezmiennym globalizacji** i sposobie jego włączania, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

## <a name="see-also"></a>Zobacz także

- [Omówienie wdrażania aplikacji .NET Core](index.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
