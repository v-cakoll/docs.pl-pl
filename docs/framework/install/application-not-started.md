---
title: Rozwiązywanie problemów "Nie można uruchomić tej aplikacji"
description: Dowiedz się, co zrobić, jeśli zostanie wyświetlone okno dialogowe "Nie można uruchomić tej aplikacji".
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965909"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Rozwiązywanie problemów z komunikatem o błędzie "Nie można uruchomić tej aplikacji"

Aplikacje opracowane dla programu .NET Framework zazwyczaj wymagają zainstalowania określonej wersji programu .NET Framework w systemie. W niektórych przypadkach można podjąć próbę uruchomienia aplikacji bez zainstalowanej wersji lub oczekiwanej wersji programu .NET Framework. Często powoduje to wyświetlenie następującego okna dialogowego błędu:

![Nie można uruchomić tej aplikacji](media/application-not-started/app-could-not-be-started.png)

Zazwyczaj wskazuje to na jeden z następujących warunków:

- Instalacja platformy .NET Framework w systemie została uszkodzona.

- Nie można wykryć wersji programu .NET Framework wymaganej przez aplikację.

Aby rozwiązać ten problem, aby uruchomić aplikację, wykonaj następujące czynności:

1. Pobierz [narzędzie do naprawy programu .NET Framework (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). Narzędzie działa automatycznie po zakończeniu pobierania.

1. Jeśli narzędzie do naprawy programu .NET Framework zaleca jakąkolwiek dodatkową akcję, taką jak ta przedstawiona na poniższym rysunku, wybierz przycisk **Dalej**.

   ![Zalecane zmiany](media/application-not-started/repair-tool-recommended-changes.png)

1. Narzędzia naprawcze platformy .NET Framework są wyświetlane na poniższym rysunku, aby wskazać, że zmiany zostały zakończone. Pozostaw otwarte okno dialogowe podczas próby ponownego uruchomienia aplikacji. To powinno się udać, jeśli narzędzie do naprawy programu .NET Framework zidentyfikowało i poprawiło uszkodzoną instalację programu .NET Framework.

   ![Zalecane zmiany](media/application-not-started/repair-tool-changes-complete.png)

1. Jeśli aplikacja działa pomyślnie, wybierz przycisk **Zakończ.** W przeciwnym razie wybierz przycisk **Dalej.**

1. Jeśli wybrano przycisk **Dalej,** narzędzie .NET Framework Repair Tool wyświetla następujące okno dialogowe. Wybierz przycisk **Zakończ,** aby wysłać informacje diagnostyczne do firmy Microsoft.

   ![Nie można rozwiązać problemu](media/application-not-started/repair-tool-no-resolution.png)

1. Jeśli nadal nie można uruchomić aplikacji, zainstaluj najnowszą wersję programu .NET Framework obsługiwanego przez twoją wersję systemu Windows, jak pokazano w poniższej tabeli.

   |Wersja systemu Windows|Instalacja programu .NET Framework|
   |---|---|
   |Rocznicowa aktualizacja systemu Windows 10 i nowsze wersje|[.NET Framework 4.8 Środowisko uruchomieniowe](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 Aktualizacja listopadowa|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Framework 4.8 Środowisko uruchomieniowe](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 z dodatkiem SP1|[.NET Framework 4.8 Środowisko uruchomieniowe](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista z dodatkiem SP2|[Program .NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > Program .NET Framework 4.8 jest preinstalowany w systemie Windows 10 May 2019 Update.

1. Spróbuj uruchomić aplikację.

1. W niektórych przypadkach może zostać wyświetlone okno dialogowe, takie jak następujące, w którym zostanie wyświetlony komunikat o zainstalowaniu programu .NET Framework 3.5. Wybierz **opcję Pobierz i zainstaluj tę funkcję,** aby zainstalować program .NET Framework 3.5, a następnie ponownie uruchom aplikację.

   ![Nie można rozwiązać problemu](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Zobacz też

- [Wymagania systemowe programu .NET Framework](../get-started/system-requirements.md)
- [Przewodnik po instalacji programu .NET Framework](index.md)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
