---
title: .NET Framework & wersje systemu operacyjnego Windows
ms.custom: updateeachrelease
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: 62ec1e21fd8e95991af6e2f8fa6f99c17249c761
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452724"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework wersje i zależności

Każda wersja .NET Framework zawiera środowisko uruchomieniowe języka wspólnego (CLR), biblioteki klas podstawowych i inne zarządzane biblioteki. W tym artykule opisano najważniejsze funkcje .NET Framework według wersji, zawiera informacje o podstawowych wersjach środowiska CLR i skojarzonych środowiskach programistycznych, a także identyfikuje wersje instalowane przez system operacyjny Windows (OS).

Każda nowa wersja .NET Framework dodaje nowe funkcje, ale zachowuje funkcje z poprzednich wersji.

Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji. Numer wersji .NET Framework jest zwiększany przy każdej wersji, ale wersja środowiska CLR nie zawsze jest zwiększana. Na przykład .NET Framework 4, 4,5 i nowsze wersje obejmują środowisko CLR 4, ale .NET Framework 2,0, 3,0 i 3,5 zawierają środowisko CLR 2,0. (Nie było wersji 3 środowiska CLR).

> [!TIP]
>
> - Aby uzyskać pełną listę obsługiwanych systemów operacyjnych, zobacz [wymagania systemowe](../get-started/system-requirements.md).
> - Aby uzyskać pliki do pobrania, zobacz [Install the .NET Framework for Developers](../install/guide-for-developers.md).
> - Aby uzyskać informacje dotyczące ustalania, które wersje .NET Framework są zainstalowane na komputerze, zobacz [jak określić, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).

## <a name="version-information"></a>Informacje o wersji

Poniższe tabele podsumowują historię wersji .NET Framework i skorelowania poszczególnych wersji z programem Visual Studio, systemem Windows i systemem Windows Server. Program Visual Studio obsługuje wiele elementów docelowych, więc nie masz ograniczenia do wersji .NET Framework, która jest wymieniona.

- Ikona znacznika wyboru ✔️ wskazuje wersje systemu operacyjnego, na których zainstalowano .NET Framework, ale muszą być włączone [w panelu sterowania](../install/dotnet-35-windows-10.md) (dla systemu Windows) lub za pomocą Menedżer serwera (dla systemu Windows Server).
- Ikona znaku plus ➕ wskazuje wersje systemu operacyjnego, na których .NET Framework nie są zainstalowane, ale można je zainstalować.

| | |
| - | - |
| [.NET Framework 4,8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4,7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4,6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3,5](#net-framework-35) |
| [.NET Framework 3,0](#net-framework-30) | [.NET Framework 2,0](#net-framework-20) | [.NET Framework 1,1](#net-framework-11) | [.NET Framework 1,0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4,8

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-48)
- [Nowość w ułatwieniach dostępu](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Wersje systemu Windows**|Aktualizacja ✔️ 10 maja 2019<br/>➕ 10 października 2018 Update (wersja 1809)<br/>➕ 10 kwietnia 2018 Update (wersja 1803)<br/>➕ 10 jesień Update (wersja 1709)<br/>Aktualizacja ➕ 10 dla twórców (wersja 1703)<br/>➕ 10 rocznicowej aktualizacji (wersja 1607)<br/>➕ 8,1<br/>➕ 7|
|**Wersje systemu Windows Server**|➕ Windows Server 2019<br/>➕ Systemu Windows Server w wersji 1809<br/>➕ Systemu Windows Server w wersji 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 Z DODATKIEM SP1|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br/>-528040 (Aktualizacja systemu Windows 10 może 2019)<br/>-528049 (wszystkie inne wersje systemu operacyjnego)<br/>(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-472)
- [Nowość w ułatwieniach dostępu](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Uwzględnione w wersji programu Visual Studio**|2019<sup>1</sup>|
|**Wersje systemu Windows**|✔️ 10 października 2018 Update (wersja 1809)<br/>✔️ 10 kwietnia 2018 Update (wersja 1803)<br/>➕ 10 jesień Update (wersja 1709)<br/>Aktualizacja ➕ 10 dla twórców (wersja 1703)<br/>➕ 10 rocznicowej aktualizacji (wersja 1607)<br/>➕ 8,1<br/>➕ 7|
|**Wersje systemu Windows Server**|✔️ Windows Server 2019<br/>✔️ systemu Windows Server w wersji 1809<br/>✔️ systemu Windows Server w wersji 1803<br/>➕ Systemu Windows Server w wersji 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 Z DODATKIEM SP1|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br/>-461814 (Aktualizacja systemu Windows 10 października 2018)<br/>-461808 (Aktualizacja systemu Windows 10 kwietnia 2018 i system Windows Server w wersji 1803)<br/>-461814 (wszystkie inne wersje systemu operacyjnego)<br/>(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> wymaga zainstalowania programu **.NET desktop Development**, **ASP.NET i Web**Development, programowanie na **platformie Azure**, **Programowanie Office/SharePoint**, programowanie **aplikacji mobilnych przy użyciu platformy .NET**lub **platformy .NET Core dla wielu platform** .

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-471)
- [Nowość w ułatwieniach dostępu](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Wersje systemu Windows**|✔️ 10 jesień Update (wersja 1709)<br/>Aktualizacja ➕ 10 dla twórców (wersja 1703)<br/>➕ 10 rocznicowej aktualizacji (wersja 1607)<br/>➕ 8,1<br/>➕ 7|
|**Wersje systemu Windows Server**|➕ Systemu Windows Server w wersji 1803<br/>✔️ systemu Windows Server w wersji 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 Z DODATKIEM SP1|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br/>-461308 (aktualizacje systemu Windows 10 dla twórców i system Windows Server w wersji 1709)<br/>-461310 (wszystkie inne wersje systemu operacyjnego)<br/>(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-47"></a>.NET framework 4.7

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-47)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Wersje systemu Windows**|Aktualizacja ✔️ 10 dla twórców (wersja 1703)<br/>➕ 10 rocznicowej aktualizacji (wersja 1607)<br/>➕ 8,1<br/>➕ 7|
|**Wersje systemu Windows Server**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 Z DODATKIEM SP1|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br/>-460798 (Aktualizacja systemu Windows 10 dla twórców)<br/>-460805 (wszystkie inne wersje systemu operacyjnego)<br/>(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-462)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Wersje systemu Windows**|✔️ 10 rocznicowej aktualizacji (wersja 1607)<br/>Aktualizacja ➕ 10 listopada (wersja 1511)<br/>➕ 10<br/>➕ 8,1<br />➕ 7|
|**Wersje systemu Windows Server**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 Z DODATKIEM SP1|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br /><br/>-394802 (Aktualizacja z rocznicą systemu Windows 10 i system Windows Server 2016)<br/>-394806 (wszystkie inne wersje systemu operacyjnego)<br /><br/>(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-461)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Uwzględnione w wersji programu Visual Studio**|2017<sup>1</sup>|
|**Wersje systemu Windows**|Aktualizacja ✔️ 10 listopada (wersja 1511)<br/>➕ 10<br />➕ 8,1<br />➕ 8<br />➕ 7|
|**Wersje systemu Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 Z DODATKIEM SP1|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br /><br/>-394254 (Aktualizacja systemu Windows 10 z listopada)<br />-394271 (wszystkie inne wersje systemu operacyjnego)<br /><br/>(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

<sup>1</sup> wymaga zainstalowania programu **.NET desktop Development**, **ASP.NET i Web**Development, programowanie na **platformie Azure**, **Programowanie Office/SharePoint**, programowanie **aplikacji mobilnych przy użyciu platformy .NET**lub **platformy .NET Core dla wielu platform** .

### <a name="net-framework-46"></a>Program .NET Framework 4.6

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-2015)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Uwzględnione w wersji programu Visual Studio**|2015|
|**Wersje systemu Windows**|✔️ 10<br /><br />➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 Z DODATKIEM SP1<br />➕ 2008 Z DODATKIEM SP2|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br /><br />-393295 (system Windows 10)<br />-393297 (wszystkie inne wersje systemu operacyjnego)<br /><br />(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-452)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Wersje systemu Windows**|➕ 8,1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 Z DODATKIEM SP1<br />➕ 2008 Z DODATKIEM SP2|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD 379893<br /><br />(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-451)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Uwzględnione w wersji programu Visual Studio**|2013|
|**Wersje systemu Windows**|✔️ 8,1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 Z DODATKIEM SP1<br />➕ 2008 Z DODATKIEM SP2|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD:<br /><br />-378675 (Windows 8.1)<br />-378758 (wszystkie inne)<br /><br />(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [Nowe funkcje](../whats-new/index.md#whats-new-in-net-framework-45)
- [Informacje o wersji](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Uwzględnione w wersji programu Visual Studio**|2012|
|**Wersje systemu Windows**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|✔️ 2012<br />➕ 2008 R2 Z DODATKIEM SP1<br />➕ 2008 Z DODATKIEM SP2|
|**Aby określić zainstalowaną wersję programu .NET**|Użyj `Release` DWORD 378389<br /><br />(Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md))|

### <a name="net-framework-4"></a>Program .NET Framework 4

[Nowe funkcje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**Wersja środowiska CLR**|4|
|**Uwzględnione w wersji programu Visual Studio**|2010|
|**Wersje systemu Windows**|➕ 7<br />➕ Vista|
|**Wersje systemu Windows Server**|➕ 2008 R2 Z DODATKIEM SP1<br />➕ 2008 Z DODATKIEM SP2<br />➕ 2003|
|**Aby określić zainstalowaną wersję programu .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-35"></a>.NET Framework 3.5

[Nowe funkcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- Drzewa wyrażeń
- Ulepszona obsługa ASP.NET na potrzeby programowania AJAX
- HashSet — kolekcje
- DateTimeOffset
- Integracja WCF i WF
- Sieć równorzędna
- Dodatki do rozszerzalności

|||
|-|-|
|**Wersja środowiska CLR**|2.0|
|**Uwzględnione w wersji programu Visual Studio**|2008|
|**Wersje systemu Windows**|✔️ 10\*<br/>✔️ 8,1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Wersje systemu Windows Server**|➕ Systemu Windows Server w wersji 1803\*<br/>➕ Systemu Windows Server w wersji 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️ 2008 R2 z dodatkiem SP1\*<br /><br/>➕ 2008 Z DODATKIEM SP2<br />➕ 2003|
|**Aby określić zainstalowaną wersję programu .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-30"></a>.NET Framework 3.0

[Nowe funkcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)):

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**Wersja środowiska CLR**|2.0|
|**Wersje systemu Windows**|✔️ Vista|
|**Wersje systemu Windows Server**|✔️ 2008 R2 Z DODATKIEM SP1 *<br />✔️ 2008 z dodatkiem SP2\*<br /><br />➕ 2003|
|**Aby określić zainstalowaną wersję programu .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md).|

### <a name="net-framework-20"></a>.NET Framework 2.0

[Nowe funkcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/t357fb32%28v%3dvs.90%29):

- Typy ogólne
- Debuger Edytuj i Kontynuuj
- Zwiększona skalowalność i wydajność
- wdrożenie ClickOnce
- W ASP.NET 2,0, nowe kontrolki i wsparcie dla szerokiej gamy przeglądarek
- 64-bit — obsługa

|||
|-|-|
|**Wersja środowiska CLR**|2.0|
|**Uwzględnione w wersji programu Visual Studio**|2005|
|**Wersje systemu Windows**|Nie dotyczy|
|**Wersje systemu Windows Server**|✔️ 2008 R2 Z DODATKIEM SP1<br />✔️ 2008 Z DODATKIEM SP2<br />✔️ 200|
|**Aby określić zainstalowaną wersję programu .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-11"></a>.NET Framework 1.1

[Nowe funkcje](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/h88tthh0%28v%3dvs.90%29):

- Kontrolki mobilne ASP.NET
- Wykonywanie równoczesne
- Pomoc techniczna dotycząca protokołu IPv6

|||
|-|-|
|**Wersja środowiska CLR**|1.1|
|**Uwzględnione w wersji programu Visual Studio**|2003|
|**Wersje systemu Windows**|Nie dotyczy|
|**Wersje systemu Windows Server**|✔️ 2003|
|**Aby określić zainstalowaną wersję programu .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**Wersja środowiska CLR**|1.0|
|**Uwzględnione w wersji programu Visual Studio**|Visual Studio .NET|
|**Wersje systemu Windows**|Nie dotyczy|
|**Wersje systemu Windows Server**|Nie dotyczy|
|**Aby określić zainstalowaną wersję programu .NET**|Zobacz [instrukcje](how-to-determine-which-versions-are-installed.md)|

> [!NOTE]
>
> - .NET Framework musi być włączona w tym systemie operacyjnym za pomocą [Panelu sterowania (dla systemu Windows) lub Menedżer serwera (dla systemu Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel).
> - Ogólnie rzecz biorąc nie należy odinstalowywać żadnych wersji .NET Framework zainstalowanych na komputerze, ponieważ używana aplikacja może zależeć od określonej wersji i może zostać przerwana, jeśli ta wersja zostanie usunięta. Można ładować wiele wersji .NET Framework na jednym komputerze w tym samym czasie. Oznacza to, że można zainstalować .NET Framework bez konieczności odinstalowywania poprzednich wersji. Aby uzyskać więcej informacji, zobacz [wprowadzenie](../get-started/index.md).

## <a name="remarks-for-version-45-and-later"></a>Uwagi dotyczące wersji 4,5 i nowszych

.NET Framework 4,5 to aktualizacja w miejscu, która zastępuje .NET Framework 4 na komputerze, a podobnie .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 i 4,8 to aktualizacje w miejscu do .NET Framework 4,5. Aktualizacja w miejscu oznacza, że korzystają z tej samej wersji środowiska uruchomieniowego, ale wersje zestawu są aktualizowane i zawierają nowe typy i elementy członkowskie. Po zainstalowaniu jednej z tych aktualizacji .NET Framework 4, .NET Framework 4,5, .NET Framework 4,6 lub .NET Framework 4,7 aplikacje powinny nadal działać bez konieczności ponownej kompilacji. Jednak odwrotna zależność nie istnieje. Nie zaleca się uruchamiania aplikacji przeznaczonych dla nowszej wersji .NET Framework w starszej wersji. Na przykład nie zalecamy uruchamiania aplikacji dla elementów docelowych .NET Framework 4,6 na .NET Framework 4,5.

Należy przestrzegać następujących wytycznych:

- W programie Visual Studio można wybrać .NET Framework 4,5 jako platformę docelową dla projektu (ustawia właściwość <xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType>) do kompilowania projektu jako zestawu .NET Framework 4,5 lub pliku wykonywalnego. Ten zestaw lub plik wykonywalny można następnie użyć na dowolnym komputerze z zainstalowanym .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 lub 4,8.

- W programie Visual Studio można wybrać .NET Framework 4.5.1 jako platformę docelową dla projektu w celu skompilowania go jako zestawu .NET Framework 4.5.1 lub pliku wykonywalnego. Ten zestaw lub plik wykonywalny jest uruchamiany tylko na komputerach, na których zainstalowano .NET Framework 4.5.1 lub nowszy. Program wykonywalny przeznaczony dla .NET Framework 4.5.1 zostanie zablokowany na komputerze, na którym jest zainstalowana tylko wcześniejsza wersja .NET Framework, taka jak .NET Framework 4,5. Użytkownik zostanie poproszony o zainstalowanie .NET Framework 4.5.1. Ponadto nie należy wywoływać zestawów .NET Framework 4.5.1 z aplikacji, która jest przeznaczona dla starszej wersji .NET Framework, takiej jak .NET Framework 4,5.

  > [!NOTE]
  > .NET Framework 4.5.1 i .NET Framework 4,5 są używane w tym miejscu tylko jako przykłady. Opisana zasada dotyczy każdej aplikacji, która jest przeznaczona dla nowszej wersji .NET Framework niż zainstalowana w systemie, na którym jest uruchomiona.

Niektóre zmiany w .NET Framework mogą wymagać zmian w kodzie aplikacji; Sprawdź [zgodność aplikacji](application-compatibility.md) przed uruchomieniem istniejących aplikacji z .NET Framework 4,5 lub nowszymi wersjami. Aby uzyskać więcej informacji na temat instalowania bieżącej wersji, zobacz [Install the .NET Framework for Developers](../install/guide-for-developers.md). Aby uzyskać informacje na temat pomocy technicznej dla .NET Framework, zobacz [.NET Framework oficjalne zasady pomocy technicznej](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework) w witrynie sieci Web platformy .NET.

## <a name="remarks-for-older-versions"></a>Uwagi dotyczące starszych wersji

.NET Framework wersje 2,0, 3,0 i 3,5 są kompilowane przy użyciu tej samej wersji środowiska CLR (CLR 2,0). Te wersje reprezentują kolejne warstwy jednej instalacji. Każda wersja jest kompilowana przyrostowo na poprzednich wersjach. Nie jest możliwe uruchamianie wersji 2,0, 3,0 i 3,5 obok siebie na komputerze. Po zainstalowaniu wersji 3.5 automatycznie są udostępniane warstwy 2.0 i 3.0, a aplikacje, które zostały zaprojektowane dla wersji 2.0, 3.0 i 3.5, można uruchamiać z użyciem wersji 3.5. Jednakże .NET Framework 4 kończy to podejście warstwowe i jego nowsze wersje (.NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 i 4,8) również reprezentują kolejne warstwy pojedynczej instalacji. Począwszy od .NET Framework 4, można użyć funkcji w procesie, która obok siebie umożliwia uruchamianie wielu wersji środowiska CLR w pojedynczym procesie. Aby uzyskać więcej informacji, zobacz [zestawy i wykonywanie równoczesne](../../standard/assembly/side-by-side-execution.md).

Ponadto, jeśli aplikacja jest przeznaczona dla wersji 2,0, 3,0 lub 3,5, użytkownicy mogą być zobowiązani do włączenia .NET Framework 3,5 na komputerze z systemem Windows 8, Windows 8.1 lub Windows 10, zanim będą mogli uruchomić aplikację. Aby uzyskać więcej informacji, zobacz [instalowanie .NET Framework 3,5 w systemie Windows 10, Windows 8.1 i Windows 8](../install/dotnet-35-windows-10.md).

## <a name="next-steps"></a>Następne kroki

- Jeśli jesteś nowym .NET Framework, zapoznaj się z [omówieniem](../get-started/overview.md) , aby zapoznać się z wprowadzeniem do kluczowych pojęć i funkcji.

- Nowe funkcje i ulepszenia w .NET Framework 4,5 i jego wydania punktowe znajdują się [w artykule Co nowego w .NET Framework](../whats-new/index.md).

- Aby uzyskać informacje na temat migrowania aplikacji do nowszej wersji .NET Framework, zobacz [Przewodnik migracji](index.md).

- Aby uzyskać informacje dotyczące ustalania, które wersje lub aktualizacje są zainstalowane na komputerze, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md) , i [instrukcje: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="see-also"></a>Zobacz też

- [Zgodność wersji](version-compatibility.md)
| [.NET Framework oficjalne zasady pomocy technicznej](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](../install/troubleshoot-blocked-installations-and-uninstallations.md)
