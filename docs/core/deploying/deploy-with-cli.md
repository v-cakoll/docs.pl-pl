---
title: Publikowanie aplikacji za pomocą wiersza wiersza wiersza wiersza wiersza i sprzedaży .NET Core
description: Dowiedz się, jak opublikować aplikację .NET Core przy użyciu poleceń wiersza polecenia .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f4c2a4ccf551c53e4aa4e125cb5720d6f1cc9601
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399071"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a>Publikowanie aplikacji .NET Core za pomocą wiersza wiersza wiersza wiersza wiersza .NET Core

W tym artykule pokazano, jak można opublikować aplikację .NET Core z wiersza polecenia. .NET Core udostępnia trzy sposoby publikowania aplikacji. Wdrożenie zależne od struktury tworzy wieloplatformowy plik dll, który używa lokalnie zainstalowanego programu .NET Core. Plik wykonywalny zależny od struktury tworzy plik wykonywalny specyficzny dla platformy, który używa lokalnie zainstalowanego programu wykonawczego .NET Core. Samodzielny plik wykonywalny tworzy plik wykonywalny specyficzny dla platformy i zawiera lokalną kopię programu wykonawczego .NET Core.

Aby zapoznać się z omówieniem tych trybów publikowania, zobacz [.NET Core Application Deployment](index.md).

Szukasz szybkiej pomocy na temat korzystania z cli? W poniższej tabeli przedstawiono kilka przykładów publikowania aplikacji. Można określić platformę docelową za pomocą parametru `-f <TFM>` lub edytując plik projektu. Aby uzyskać więcej informacji, zobacz [Publikowanie podstaw](#publishing-basics).

| Tryb publikowania | Wersja zestawu SDK | Polecenie |
| ------------ | ----------- | ------- |
| Wdrożenie zależne od struktury | 2.x | `dotnet publish -c Release` |
| Plik wykonywalny zależny od struktury | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Samodzielne wdrażanie      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\*W przypadku korzystania z pakietu SDK w wersji 3.0 plik `dotnet publish` wykonywalny zależny od struktury jest domyślnym trybem publikowania podczas uruchamiania polecenia podstawowego. Dotyczy to tylko wtedy, gdy projekt jest przeznaczony dla **.NET Core 2.1** lub **.NET Core 3.0**.

## <a name="publishing-basics"></a>Podstawowe informacje o publikowaniu

Ustawienie `<TargetFramework>` pliku projektu określa domyślną strukturę docelową podczas publikowania aplikacji. Można zmienić platformę docelową na dowolną [prawidłową moniker framework target (TFM)](../../standard/frameworks.md). Na przykład jeśli projekt `<TargetFramework>netcoreapp2.2</TargetFramework>`używa , plik binarny, który jest przeznaczony dla .NET Core 2.2 jest tworzony. TFM określony w tym ustawieniu jest domyślnym obiektem docelowym używanym [`dotnet publish`](../tools/dotnet-publish.md) przez polecenie.

Jeśli chcesz kierować więcej niż jedną strukturę, można ustawić `<TargetFrameworks>` ustawienie na więcej niż jedną wartość TFM oddzielone średnikiem. Można opublikować jedną z platform `dotnet publish -f <TFM>` za pomocą polecenia. Na przykład, jeśli `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` masz `dotnet publish -f netcoreapp2.1`i uruchomisz, tworzony jest plik binarny przeznaczony dla .NET Core 2.1.

O ile nie ustalono inaczej, [`dotnet publish`](../tools/dotnet-publish.md) katalog `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`wyjściowy polecenia to . Domyślnym trybem **BUILD-CONFIGURATION** jest **Debug,** chyba że zmieniono go z parametrem. `-c` Na przykład `dotnet publish -c Release -f netcoreapp2.1` publikuje `myfolder/bin/Release/netcoreapp2.1/publish/`do .

Jeśli używasz .NET Core SDK 3.0 lub nowszego, domyślny tryb publikowania dla aplikacji docelowych .NET Core w wersjach 2.1, 2.2, 3.0 lub nowszej wersji jest zależny od struktury.

Jeśli używasz .NET Core SDK 2.1, domyślny tryb publikowania dla aplikacji, które są przeznaczone dla .NET Core w wersjach 2.1 i 2.2 jest wdrożenie zależne od struktury.

### <a name="native-dependencies"></a>Zależności macierzyste

Jeśli aplikacja ma zależności macierzyste, może nie działać w innym systemie operacyjnym. Jeśli na przykład aplikacja korzysta z natywnego interfejsu API systemu Windows, nie będzie działać w systemie macOS ani Linux. Należy podać kod specyficzne dla platformy i skompilować plik wykonywalny dla każdej platformy.

Należy również wziąć pod uwagę, jeśli biblioteka, do której odwołujesz się, ma zależność natywną, aplikacja może nie działać na każdej platformie. Jednak jest możliwe, pakiet NuGet, do którego odwołujesz się zawiera wersje specyficzne dla platformy do obsługi wymaganych zależności macierzystych dla Ciebie.

Podczas dystrybucji aplikacji z natywnych zależności, `dotnet publish -r <RID>` może być konieczne użycie przełącznika, aby określić platformę docelową, które mają zostać opublikowane dla. Aby uzyskać listę identyfikatorów czasu wykonywania, zobacz [Katalog identyfikatorów ustawień wykonywania (RID).](../rid-catalog.md)

Więcej informacji na temat plików binarnych specyficznych dla platformy jest omówione w sekcjach [wykonawczych](#self-contained-deployment) i wdrażania [zależnych od struktury.](#framework-dependent-executable)

## <a name="sample-app"></a>Przykładowa aplikacja

Za pomocą następującej aplikacji można eksplorować polecenia publikowania. Aplikacja jest tworzona przez uruchomienie następujących poleceń w terminalu:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

Plik `Program.cs` `Program.vb` lub plik wygenerowany przez szablon konsoli musi zostać zmieniony na następujący:

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

Po uruchomieniu aplikacji[`dotnet run`](../tools/dotnet-run.md)( ) wyświetlane są następujące dane wyjściowe:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Wdrożenie zależne od struktury

W przypadku polecenia CLI .NET Core 2.x wdrożenie zależne od struktury (FDD) jest domyślnym trybem dla polecenia podstawowego. `dotnet publish`

Podczas publikowania aplikacji jako `<PROJECT-NAME>.dll` FDD, plik jest `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` tworzony w folderze. Aby uruchomić aplikację, przejdź do folderu `dotnet <PROJECT-NAME>.dll` wyjściowego i użyj polecenia.

Aplikacja jest skonfigurowana do kierowania określonej wersji programu .NET Core. Ten docelowy program .NET Core runtime jest wymagane na dowolnym komputerze, na którym aplikacja jest uruchamiana. Na przykład jeśli aplikacja jest przeznaczona dla .NET Core 2.2, każdy komputer, na której działa aplikacja, musi mieć zainstalowany czas uruchomieniowy .NET Core 2.2. Jak podano w [sekcji Podstawy publikowania,](#publishing-basics) można edytować plik projektu, aby zmienić domyślną strukturę docelową lub kierować więcej niż jedną strukturę.

Publikowanie fdd tworzy aplikację, która automatycznie przerzuca dalej do najnowszej poprawki zabezpieczeń .NET Core dostępnej w systemie, w który działa aplikacja. Aby uzyskać więcej informacji na temat powiązania wersji w czasie kompilacji, zobacz [Wybierz wersję .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Plik wykonywalny zależny od struktury

Dla polecenia CLI .NET Core SDK 3.x plik wykonywalny zależny `dotnet publish` od struktury (FDE) jest domyślnym trybem polecenia podstawowego. Nie trzeba określać żadnych innych parametrów, tak długo, jak chcesz kierować bieżącego systemu operacyjnego.

W tym trybie host wykonywalny specyficzny dla platformy jest tworzony w celu hosta aplikacji między platformami. Ten tryb jest podobny do FDD, ponieważ FDD `dotnet` wymaga hosta w postaci polecenia. Nazwa pliku wykonywalnego hosta różni się `<PROJECT-FILE>.exe`w zależności od platformy i nosi nazwę podobną do . Ten plik wykonywalny `dotnet <PROJECT-FILE>.dll`można uruchomić bezpośrednio zamiast wywoływania , co nadal jest akceptowalnym sposobem uruchamiania aplikacji.

Aplikacja jest skonfigurowana do kierowania określonej wersji programu .NET Core. Ten docelowy program .NET Core runtime jest wymagane na dowolnym komputerze, na którym aplikacja jest uruchamiana. Na przykład jeśli aplikacja jest przeznaczona dla .NET Core 2.2, każdy komputer, na której działa aplikacja, musi mieć zainstalowany czas uruchomieniowy .NET Core 2.2. Jak podano w [sekcji Podstawy publikowania,](#publishing-basics) można edytować plik projektu, aby zmienić domyślną strukturę docelową lub kierować więcej niż jedną strukturę.

Publikowanie FDE tworzy aplikację, która automatycznie przerzuca dalej do najnowszej poprawki zabezpieczeń .NET Core dostępnej w systemie uruchamiającym aplikację. Aby uzyskać więcej informacji na temat powiązania wersji w czasie kompilacji, zobacz [Wybierz wersję .NET Core do użycia](../versions/selection.md#framework-dependent-apps-roll-forward).

W przypadku programu .NET Core 2.2 i wcześniejszych `dotnet publish` należy użyć następujących przełączników z poleceniem do opublikowania FDE:

- `-r <RID>`Ten przełącznik używa identyfikatora (RID) do określenia platformy docelowej. Aby uzyskać listę identyfikatorów czasu wykonywania, zobacz [Katalog identyfikatorów ustawień wykonywania (RID).](../rid-catalog.md)

- `--self-contained false`Ten przełącznik informuje zestaw SDK .NET Core o utworzeniu pliku wykonywalnego jako FDE.

Za każdym razem, gdy używasz `-r` przełącznika, ścieżka folderu wyjściowego zmienia się na:`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Jeśli używasz [przykładowej](#sample-app)aplikacji `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`, uruchom . To polecenie tworzy następujący plik wykonywalny:`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Całkowity rozmiar wdrożenia można zmniejszyć, włączając **tryb niezmienny globalizacji.** Ten tryb jest przydatny w przypadku aplikacji, które nie są globalnie świadome i które mogą używać konwencji formatowania, konwencji wielkości liter oraz porównania i sortowania ciągów [kultury niezmiennej.](xref:System.Globalization.CultureInfo.InvariantCulture) Aby uzyskać więcej informacji na temat **trybu niezmiennego globalizacji** i sposobu jego włączenia, zobacz [Tryb niezmienny globalizacji .NET .](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Samodzielne wdrażanie

Podczas publikowania niezależnego wdrożenia (SCD) zestaw SDK .NET Core tworzy plik wykonywalny specyficzny dla platformy. Publikowanie dysku SCD zawiera wszystkie wymagane pliki .NET Core do uruchomienia aplikacji, ale nie zawiera [natywnych zależności .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Te zależności muszą być obecne w systemie przed uruchomieniem aplikacji.

Publikowanie dysku SCD tworzy aplikację, która nie jest przerzucana do najnowszej dostępnej poprawki zabezpieczeń .NET Core. Aby uzyskać więcej informacji na temat powiązania wersji w czasie kompilacji, zobacz [Wybierz wersję .NET Core do użycia](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Aby opublikować dysk SCD, należy użyć następujących przełączników z `dotnet publish` poleceniem:

- `-r <RID>`Ten przełącznik używa identyfikatora (RID) do określenia platformy docelowej. Aby uzyskać listę identyfikatorów czasu wykonywania, zobacz [Katalog identyfikatorów ustawień wykonywania (RID).](../rid-catalog.md)

- `--self-contained true`Ten przełącznik informuje zestaw SDK .NET Core o utworzeniu pliku wykonywalnego jako dysku SCD.

> [!NOTE]
> Całkowity rozmiar wdrożenia można zmniejszyć, włączając **tryb niezmienny globalizacji.** Ten tryb jest przydatny w przypadku aplikacji, które nie są globalnie świadome i które mogą używać konwencji formatowania, konwencji wielkości liter oraz porównania i sortowania ciągów [kultury niezmiennej.](xref:System.Globalization.CultureInfo.InvariantCulture) Aby uzyskać więcej informacji na temat **trybu niezmiennego globalizacji** i sposobu jego włączenia, zobacz [Tryb niezmienny globalizacji .NET .](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)

## <a name="see-also"></a>Zobacz też

- [Omówienie wdrażania aplikacji podstawowej .NET](index.md)
- [Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)](../rid-catalog.md)
