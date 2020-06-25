---
title: Publikowanie aplikacji przy użyciu interfejs wiersza polecenia platformy .NET Core
description: Dowiedz się, jak opublikować aplikację platformy .NET Core za pomocą poleceń interfejs wiersza polecenia platformy .NET Core.
author: adegeo
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: a592b397d1ffee5b224638a8d17ce6fa9e44eea2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325025"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a>Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core

W tym artykule pokazano, jak można opublikować aplikację .NET Core z poziomu wiersza polecenia. Platforma .NET Core oferuje trzy sposoby publikowania aplikacji. Wdrożenie zależne od platformy tworzy plik DLL dla wielu platform, który używa lokalnie zainstalowanego środowiska uruchomieniowego platformy .NET Core. Plik wykonywalny zależny od struktury tworzy plik wykonywalny specyficzny dla platformy, który używa zainstalowanego lokalnie środowiska uruchomieniowego platformy .NET Core. Samodzielny plik wykonywalny tworzy plik wykonywalny specyficzny dla platformy i zawiera kopię lokalną środowiska uruchomieniowego platformy .NET Core.

Aby zapoznać się z omówieniem tych trybów publikowania, zobacz [wdrażanie aplikacji .NET Core](index.md).

Szukasz jakiejś szybkiej pomocy przy korzystaniu z interfejsu wiersza polecenia? W poniższej tabeli przedstawiono kilka przykładów sposobu publikowania aplikacji. Możesz określić platformę docelową z `-f <TFM>` parametrem lub edytując plik projektu. Aby uzyskać więcej informacji, zobacz temat [Publikowanie podstawowych](#publishing-basics).

| Tryb publikowania | Wersja zestawu SDK | Polecenie |
| ------------ | ----------- | ------- |
| Wdrożenie zależne od platformy | 2.x | `dotnet publish -c Release` |
| Plik wykonywalny zależny od struktury | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 * | `dotnet publish -c Release` |
| Wdrażanie samodzielne      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\*W przypadku korzystania z zestawu SDK w wersji 3,0, zależny od platformy plik wykonywalny jest domyślnym trybem publikowania podczas uruchamiania `dotnet publish` polecenia Basic. Ma to zastosowanie tylko wtedy, gdy projekt jest przeznaczony dla **platformy .net core 2,1** lub **.NET Core 3,0**.

## <a name="publishing-basics"></a>Podstawowe informacje o publikowaniu

`<TargetFramework>`Ustawienie pliku projektu określa domyślną platformę docelową podczas publikowania aplikacji. Można zmienić platformę docelową na dowolną prawidłową [moniker platformy docelowej (TFM)](../../standard/frameworks.md). Na przykład, jeśli używany jest projekt `<TargetFramework>netcoreapp2.2</TargetFramework>` , tworzony jest plik binarny, który jest przeznaczony dla programu .NET Core 2,2. TFM określony w tym ustawieniu jest domyślnym obiektem docelowym używanym przez [`dotnet publish`](../tools/dotnet-publish.md) polecenie.

Jeśli chcesz utworzyć więcej niż jedną strukturę, można ustawić `<TargetFrameworks>` na więcej niż jedną wartość TFM oddzieloną średnikami. Jedną z platform można opublikować za pomocą `dotnet publish -f <TFM>` polecenia. Na przykład jeśli masz `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` i uruchomisz `dotnet publish -f netcoreapp2.1` , tworzony jest plik binarny przeznaczony dla programu .net Core 2,1.

O ile nie określono inaczej, katalog wyjściowy [`dotnet publish`](../tools/dotnet-publish.md) polecenia jest `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` . Domyślny tryb **kompilacji — konfiguracja** jest **debugowany** , chyba że zostanie zmieniony przy użyciu `-c` parametru. Na przykład program `dotnet publish -c Release -f netcoreapp2.1` publikuje w usłudze `myfolder/bin/Release/netcoreapp2.1/publish/` .

Jeśli używasz zestaw .NET Core SDK 3,0 lub nowszej, domyślnym trybem publikowania dla aplikacji przeznaczonych dla platformy .NET Core w wersji 2,1, 2,2, 3,0 lub nowszej wersji jest plik wykonywalny zależny od struktury.

Jeśli używasz zestaw .NET Core SDK 2,1, domyślnym trybem publikowania dla aplikacji przeznaczonych dla platformy .NET Core w wersji 2,1 i 2,2 jest wdrożenie zależne od platformy.

### <a name="native-dependencies"></a>Zależności natywne

Jeśli aplikacja ma natywne zależności, może nie działać w innym systemie operacyjnym. Na przykład jeśli aplikacja używa natywnego interfejsu API systemu Windows, nie będzie działać w systemie macOS lub Linux. Należy dostarczyć kod specyficzny dla platformy i skompilować plik wykonywalny dla każdej platformy.

Należy również wziąć pod uwagę, że jeśli przywoływana Biblioteka ma natywną zależność, aplikacja może nie działać na każdej platformie. Jednak jest możliwe, że odwołanie do pakietu NuGet obejmuje wersje specyficzne dla platformy, które obsługują wymagane natywne zależności.

W przypadku dystrybucji aplikacji z natywnymi zależnościami może być konieczne użycie `dotnet publish -r <RID>` przełącznika, aby określić platformę docelową do opublikowania. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego, zobacz [wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md).

Więcej informacji na temat plików binarnych specyficznych dla platformy znajduje się w [plikach wykonywalnych zależnych od struktury](#framework-dependent-executable) i zawartych w nich sekcjach [wdrożenia](#self-contained-deployment) .

## <a name="sample-app"></a>Przykładowa aplikacja

Aby poznać polecenia publikowania, można użyć następującej aplikacji. Aplikacja zostanie utworzona, uruchamiając następujące polecenia w terminalu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

`Program.cs`Plik lub `Program.vb` generowany przez szablon konsoli należy zmienić na następujący:

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
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Po uruchomieniu aplikacji ( [`dotnet run`](../tools/dotnet-run.md) ) wyświetlane są następujące dane wyjściowe:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Wdrożenie zależne od platformy

W przypadku interfejsu wiersza polecenia zestaw .NET Core SDK 2. x wdrożenie zależne od platformy (FDD) jest domyślnym trybem dla podstawowe `dotnet publish` polecenie.

Po opublikowaniu aplikacji jako FDD `<PROJECT-NAME>.dll` plik zostanie utworzony w `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` folderze. Aby uruchomić aplikację, przejdź do folderu danych wyjściowych i Użyj `dotnet <PROJECT-NAME>.dll` polecenia.

Twoja aplikacja jest skonfigurowana pod kątem określonej wersji platformy .NET Core. Odpowiednie środowisko uruchomieniowe platformy .NET Core musi znajdować się na dowolnym komputerze, na którym działa aplikacja. Na przykład jeśli aplikacja jest przeznaczona dla platformy .NET Core 2,2, na każdym komputerze, na którym działa aplikacja, musi być zainstalowany program .NET Core 2,2 Runtime. Zgodnie z opisem w sekcji [Informacje o publikowaniu](#publishing-basics) można edytować plik projektu, aby zmienić domyślną platformę docelową lub docelową więcej niż jedną strukturę.

Opublikowanie FDD powoduje utworzenie aplikacji, która automatycznie przeniesie do najnowszej wersji programu .NET Core w systemie, w której działa aplikacja. Aby uzyskać więcej informacji na temat powiązań wersji w czasie kompilacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Plik wykonywalny zależny od struktury

W przypadku interfejsu wiersza polecenia zestaw .NET Core SDK 3. x zależny od platformy plik wykonywalny (całego) jest domyślnym trybem dla podstawowych `dotnet publish` poleceń. Nie trzeba określać żadnych innych parametrów, o ile chcesz ustawić jako docelowy bieżący system operacyjny.

W tym trybie jest tworzony Host wykonywalny specyficzny dla platformy, który umożliwia hostowanie aplikacji dla wielu platform. Ten tryb jest podobny do FDD, ponieważ FDD wymaga hosta w postaci `dotnet` polecenia. Nazwa pliku wykonywalnego hosta różni się w zależności od platformy i nazywa się coś podobnego do `<PROJECT-FILE>.exe` . Można uruchomić ten plik wykonywalny bezpośrednio zamiast wywoływania `dotnet <PROJECT-FILE>.dll` , co jest nadal akceptowalnym sposobem uruchomienia aplikacji.

Twoja aplikacja jest skonfigurowana pod kątem określonej wersji platformy .NET Core. Odpowiednie środowisko uruchomieniowe platformy .NET Core musi znajdować się na dowolnym komputerze, na którym działa aplikacja. Na przykład jeśli aplikacja jest przeznaczona dla platformy .NET Core 2,2, na każdym komputerze, na którym działa aplikacja, musi być zainstalowany program .NET Core 2,2 Runtime. Zgodnie z opisem w sekcji [Informacje o publikowaniu](#publishing-basics) można edytować plik projektu, aby zmienić domyślną platformę docelową lub docelową więcej niż jedną strukturę.

Opublikowanie całego powoduje utworzenie aplikacji, która automatycznie przeniesie do najnowszej wersji programu .NET Core w systemie, w której działa aplikacja. Aby uzyskać więcej informacji na temat powiązań wersji w czasie kompilacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

W przypadku platformy .NET Core 2,2 i starszych należy użyć następujących przełączników z `dotnet publish` poleceniem, aby OPUBLIKOWAĆ całego:

- `-r <RID>`Ten przełącznik używa identyfikatora (RID), aby określić platformę docelową. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego, zobacz [wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md).

- `--self-contained false`Ten przełącznik instruuje zestaw .NET Core SDK, aby utworzył plik wykonywalny jako całego.

Za każdym razem, gdy używasz `-r` przełącznika, ścieżka folderu wyjściowego zmieni się na:`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Jeśli używasz [przykładowej aplikacji](#sample-app), uruchom polecenie `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false` . To polecenie tworzy następujący plik wykonywalny:`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Możesz zmniejszyć łączny rozmiar wdrożenia, włączając **tryb niezmienny globalizacji**. Ten tryb jest przydatny w przypadku aplikacji, które nie są ogólnie obsługiwane i mogą korzystać z Konwencji formatowania, konwencji dotyczących wielkości liter i porównywania ciągów oraz kolejności sortowania [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture). Aby uzyskać więcej informacji o **trybie niezmiennym globalizacji** i sposobie jego włączania, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Wdrażanie samodzielne

Po opublikowaniu wdrożenia samodzielnego (SCD), zestaw .NET Core SDK tworzy plik wykonywalny specyficzny dla platformy. Opublikowanie SCD obejmuje wszystkie wymagane pliki .NET Core do uruchomienia aplikacji, ale nie obejmuje [natywnych zależności programu .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Te zależności muszą być obecne w systemie przed uruchomieniem aplikacji.

Opublikowanie elementu SCD powoduje utworzenie aplikacji, która nie przekazuje do najnowszej dostępnej poprawki zabezpieczeń platformy .NET Core. Aby uzyskać więcej informacji na temat powiązań wersji w czasie kompilacji, zobacz [Wybieranie wersji platformy .NET Core do użycia](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Aby opublikować SCD, należy użyć następujących przełączników `dotnet publish` :

- `-r <RID>`Ten przełącznik używa identyfikatora (RID), aby określić platformę docelową. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego, zobacz [wykaz identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md).

- `--self-contained true`Ten przełącznik instruuje zestaw .NET Core SDK, aby utworzył plik wykonywalny jako SCD.

> [!NOTE]
> Możesz zmniejszyć łączny rozmiar wdrożenia, włączając **tryb niezmienny globalizacji**. Ten tryb jest przydatny w przypadku aplikacji, które nie są ogólnie obsługiwane i mogą korzystać z Konwencji formatowania, konwencji dotyczących wielkości liter i porównywania ciągów oraz kolejności sortowania [niezmiennej kultury](xref:System.Globalization.CultureInfo.InvariantCulture). Aby uzyskać więcej informacji o **trybie niezmiennym globalizacji** i sposobie jego włączania, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

## <a name="see-also"></a>Zobacz też

- [Omówienie wdrażania aplikacji .NET Core](index.md)
- [Wykaz identyfikatorów środowiska uruchomieniowego platformy .NET Core (RID)](../rid-catalog.md)
