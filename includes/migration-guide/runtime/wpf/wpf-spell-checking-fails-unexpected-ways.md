---
ms.openlocfilehash: 8049bf01bc10c5913fa11b25e49afd1b1317eecc
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802977"
---
### <a name="wpf-spell-checking-fails-in-unexpected-ways"></a>Sprawdzanie pisowni WPF nie powiedzie się w nieoczekiwany sposób

|   |   |
|---|---|
|Szczegóły|Obejmuje to wiele problemów WPF moduł sprawdzania pisowni:<ul><li>Czasami zgłasza sprawdzania pisowni WPF <xref:System.Runtime.InteropServices.COMException?displayProperty=name></li><li>Moduł sprawdzania pisowni WPF kończy się niepowodzeniem z <xref:System.UnauthorizedAccessException> podczas uruchamiania aplikacji za pomocą polecenia "Uruchom jako inny użytkownik"</li><li>Moduł sprawdzania pisowni WPF niepoprawnie identyfikuje błędy pisowni w wyrazy złożone, takich jak "Hausnummer" w języku niemieckim.</li></ul>|
|Sugestia|Problem #1 — ten problem został rozwiązany w programie .NET Framework 4.6.2 problem nr 2 — Moduł sprawdzania pisowni WPF nie jest już obsługiwana w przypadku aplikacji na rynek za pomocą polecenia "Uruchom jako inny użytkownik". Począwszy od .NET Framework 4.6.2, aplikacje uruchomione w ten sposób nie będzie nieoczekiwaną awarię — zamiast tego sprawdzania pisowni będzie dyskretnie wyłączone. Problem #3 — ten problem został rozwiązany w programie .NET Framework 4.6.2.|
|Scope|Krawędź|
|Wersja|4.6.1|
|Typ|Środowisko uruchomieniowe|

