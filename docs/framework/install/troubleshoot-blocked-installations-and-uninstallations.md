---
title: Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework
ms.date: 04/18/2019
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d96ca26ab3733999810dd48611cf10a577381f40
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859530"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework

Po uruchomieniu [sieci web lub Instalatora w trybie offline](../../../docs/framework/install/guide-for-developers.md) dla .NET Framework 4.5 lub nowszy, może wystąpić problem, który uniemożliwia lub blokuje instalację programu .NET Framework. Poniższa tabela zawiera listę możliwych problemów z blokowaniem oraz łącza do informacji dotyczących rozwiązywania problemów.

W systemie Windows 8 lub nowszym programu .NET Framework jest składnikiem systemu operacyjnego i nie można odinstalować niezależnie. Aktualizacje programu .NET Framework są wyświetlane w **zainstalowane aktualizacje** kartę tytułową Panelu sterowania **programy i funkcje** aplikacji. Dla systemów operacyjnych, na których nie jest preinstalowany programu .NET Framework, .NET Framework jest wyświetlana w **Odinstaluj lub zmień program** karty (lub **Dodaj/Usuń programy** kartę) z  **Programy i funkcje** aplikacji w Panelu sterowania. Aby uzyskać informacje na temat wersji Windows, na których jest preinstalowany programu .NET Framework, zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).

> [!IMPORTANT]
> Ponieważ wersje programu .NET Framework 4.x aktualizacji w miejscu, nie można zainstalować starszej wersji programu .NET Framework 4.x w systemie jest już zainstalowana nowsza wersja. Na przykład w systemie Windows 10 Fall Creators Update, nie można zainstalować programu .NET Framework 4.6.2, ponieważ platformy .NET Framework 4.7.1 jest preinstalowany w systemie operacyjnym.

Można określić, które wersje programu .NET Framework są zainstalowane w systemie. Zobacz [jak: Określić, które .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) Aby uzyskać więcej informacji.

W tej tabeli 4.5.x odnosi się do programu .NET Framework 4.5 i jego wydania punktowe, 4.5.1 i 4.5.2, 4.6.x odnosi się do programu .NET Framework 4.6 i jego wydania punktowe, 4.6.1 i 4.6.2, 4.7.x odnosi się do programu .NET Framework 4.7 i jego wydania punktowe, 4.7.1 i 4.7.2 , a 4.8 odwołuje się do programu .NET Framework 4.8.

|Komunikat związany z blokowaniem|Aby uzyskać więcej informacji lub rozwiązać problem|  
|----------------------|--------------------------------------------------|  
|Odinstalowanie programu Microsoft .NET Framework może spowodować, że niektóre aplikacje przestaną działać.|Ogólnie rzecz biorąc, nie należy odinstalowywać żadnych wersji programu .NET Framework, które są zainstalowane na komputerze, ponieważ używana aplikacja może zależeć od określonej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [program .NET Framework dla użytkowników](../../../docs/framework/get-started/index.md#ForUsers) w *wprowadzenie* przewodnik.|  
|.NET framework 4.5.x/4.6.x/4.7.x (ENU) lub nowsza wersja jest już zainstalowana na tym komputerze.|Nie trzeba podejmować żadnych działań.<br /><br /> Aby określić, które wersje programu .NET Framework są zainstalowane w systemie, zobacz [jak: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).|  
|4\.5.x/4.6.x/4.7.x/4.8 .NET Framework (*języka*) wymaga 4.5.x/4.6.x/4.7.x/4.8 .NET Framework. Zainstaluj 4.5.x/4.6.x/4.7.x/4.8 .NET Framework z Centrum pobierania i uruchom ponownie Instalatora.|Musisz zainstalować angielską wersję określonej wersji środowiska .NET Framework przed zainstalowaniem pakietu językowego. Aby uzyskać więcej informacji, zobacz sekcję na [Aby zainstalować pakiety językowe](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs) w podręczniku instalacji.|  
|Nie można zainstalować 4.5.x/4.6.x/4.7.x/4.8 .NET Framework. Inne aplikacje na komputerze są niezgodne z tym programem.<br /><br /> —lub—<br /><br /> Inne aplikacje na komputerze są niezgodne z tym programem.|Najbardziej prawdopodobną przyczyną tego komunikatu jest to, że na komputerze została zainstalowana wersja zapoznawcza lub wersja RC programu .NET Framework. Odinstaluj wersję zapoznawczą lub RC i uruchom ponownie Instalatora.|  
|.NET framework 4.5.x/4.6.x/4.7.x/4.8 nie można odinstalować za pomocą tego pakietu. Aby odinstalować 4.5.x/4.6.x/4.7.x/4.8 .NET Framework z komputera, przejdź do **Panelu sterowania**, wybierz **programy i funkcje**, wybierz **Wyświetl zainstalowane aktualizacje**, wybierz opcję Aktualizacja dla Microsoft Windows (KB2828152), a następnie wybierz **Odinstaluj**.|Pakiet, który jest instalowany nie odinstalowania wersji zapoznawczej ani wersji RC programu .NET Framework.<br /><br /> Odinstalowania wersji zapoznawczej ani wersji RC zwolnienia z Panelu sterowania.|  
|Nie można odinstalować 4.5.x/4.6.x/4.7.x/4.8 .NET Framework. Zależą od niego inne aplikacje zainstalowane na tym komputerze.|Ogólnie rzecz biorąc nie należy odinstalować wszelkie wersje programu .NET Framework na komputerze, ponieważ aplikacja może zależeć od określonej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [program .NET Framework dla użytkowników](../../../docs/framework/get-started/index.md#ForUsers) w *wprowadzenie* przewodnik.|  
|Pakiet redystrybucyjny 4.5.x/4.6.x/4.7.x/4.8 .NET Framework nie ma zastosowania do tego systemu operacyjnego. Pobierz 4.5.x/4.6.x/4.7.x/4.8 .NET Framework w systemie operacyjnym z Microsoft Download Center.|Być może próbujesz zainstalować program .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 lub 4.8 na platformie, która nie jest obsługiwana, lub wybrano pakiet instalacyjny, który nie zawiera składników dla wszystkich obsługiwanych systemach operacyjnych. Ponownie uruchom instalację przy użyciu Instalatora w trybie offline ([4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=309493), [dla 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706), [dla 4.6](https://go.microsoft.com/fwlink/p/?LinkId=528233), [dla 4.6.1](https://go.microsoft.com/fwlink/p/?LinkId=671744), aby uzyskać [ 4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604), dla [4.7](https://go.microsoft.com/fwlink/p/?LinkId=825306)), aby uzyskać [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090), dla [4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863265), lub [4.8](https://go.microsoft.com/fwlink/?linkid=2088631). Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji](../../../docs/framework/install/guide-for-developers.md) i [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.|  
|Aktualizacja odpowiadający KB\<*numer*> musi zostać zainstalowany przed zainstalowaniem tego produktu.|Instalacja platformy .NET Framework wymaga zainstalowania aktualizacji KB przed zainstalowaniem programu .NET Framework. Zainstaluj aktualizację, a następnie rozpocznij ponownie instalację .NET Framework.<br /><br /> Na przykład instalacji zaktualizowane wersje programu .NET Framework na Windows 8.1, Windows RT 8.1, i Windows Server 2012 R2 wymaga, aby aktualizacja odpowiadający [KB 2919355](https://support.microsoft.com/kb/2919355) można zainstalować.|  
|Na tym komputerze jest obecnie uruchomiona instalacja Server Core systemu operacyjnego Windows Server 2008. .NET Framework 4.5.x wymaga nowszej wersji systemu operacyjnego. Zainstaluj system Windows Server 2008 R2 z dodatkiem SP1 lub nowszym i ponownie uruchom Instalatora 4.5.x .NET Framework.|.NET Framework 4.5.1 i 4.5.2 są obsługiwane w roli Server Core z systemu Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  
|Nie masz wystarczających uprawnień, aby zakończyć tę operację dla wszystkich użytkowników tego komputera. Zaloguj się jako administrator i uruchom ponownie **Instalatora**.|Musisz być administratorem na danym komputerze, aby zainstalować program .NET Framework.|  
|Instalator nie może kontynuować działania, ponieważ poprzednia instalacja wymaga ponownego uruchomienia tego komputera. Uruchom ponownie komputer i uruchom ponownie Instalatora.|Czasami konieczne jest ponowne pełni ukończenie instalacji. Postępuj zgodnie z instrukcjami, aby ponownie uruchomić komputer i uruchom ponownie Instalatora.<br /><br /> W rzadkich przypadkach może prośba o więcej niż jeden raz ponowne uruchomienie systemu, jeśli Windows wykrył, że liczba brakujących aktualizacji i jest uruchamiana ponownie, aby zainstalować aktualizację dalej w kolejce.|  
|Instalator programu .NET Framework nie może działać w trybie zgodności programów.|Zobacz [problemy ze zgodnością programu](#compat) sekcję w dalszej części tego artykułu.|  
|4\.5.x/4.6.x/4.7.x/4.8 .NET framework nie został zainstalowany, ponieważ Magazyn składników jest uszkodzony.|Zobacz [aktualizacji Windows naprawić błędy za pomocą narzędzia DISM lub gotowość do aktualizacji systemu](https://support.microsoft.com/kb/947821) Aby uzyskać więcej informacji.|  
|Nie można uruchomić Instalatora, ponieważ na komputerze nie jest dostępna usługa Instalatora Windows.|Zobacz [błąd usługi Instalatora Windows podczas instalowania lub aktualizowania programów](https://go.microsoft.com/fwlink/p/?LinkId=248684) w witrynie Microsoft Support.|  
|Instalator może nie działać poprawnie, ponieważ na tym komputerze nie jest dostępna usługa Windows Update.|Komputer mógł zostać skonfigurowany do korzystania z programu Windows Server Update Services (WSUS), a nie z usługi Microsoft Windows Update. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą kodu błędu 0x800F0906 w [kody błędów podczas próby zainstalowania programu .NET Framework 3.5 w systemie Windows 8 lub Windows Server 2012](https://support.microsoft.com/kb/2734782).<br /><br /> Zobacz też [jak uzyskać najnowszą wersję usługi Windows Update Agent ułatwiającego zarządzanie aktualizacjami na komputerze](https://go.microsoft.com/fwlink/p/?LinkId=248437) w witrynie Microsoft Support.|  
|Instalator może nie działać poprawnie, ponieważ na tym komputerze nie jest dostępna usługa inteligentnego transferu w tle.|Zobacz [aktualizacja zapobiegająca awariom usługi inteligentnego transferu w tle (BITS), na komputerze z systemem Windows Vista](https://go.microsoft.com/fwlink/p/?LinkId=248680) w witrynie Microsoft Support.|  
|Instalator nie może działać prawidłowo, ponieważ aktualizacja Windows napotkał błąd i wyświetlony kod błędu 0x80070643 lub 0x643.|Zobacz [błąd instalacji aktualizacji programu .NET Framework: "0x80070643" lub "0x643"](https://support.microsoft.com/kb/976982) w witrynie Microsoft Support.|  
|4\.5.x/4.6.x/4.7.x/4.8 .NET Framework jest już częścią tego systemu operacyjnego. Nie musisz zainstalować pakiet redystrybucyjny 4.5.x/4.6.x/4.7.x/4.8 .NET Framework.|Nie trzeba podejmować żadnych działań.<br /><br /> Aby określić, które wersje programu .NET Framework są zainstalowane w systemie, zobacz [jak: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.|  
|4\.5.x/4.6.x/4.7.x/4.8 .NET Framework nie jest obsługiwana w tym systemie operacyjnym.|Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.<br /><br /> Dotyczące nieudanych instalacji programu .NET Framework w systemie Windows 7 zwykle wskazuje, czy Windows 7 z dodatkiem SP1 nie jest zainstalowana. .NET Framework wymaga w systemach Windows 7, Windows 7 z dodatkiem SP1. Jeśli znajdują się na Windows 7 i dodatkiem Service Pack 1 nie jest jeszcze zainstalowany, należy to zrobić przed zainstalowaniem programu .NET Framework. Aby uzyskać informacje na temat instalowania Windows 7 z dodatkiem SP1, zobacz [Dowiedz się, jak zainstalować Windows 7 z dodatkiem Service Pack 1 (SP1)](https://windows.microsoft.com/windows7/install-windows-7-service-pack-1).|  
|Na tym komputerze jest obecnie uruchomiona instalacja Server Core systemu operacyjnego Windows Server 2008. .NET Framework 4.5.x wymaga pełnej wersji systemu operacyjnego lub Server Core 2008 R2 z dodatkiem SP1. Zainstaluj pełną wersję systemu Windows Server 2008 z dodatkiem SP2 lub Windows Server 2008 R2 z dodatkiem SP1 lub Server Core 2008 R2 z dodatkiem SP1 i ponownie uruchom z .NET Framework 4.5.x Instalatora.|Program .NET Framework jest obsługiwany w roli Server Core w systemie Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  
|.NET Framework 4.5.x jest już częścią tego systemu operacyjnego, ale jest aktualnie wyłączony ([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] tylko).|Zobacz [Windows Włącz lub wyłącz funkcje](https://go.microsoft.com/fwlink/p/?LinkId=248438) w witrynie Windows.|  
|Ten program instalacyjny wymaga komputera x86. Nie można go zainstalować na komputerze x64 ani IA64.|Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  
|Ten program instalacyjny wymaga komputera x64 lub x86. Nie można go instalować na komputerach IA64.|Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problemy ze zgodnością programu

Instalacja programu .NET Framework 4.5 lub jego wydania punktowe kończy się niepowodzeniem z kodem błędu 1603 lub bloków uruchamianego w trybie zgodności programów Windows. **Asystent zgodności programów** wskazuje, że .NET Framework może nie został poprawnie zainstalowany i wyświetla monit o jego ponowną instalację przy użyciu zalecanego ustawienia (tryb zgodności programów). Tryb zgodności programów mógł zostać skonfigurowany przez Asystenta zgodności programów podczas wcześniejszych nieudanych lub anulowanych prób uruchomienia Instalatora programu .NET Framework.

Instalator programu .NET Framework nie może działać w trybie zgodności programów. Aby rozwiązać ten problem blokowania, należy użyć Edytora rejestru, aby upewnić się, że ustawienie trybu zgodności nie włączono całego systemu:

1. Wybierz **Start** przycisk, a następnie wybierz **Uruchom**.

1. W **Uruchom** okno dialogowe, wpisz "regedit", a następnie wybierz **OK**.

1. W Edytorze rejestru przejdź do następującego podklucza:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. W kolumnie Nazwa Wyszukaj programu .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, lub 4.7.2 pobieranie nazw, w zależności od tego, która wersja jest instalowana i usuń te wpisy. Pobieranie nazwy opisano w artykule [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md) artykułu.

1. Uruchom ponownie Instalatora programu .NET Framework w wersji 4.5, 4.5.1, 4.5.2, lub 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1 lub 4.7.2.

## <a name="see-also"></a>Zobacz także

- [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)
- [Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)
- [Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)
