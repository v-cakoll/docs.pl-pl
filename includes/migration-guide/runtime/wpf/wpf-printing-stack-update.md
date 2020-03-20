---
ms.openlocfilehash: 6fafb689af5d50b31b19f5d1fe7090a6c256ca45
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802539"
---
### <a name="wpf-printing-stack-update"></a>Aktualizacja stosu drukowania WPF

|   |   |
|---|---|
|Szczegóły|Interfejsy API drukowania WPF WPF przy użyciu <xref:System.Printing.PrintQueue?displayProperty=name> teraz wywołać okna Print Document Package API na rzecz teraz przestarzałe XPS Print API. Zmiana została wniesiena z myślą o zbywalności; ani użytkownicy, ani deweloperzy nie powinni widzieć żadnych zmian w zachowaniu lub użyciu interfejsu API. Nowy stos drukowania jest domyślnie włączony podczas pracy w aktualizacji Windows 10 Creators Update. Stary stos drukowania będzie nadal działać tak jak poprzednio w starszych wersjach systemu Windows.|
|Sugestia|Aby użyć starego stosu w aktualizacji Windows <code>UseXpsOMPrinting</code> 10 Creators Update, ustaw <code>1</code>wartość REG_DWORD klucza rejestru na <code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> .|
|Zakres|Brzeg|
|Wersja|4.7|
|Typ|Środowisko uruchomieniowe|
