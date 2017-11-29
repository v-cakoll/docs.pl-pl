---
title: Wymagania systemowe programu .NET framework
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- software requirements
- .NET Framework, system requirements
- system requirements
- operating systems supported
- hardware requirements
ms.assetid: 298275e2-da1d-4618-9f74-6a3567832350
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b08bd7b78a8606f61c266da51f4079f0b5f4aac6
ms.sourcegitcommit: d0f7646d67db5809cf43ff1d27b399a4020e8ee2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2017
---
# <a name="net-framework-system-requirements"></a>Wymagania systemowe programu .NET framework

Tabele w tym temacie zawierają sprzętu, systemu operacyjnego i wymagań dotyczących oprogramowania dla programu .NET Framework 4.5 oraz jego wersje punktu (4.5.1 i 4.5.2), [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] i jego wersje punktu (4.6.1 i 4.6.2) i .NET Framework 4.7 i jego punktu Wersja (4.7.1). Środowisk deweloperskich, które umożliwiają tworzenie aplikacji dla programu .NET Framework ma osobny zestaw wymagań.

Pobieranie informacji oraz linki, zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).

Aby uzyskać informacje na cykl pomocy technicznej wersje programu .NET Framework, zobacz [Microsoft Cykl wsparcia technicznego produktów](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=Microsoft%20.NET%20Framework&Filter=FilterNO).

## <a name="hardware-requirements"></a>Wymagania sprzętowe

|                          |        |
| ------------------------ | ------ |
| **Procesor**            | 1 GHz  |
| **PAMIĘĆ RAM**                  | 512 MB |
| **Miejsce na dysku (minimum)** |        |
| 32-bitowa                   | 4.5 GB |
| 64-bitowy                   | 4.5 GB |

## <a name="installation-requirements"></a>Wymagania dotyczące instalacji

.NET Framework wymaga uprawnień administratora do instalacji. Jeśli nie masz uprawnienia administratora na komputerze, na którym chcesz zainstalować program .NET Framework, skontaktuj się z administratorem sieci.

## <a name="supported-client-operating-systems"></a>Obsługiwane klienckie systemy operacyjne

| System operacyjny | Obsługiwane wersje | Wstępnie zainstalowane z systemem operacyjnym | Można zainstalować oddzielnie |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| Aktualizacja spadek twórców systemu Windows 10 | 32-bitowe i 64-bitowych | .NET framework 4.7.1 | |
| Aktualizacja twórców systemu Windows 10 | 32-bitowe i 64-bitowych | .NET framework 4.7 | .NET framework 4.7.1 | 
| Rocznicowa aktualizacja systemu Windows 10 | 32-bitowe i 64-bitowych | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| Usługa Windows Update 10 listopada | 32-bitowe i 64-bitowych | [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] | |
| Windows 10 | 32-bitowe i 64-bitowych | [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] | [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| [!INCLUDE[win81](../../../includes/win81-md.md)] | 32-bitowy, 64-bitowy i ARM | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| [!INCLUDE[win8](../../../includes/win8-md.md)] | 32-bitowy, 64-bitowy i ARM | [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] |
| Windows 7 z dodatkiem SP1|32-bitowe i 64-bitowych | -- | Program .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1|
| Windows Vista z dodatkiem SP2|32-bitowe i 64-bitowych | -- | Program .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |
| Windows XP |32-bitowe i 64-bitowych | -- | Program .NET Framework 4 |

 **Uwagi:**

- W systemach Windows 7 .NET Framework wymaga systemu Windows 7 z dodatkiem SP1. Jeśli komputer znajduje się w systemie Windows 7 i nie został jeszcze zainstalowany dodatek Service Pack 1, należy to zrobić przed zainstalowaniem programu .NET Framework.

- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Jest obsługiwana w środowisku preinstalacji systemu Windows (Windows PE). Nie wszystkie funkcje są obsługiwane w środowisku Windows PE.

- .NET Framework 4 obsługuje również platformie IA64.

- Dla wszystkich platform, zaleca się uaktualnienie do najnowszego dodatku Service Pack dla systemu Windows i zainstaluj aktualizacje krytyczne, które są dostępne z [witryny Windows Update](http://go.microsoft.com/fwlink/?LinkId=168461) aby zapewnić najlepsze zgodności i zabezpieczeń.

- W 64-bitowych systemach operacyjnych .NET Framework obsługuje WOW64 (32-bitowy przetwarzania na komputerze 64-bitowym) i natywnych 64-bitowego przetwarzania.

## <a name="supported-server-operating-systems"></a>Systemy operacyjne obsługiwane serwera

| System operacyjny | Obsługiwane wersje | Wstępnie zainstalowane z systemem operacyjnym | Można zainstalować oddzielnie |
| ---------------- | ------------------ | ------------------------ | ---------------------- |
| W systemie Windows Server w wersji 1709 | 64-bitowy | .NET framework 4.7.1 | -- |
| Windows Server 2016 | 64-bitowy | [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] | .NET framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 z dodatkiem R2 | 64-bitowy | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] | [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/> .NET framework 4.7.1 |
| Windows Server 2012 (64-bitowa) | 64-bitowy| [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] | [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 R2 SP1|64-bitowy | -- | Program .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]<br /><br /> [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]<br /><br />.NET framework 4.7<br/><br/>.NET framework 4.7.1 |
| Windows Server 2008 SP2|32-bitowe i 64-bitowych | -- | Program .NET Framework 4<br /><br /> [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]<br /><br /> [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]<br /><br /> [!INCLUDE[net_v452](../../../includes/net-v452-md.md)]<br /><br /> [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] |

 **Uwagi:**

- [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]zawiera [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], więc nie trzeba zainstalować oddzielnie. Podobnie [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] obejmuje [!INCLUDE[net_v451](../../../includes/net-v451-md.md)].

- .NET Framework ma ograniczoną obsługę roli Server Core z systemu Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [funkcje platformy .NET Core serwera](https://msdn.microsoft.com/library/ee391632.aspx) listę nieobsługiwany interfejsów API.

- .NET Framework nie jest obsługiwana w systemie Windows Server 2008 R2 dla komputerów z procesorami Itanium.

- W systemie Windows Server 2008 z dodatkiem SP2 .NET Framework nie jest obsługiwana w roli Server Core.

- Dla wszystkich platform, zaleca się uaktualniania do najnowszego dodatku Service Pack dla systemu Windows i krytyczne aktualizacje dostępne z [witryny Windows Update](http://go.microsoft.com/fwlink/?LinkId=168461) aby zapewnić najlepsze zgodności i zabezpieczeń. W niektórych systemach operacyjnych, może być konieczne instalacji najnowszego dodatku Service Pack dla systemu Windows.

- W 64-bitowych systemach operacyjnych .NET Framework obsługuje WOW64 (32-bitowy przetwarzania na komputerze 64-bitowym) i natywnych 64-bitowego przetwarzania.

## <a name="see-also"></a>Zobacz także

[Przewodnik instalacji](../../../docs/framework/install/index.md)   
[Wprowadzenie](../../../docs/framework/get-started/index.md)   
[Rozwiązywanie problemów z zablokowaną .NET Framework i odinstalowywaniem programu](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
