---
ms.openlocfilehash: 09e3f0e168e0dcbe79d8ee7216f2671c67bfb87e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802977"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Sprawdzanie pisowni WPF kończy się niepowodzeniem w nieoczekiwany sposób

|   |   |
|---|---|
|Szczegóły|Obejmuje to szereg problemów z sprawdzaniem pisowni WPF:<ul><li>WPF Spell Checker czasami rzuca<xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Sprawdzanie pisowni WPF <xref:System.UnauthorizedAccessException> kończy się niepowodzeniem, gdy aplikacje są uruchamiane przy użyciu "uruchom jako inny użytkownik"</li><li>Moduł sprawdzania pisowni WPF niepoprawnie identyfikuje błędy pisowni w złożonych wyrazach, takich jak "Hausnummer" w języku niemieckim.</li></ul>|
|Sugestia|Problem #1 — zostało to naprawione w .NET Framework 4.6.2 problem #2 — WPF Spell Checker nie jest już obsługiwany, gdy aplikacje są uruchamiane przy użyciu "uruchom jako inny użytkownik". Uruchamianie programu .NET Framework 4.6.2, aplikacje uruchomione w ten sposób nie będą już nieoczekiwanie ulegać awarii — zamiast tego moduł sprawdzania pisowni zostanie po cichu wyłączony. Problem #3 — zostało to naprawione w .NET Framework 4.6.2.|
|Zakres|Brzeg|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|
