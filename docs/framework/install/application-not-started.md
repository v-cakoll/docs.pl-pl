---
title: Rozwiązywanie problemów — nie można uruchomić tej aplikacji
description: Dowiedz się, co zrobić, Jeśli zobaczysz okno dialogowe "nie można uruchomić tej aplikacji".
author: rpetrusha
ms.author: ronpet
ms.date: 09/05/2019
ms.openlocfilehash: 2534979e8dea886c2d7298c57e12b66d7a962c69
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401705"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Rozwiązywanie problemów z komunikatem o błędzie "nie można uruchomić tej aplikacji"

Aplikacje opracowane dla .NET Framework zwykle wymagają, aby w systemie była zainstalowana określona wersja .NET Framework. W niektórych przypadkach może zostać podjęta próba uruchomienia aplikacji bez zainstalowanej wersji lub oczekiwanej wersji .NET Framework. Powoduje to często Generowanie okna dialogowego błędu w następujący sposób:

![Nie można uruchomić tej aplikacji](media/application-not-started/app-could-not-be-started.png)

Zwykle wskazuje jeden z następujących warunków:

- Instalacja .NET Framework w systemie uległa uszkodzeniu.

- Nie można wykryć wersji .NET Framework wymaganej przez aplikację.

Aby rozwiązać ten problem, możesz uruchomić aplikację, wykonując następujące czynności:

1. Pobierz [Narzędzie do naprawy .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135). Narzędzie jest uruchamiane automatycznie po zakończeniu pobierania.

1. Jeśli narzędzie do naprawy .NET Framework zaleca wykonanie dodatkowych czynności, takich jak pokazane na poniższej ilustracji, wybierz pozycję **dalej**.

   ![Zalecane zmiany](media/application-not-started/repair-tool-recommended-changes.png)

1. Narzędzia do naprawy .NET Frameworką wyświetla okno dialogowe pokazane na poniższym rysunku, aby wskazać, że zmiany zostały wykonane. Pozostaw to okno dialogowe otwarte, aby spróbować ponownie uruchomić aplikację. Powinno to powieść się, jeśli narzędzie do naprawy .NET Framework zidentyfikowała i naprawił uszkodzoną instalację .NET Framework.

   ![Zalecane zmiany](media/application-not-started/repair-tool-changes-complete.png)

1. Jeśli aplikacja zostanie uruchomiona pomyślnie, wybierz przycisk **Zakończ** . W przeciwnym razie wybierz przycisk **dalej** .

1. W przypadku wybrania przycisku **dalej** narzędzie .NET Framework Repair wyświetli okno dialogowe, takie jak poniższe. Wybierz przycisk **Zakończ** , aby wysłać informacje diagnostyczne do firmy Microsoft.

   ![Nie można rozwiązać problemu](media/application-not-started/repair-tool-no-resolution.png)

1. Jeśli nadal nie można uruchomić aplikacji, zainstaluj najnowszą wersję .NET Framework obsługiwaną przez daną wersję systemu Windows, jak pokazano w poniższej tabeli.

   |Wersja systemu Windows|Instalacja .NET Framework|
   |---|---|
   |Rocznicowa Aktualizacja systemu Windows 10 i nowsze wersje|[Środowisko uruchomieniowe .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Aktualizacja systemu Windows 10, Windows 10 listopad|[.NET Framework 4.6.2](https://www.microsoft.com/download/details.aspx?id=53345)|
   |Windows 8.1|[Środowisko uruchomieniowe .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981)|
   |Windows 7 z dodatkiem SP1|[Środowisko uruchomieniowe .NET Framework 4,8](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista z dodatkiem SP2|[.NET Framework 4.6](https://www.microsoft.com/download/details.aspx?id=48130)|

   > [!NOTE]
   >  .NET Framework 4,8 jest preinstalowany w systemie Windows 10 maja 2019 Update.

1. Podjęto próbę uruchomienia aplikacji.

1. W niektórych przypadkach może zostać wyświetlone okno dialogowe podobne do poniższego, które prosi o zainstalowanie .NET Framework 3,5. Wybierz pozycję **Pobierz i zainstaluj tę funkcję** , aby zainstalować .NET Framework 3,5, a następnie ponownie uruchom aplikację.

   ![Nie można rozwiązać problemu](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Zobacz także

- [Wymagania systemowe .NET Framework](../get-started/system-requirements.md)
- [Przewodnik instalacji .NET Framework](index.md)
- [Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
