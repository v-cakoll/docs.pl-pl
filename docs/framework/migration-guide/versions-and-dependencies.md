---
title: Program .NET Framework & wersji systemu operacyjnego Windows
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 486b320ca30323684d301630ad29f8f4615764ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77504049"
---
# <a name="net-framework-versions-and-dependencies"></a>Wersje i zależności programu .NET Framework

Każda wersja programu .NET Framework zawiera środowisko uruchomieniowe języka wspólnego (CLR), biblioteki klas podstawowych i inne biblioteki zarządzane. W tym artykule opisano kluczowe funkcje programu .NET Framework według wersji, zawiera informacje o podstawowych wersjach CLR i skojarzonych środowiskach programistycznych i identyfikuje wersje zainstalowane przez system operacyjny Windows(OS).

Każda nowa wersja programu .NET Framework dodaje nowe funkcje, ale zachowuje funkcje z poprzednich wersji.

Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji. Numer wersji programu .NET Framework jest zwiększany w każdej wersji, ale wersja CLR nie zawsze jest zwiększana. Na przykład .NET Framework 4, 4.5 i nowsze wersje obejmują CLR 4, ale .NET Framework 2.0, 3.0 i 3.5 obejmują CLR 2.0. (Nie było wersji 3 środowiska CLR).

> [!TIP]
>
> - Aby uzyskać pełną listę obsługiwanych systemów operacyjnych, zobacz [Wymagania systemowe](../get-started/system-requirements.md).
> - Aby uzyskać informacje o plikach do pobrania, zobacz [Instalowanie programu .NET Framework dla deweloperów](../install/guide-for-developers.md).
> - Aby uzyskać informacje dotyczące określania, które wersje programu .NET Framework są zainstalowane na komputerze, zobacz [Jak określić, które wersje programu .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informacje o wersji

Tabele, które należy wykonać podsumować historię wersji programu .NET Framework i skorelować każdą wersję z programami Visual Studio, Windows i Windows Server. Visual Studio obsługuje wiele kierowania, więc nie jesteś ograniczony do wersji programu .NET Framework, który jest wymieniony.

- Ikona znacznika wyboru ✔️ oznacza wersje systemu operacyjnego, w których jest zainstalowany program .NET Framework, ale musi być włączona [w Panelu sterowania](../install/dotnet-35-windows-10.md) (dla systemu Windows) lub za pośrednictwem Menedżera serwera (dla systemu Windows Server).
- Ikona znaku plus ➕ oznacza wersje systemu operacyjnego, na których program .NET Framework nie jest zainstalowany, ale można go zainstalować.

| | |
| - | - |
| [.NET Framework 4.8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [Program .NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [Program .NET Framework 4](#net-framework-4) | [Program .NET Framework 3,5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a> .NET Framework 4.8

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-48)
- [Nowość w dostępności](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Wersje systemu Windows**|✔️ aktualizacja z 10 maja 2019<br/>➕ aktualizacja z 10 października 2018 r. (wersja 1809)<br/>➕ aktualizacja z 10 kwietnia 2018 r. (wersja 1803)<br/>➕ 10 Fall Creators Update (wersja 1709)<br/>➕ 10 Creators Update (wersja 1703)<br/>➕ 10 rocznicowa aktualizacja (wersja 1607)<br/>➕ 8.1<br/>➕7|
|**Wersje systemu Windows Server**|➕ systemie Windows Server 2019<br/>➕ windows server, wersja 1809<br/>➕ systemie Windows Server w wersji 1803<br/>➕ 2016 r.<br/>➕ 2012 R2<br/>➕ 2012 r.<br/>➕ 2008 R2 SP1|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br/>- 528040 (Aktualizacja systemu Windows 10 maja 2019)<br/>- 528049 (wszystkie inne wersje systemu operacyjnego)<br/>(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-472"></a> .NET Framework 4.7.2

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-472)
- [Nowość w dostępności](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Zawarte w wersji programu Visual Studio**|2019<sup>r. 1</sup>|
|**Wersje systemu Windows**|✔️ aktualizacja z 10 października 2018 r. (wersja 1809)<br/>✔️ aktualizacja z 10 kwietnia 2018 r. (wersja 1803)<br/>➕ 10 Fall Creators Update (wersja 1709)<br/>➕ 10 Creators Update (wersja 1703)<br/>➕ 10 rocznicowa aktualizacja (wersja 1607)<br/>➕ 8.1<br/>➕7|
|**Wersje systemu Windows Server**|✔️ systemie Windows Server 2019<br/>✔️ Windows Server, wersja 1809<br/>✔️ systemie Windows Server w wersji 1803<br/>➕ Windows Server, wersja 1709<br/>➕ 2016 r.<br/>➕ 2012 R2<br/>➕ 2012 r.<br/>➕ 2008 R2 SP1|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br/>- 461814 (Aktualizacja systemu Windows 10 października 2018)<br/>- 461808 (Windows 10 April 2018 Update i Windows Server, wersja 1803)<br/>- 461814 (wszystkie inne wersje systemu operacyjnego)<br/>(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

<sup>1</sup> Wymaga zainstalowania **programu .NET rozwoju pulpitu,** **ASP.NET i tworzenia stron internetowych,** **tworzenia platformy Azure,** **rozwoju pakietu Office/SharePoint,** **rozwoju urządzeń mobilnych z programami .NET**lub **.NET Core obciążeń programisty.**

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-471)
- [Nowość w dostępności](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Wersje systemu Windows**|✔️ 10 Fall Creators Update (wersja 1709)<br/>➕ 10 Creators Update (wersja 1703)<br/>➕ 10 rocznicowa aktualizacja (wersja 1607)<br/>➕ 8.1<br/>➕7|
|**Wersje systemu Windows Server**|➕ systemie Windows Server w wersji 1803<br/>✔️ Windows Server, wersja 1709<br/>➕ 2016 r.<br/>➕ 2012 R2<br/>➕ 2012 r.<br/>➕ 2008 R2 SP1|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br/>- 461308 (Windows 10 Creators Update i Windows Server, wersja 1709)<br/>- 461310 (wszystkie inne wersje systemu operacyjnego)<br/>(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-47)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Wersje systemu Windows**|✔️ 10 Creators Update (wersja 1703)<br/>➕ 10 rocznicowa aktualizacja (wersja 1607)<br/>➕ 8.1<br/>➕7|
|**Wersje systemu Windows Server**|➕ 2016 r.<br/>➕ 2012 R2<br/>➕ 2012 r.<br/>➕ 2008 R2 SP1|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br/>- 460798 (Windows 10 Creators Update)<br/>- 460805 (wszystkie inne wersje systemu operacyjnego)<br/>(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-462)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Wersje systemu Windows**|✔️ 10-lecie aktualizacji (wersja 1607)<br/>➕ aktualizacja z 10 listopada (wersja 1511)<br/>➕ 10<br/>➕ 8.1<br />➕ 7|
|**Wersje systemu Windows Server**|✔️ 2016 r.<br /><br/>➕ 2012 R2<br />➕ 2012 r.<br />➕ 2008 R2 SP1|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br /><br/>- 394802 (Windows 10 Anniversary Update i Windows Server 2016)<br/>- 394806 (wszystkie inne wersje systemu operacyjnego)<br /><br/>(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-461)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Zawarte w wersji programu Visual Studio**|2017<sup>r. 1</sup>|
|**Wersje systemu Windows**|✔️ aktualizacja z 10 listopada (wersja 1511)<br/>➕ 10<br />➕ 8.1<br />➕ 8<br />➕ 7|
|**Wersje systemu Windows Server**|➕ 2012 R2<br />➕ 2012 r.<br />➕ 2008 R2 SP1|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br /><br/>- 394254 (Windows 10 Aktualizacja listopadowa)<br />- 394271 (wszystkie inne wersje systemu operacyjnego)<br /><br/>(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

<sup>1</sup> Wymaga zainstalowania **programu .NET rozwoju pulpitu,** **ASP.NET i tworzenia stron internetowych,** **tworzenia platformy Azure,** **rozwoju pakietu Office/SharePoint,** **rozwoju urządzeń mobilnych z programami .NET**lub **.NET Core obciążeń programisty.**

### <a name="net-framework-46"></a>Program .NET Framework 4.6

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-2015)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Zawarte w wersji programu Visual Studio**|2015|
|**Wersje systemu Windows**|✔️ 10<br /><br />➕ 8.1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|➕ 2012 R2<br />➕ 2012 r.<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br /><br />- 393295 (Windows 10)<br />- 393297 (wszystkie inne wersje systemu operacyjnego)<br /><br />(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-452)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Wersje systemu Windows**|➕ 8.1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|➕ 2012 R2<br />➕ 2012 r.<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD 379893<br /><br />(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-451)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Zawarte w wersji programu Visual Studio**|2013|
|**Wersje systemu Windows**|✔️ 8.1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|✔️ 2012 R2<br /><br />➕ 2012 r.<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD:<br /><br />- 378675 (Windows 8.1)<br />- 378758 (wszystkie pozostałe)<br /><br />(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-45)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Wersja CLR**|4|
|**Zawarte w wersji programu Visual Studio**|2012|
|**Wersje systemu Windows**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|✔️ 2012 r.<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**Aby określić zainstalowaną wersję .NET**|Użyj `Release` DWORD 378389<br /><br />(Patrz [instrukcje)](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-4"></a>Program .NET Framework 4

[Nowe funkcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Wersja CLR**|4|
|**Zawarte w wersji programu Visual Studio**|2010|
|**Wersje systemu Windows**|➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003 r.|
|**Aby określić zainstalowaną wersję .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>Program .NET Framework 3,5

[Nowe funkcje:](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\))

- LINQ
- Drzewa wyrażeń
- Ulepszone wsparcie ASP.NET dla rozwoju AJAX
- Kolekcje HashSet
- Datetimeoffset
- Integracja WCF i WF
- Sieci peer-to-peer
- Dodatki rozszerzalności

|||
|-|-|
|**Wersja CLR**|2.0|
|**Zawarte w wersji programu Visual Studio**|2008|
|**Wersje systemu Windows**|✔️ 10\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Wersje systemu Windows Server**|➕ systemie Windows Server w wersji 1803\*<br/>➕ Windows Server, wersja 1709\*<br/>➕ 2016 r.\*<br/>➕ 2012 R2\*<br />➕ 2012 r.\*<br /><br />✔️2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003 r.|
|**Aby określić zainstalowaną wersję .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Nowe funkcje:](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90))

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Obszar kart systemu Windows

|||
|-|-|
|**Wersja CLR**|2.0|
|**Wersje systemu Windows**|✔️ Vista|
|**Wersje systemu Windows Server**|✔️ 2008 R2 SP1*<br />✔️ 2008 SP2\*<br /><br />➕ 2003 r.|
|**Aby określić zainstalowaną wersję .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Nowe funkcje:](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29)

- Typy ogólne
- Debuger edytuj i kontynuuj
- Zwiększona skalowalność i wydajność
- wdrożenie ClickOnce
- W ASP.NET 2.0 nowe elementy sterujące i obsługa szerokiej gamy przeglądarek
- 64-bit — obsługa

|||
|-|-|
|**Wersja CLR**|2.0|
|**Zawarte w wersji programu Visual Studio**|2005|
|**Wersje systemu Windows**|Nie dotyczy|
|**Wersje systemu Windows Server**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 2003 r.|
|**Aby określić zainstalowaną wersję .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Nowe funkcje:](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29)

- ASP.NET sterowanie mobilne
- Wykonywanie równoczesne
- Pomoc techniczna dotycząca protokołu IPv6

|||
|-|-|
|**Wersja CLR**|1.1|
|**Zawarte w wersji programu Visual Studio**|2003|
|**Wersje systemu Windows**|Nie dotyczy|
|**Wersje systemu Windows Server**|✔️ 2003 r.|
|**Aby określić zainstalowaną wersję .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Wersja CLR**|1.0|
|**Zawarte w wersji programu Visual Studio**|Visual Studio .NET|
|**Wersje systemu Windows**|Nie dotyczy|
|**Wersje systemu Windows Server**|Nie dotyczy|
|**Aby określić zainstalowaną wersję .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - Program .NET Framework musi być włączony w tym systemie operacyjnym za pośrednictwem [Panelu sterowania (dla systemu Windows) lub Menedżera serwera (dla systemu Windows Server).](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)
> - Ogólnie rzecz biorąc nie należy odinstalowywać żadnych wersji programu .NET Framework zainstalowanych na komputerze, ponieważ używana aplikacja może zależeć od określonej wersji i może ulec przerwaniu w przypadku usunięcia tej wersji. Można załadować wiele wersji programu .NET Framework na jednym komputerze w tym samym czasie. Oznacza to, że można zainstalować program .NET Framework bez konieczności odinstalowywania poprzednich wersji. Aby uzyskać więcej informacji, zobacz [Wprowadzenie](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Uwagi dotyczące wersji 4.5 i nowszej

.NET Framework 4.5 to aktualizacja w miejscu, która zastępuje program .NET Framework 4 na komputerze, i podobnie .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 i 4.8 są aktualizacjami w miejscu .NET Framework 4.5. Aktualizacja w miejscu oznacza, że używają tej samej wersji środowiska wykonawczego, ale wersje zestawu są aktualizowane i zawierają nowe typy i elementy członkowskie. Po zainstalowaniu jednej z tych aktualizacji aplikacje .NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 lub .NET Framework 4.7 powinny nadal działać bez konieczności ponownej kompilacji. Jednak odwrotna zależność nie istnieje. Nie zaleca się uruchamiania aplikacji, które są przeznaczone dla nowszej wersji programu .NET Framework we wcześniejszej wersji. Na przykład nie zaleca się uruchamiania aplikacji obiektów docelowych .NET Framework 4.6 w programie .NET Framework 4.5.

Należy przestrzegać następujących wytycznych:

- W programie Visual Studio można wybrać .NET Framework 4.5 jako platformę docelową dla projektu (to ustawia <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> właściwość) do kompilowania projektu jako .NET Framework 4.5 zestawu lub pliku wykonywalnego. Ten zestaw lub plik wykonywalny może być następnie używany na dowolnym komputerze z zainstalowanym programem .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7.1, 4.7.2 lub 4.8.

- W programie Visual Studio można wybrać program .NET Framework 4.5.1 jako platformę docelową dla projektu, aby skompilować go jako .NET Framework 4.5.1 zestawu lub pliku wykonywalnego. Uruchom ten zestaw lub plik wykonywalny tylko na komputerach z zainstalowanym programem .NET Framework 4.5.1 lub nowszym. Plik wykonywalny przeznaczony dla platformy .NET Framework 4.5.1 zostanie zablokowany przed uruchomieniem na komputerze, na który zainstalowano tylko wcześniejszą wersję programu .NET Framework, takiej jak .NET Framework 4.5. Użytkownik zostanie poproszony o zainstalowanie programu .NET Framework 4.5.1. Ponadto zestawy .NET Framework 4.5.1 nie powinny być wywoływane z aplikacji przeznaczonej dla wcześniejszej wersji programu .NET Framework, takiej jak .NET Framework 4.5.

  > [!NOTE]
  > .NET Framework 4.5.1 i .NET Framework 4.5 są tutaj używane tylko jako przykłady. Opisana zasada ma zastosowanie do każdej aplikacji przeznaczonej dla nowszej wersji programu .NET Framework niż tej zainstalowanej w systemie, w którym jest uruchomiona.

Niektóre zmiany w .NET Framework mogą wymagać zmian w kodzie aplikacji; Zobacz [Zgodność aplikacji](application-compatibility.md) przed uruchomieniem istniejących aplikacji w wersji .NET Framework 4.5 lub nowszej. Aby uzyskać więcej informacji na temat instalowania bieżącej wersji, zobacz [Instalowanie programu .NET Framework dla deweloperów](../install/guide-for-developers.md). Aby uzyskać informacje na temat pomocy technicznej dla programu .NET Framework, zobacz [.NET Framework oficjalne zasady pomocy technicznej](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) w witrynie sieci .NET.

## <a name="remarks-for-older-versions"></a>Uwagi dotyczące starszych wersji

Program .NET Framework w wersjach 2.0, 3.0 i 3.5 jest zbudowany z tą samą wersją programu CLR (CLR 2.0). Te wersje reprezentują kolejne warstwy jednej instalacji. Każda wersja jest kompilowana przyrostowo na poprzednich wersjach. Nie można uruchamiać wersji 2.0, 3.0 i 3.5 obok siebie na komputerze. Po zainstalowaniu wersji 3.5 automatycznie są udostępniane warstwy 2.0 i 3.0, a aplikacje, które zostały zaprojektowane dla wersji 2.0, 3.0 i 3.5, można uruchamiać z użyciem wersji 3.5. Jednak .NET Framework 4 kończy to podejście warstwowe, i nowsze wersje (.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 i 4.8) również przedstawiają kolejne warstwy pojedynczej instalacji. Począwszy od programu .NET Framework 4, można użyć hostingu w trakcie procesu, obok hostingu obok siebie, aby uruchomić wiele wersji programu CLR w jednym procesie. Aby uzyskać więcej informacji, zobacz [Zestawy i Wykonanie side-by-Side](../../standard/assembly/side-by-side-execution.md).

Ponadto jeśli aplikacja jest przeznaczona dla wersji 2.0, 3.0 lub 3.5, użytkownicy mogą być zobowiązani do włączenia programu .NET Framework 3.5 na komputerze z systemem Windows 8, Windows 8.1 lub Windows 10, zanim będą mogli uruchomić aplikację. Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Framework 3.5 w systemach Windows 10, Windows 8.1 i Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Następne kroki

- Jeśli jesteś nowy w .NET Framework, zobacz [omówienie](../get-started/overview.md) wprowadzenie do kluczowych pojęć i funkcji.

- Aby uzyskać nowe funkcje i ulepszenia w programie .NET Framework 4.5 i jego wersjach punktowych, zobacz [Co nowego w programie .NET Framework](../whats-new/index.md).

- Aby uzyskać informacje dotyczące migracji aplikacji do nowszej wersji programu .NET Framework, zobacz [przewodnik po migracji](index.md).

- Aby uzyskać informacje dotyczące określania, które wersje lub aktualizacje są zainstalowane na komputerze, zobacz [Jak: Określanie, które wersje programu .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md) i [jak: Określać, które aktualizacje programu .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="see-also"></a>Zobacz też

- [Zgodność wersji](version-compatibility.md)
| [.NET Framework oficjalna polityka pomocy technicznej](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
