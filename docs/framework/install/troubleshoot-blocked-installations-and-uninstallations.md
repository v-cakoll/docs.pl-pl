---
title: "Rozwiązywanie problemów z zablokowaną .NET Framework i odinstalowywaniem programu"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 850cae7d0d9739bc97770934050f514d5266fb3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Rozwiązywanie problemów z zablokowaną .NET Framework i odinstalowywaniem programu

Po uruchomieniu [sieci web lub w trybie offline Instalatora](../../../docs/framework/install/guide-for-developers.md) dla platformy .NET Framework 4.5 lub nowszy, mogą wystąpić problem, który uniemożliwia lub blokuje instalację programu .NET Framework. Poniższa tabela zawiera listę możliwych problemów z blokowaniem oraz łącza do informacji dotyczących rozwiązywania problemów.

W systemie Windows 8 i nowszych wersji programu .NET Framework jest składnikiem systemu operacyjnego i nie można odinstalować niezależnie. Aktualizacje programu .NET Framework są wyświetlane w **zainstalowane aktualizacje** Panelu sterowania na karcie **programy i funkcje** aplikacji. Dla systemów operacyjnych, na których nie jest preinstalowany programu .NET Framework, .NET Framework jest wyświetlana w **Odinstaluj lub zmień program** kartę (lub **Dodaj lub usuń programy** kartę) z  **Programy i funkcje** aplikacji w Panelu sterowania. Aby uzyskać informacji o wersji systemu Windows, na których jest preinstalowany programu .NET Framework, zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).

> [!IMPORTANT]
> Ponieważ wersje programu .NET Framework 4.x są aktualizacje w miejscu, nie można zainstalować starszej wersji programu .NET Framework 4.x w systemie jest już zainstalowana nowsza wersja. Na przykład w systemie Windows 10 spadek twórców aktualizacji, nie można zainstalować programu .NET Framework 4.6.2, ponieważ .NET Framework 4.7.1 jest wstępnie zainstalowane w systemie operacyjnym.

Aby ustalić, które wersje programu .NET Framework są zainstalowane w systemie. Zobacz [porady: ustalić, które .NET Framework są zainstalowane wersje](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) Aby uzyskać więcej informacji.

W tej tabeli 4.5. *x* odwołuje się do programu .NET Framework 4.5 oraz jego wersje punktu, 4.5.1, 4.5.2 i 4.6. *x* odwołuje się do programu .NET Framework 4.6 i jego wersje punktu 4.6.1 i 4.6.2 i 4.7. *x* odwołuje się do .NET Framework 4.7 i wydanie punktu 4.7.1.

|Komunikat związany z blokowaniem|Aby uzyskać więcej informacji lub rozwiązać problem|  
|----------------------|--------------------------------------------------|  
|Odinstalowanie programu Microsoft .NET Framework może spowodować, że niektóre aplikacje przestaną działać.|Ogólnie rzecz biorąc, nie należy odinstalowywać żadnych wersji programu .NET Framework, które są zainstalowane na komputerze, ponieważ używana aplikacja może zależeć od określonej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework dla użytkowników](../../../docs/framework/get-started/index.md#ForUsers) w *wprowadzenie* przewodnik.|  
|.NET framework 4.5*x*/4.6*.x*  /4.7 (ENU) lub jego nowsza wersja jest już zainstalowana na tym komputerze.|Nie trzeba podejmować żadnych działań.<br /><br /> Aby ustalić, które wersje programu .NET Framework są zainstalowane w systemie, zobacz [porady: ustalić, które .NET Framework są zainstalowane wersje](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).|  
|.NET Framework 4.5*x*/4.6*x*/4,7*x* (*języka*) wymaga programu .NET Framework 4.5*.x*/4.6*x*/4,7*.x*. Zainstaluj program .NET Framework 4.5*x*/4.6*x*/4,7*.x* z Centrum pobierania i uruchom ponownie Instalatora.|Należy zainstalować angielską wersję językową określonej wersji .NET Framework, przed zainstalowaniem pakietu językowego. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [zainstalować pakiety językowe](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs) w podręczniku instalacji.|  
|Nie można zainstalować program .NET Framework 4.5*x*/4.6*x*/4,7*.x*. Inne aplikacje na komputerze są niezgodne z tym programem.<br /><br /> —lub—<br /><br /> Inne aplikacje na komputerze są niezgodne z tym programem.|Najbardziej prawdopodobną przyczyną tego komunikatu jest to, że na komputerze została zainstalowana wersja zapoznawcza lub wersja RC programu .NET Framework. Odinstaluj Podgląd lub wersji RC, a następnie ponownie uruchom Instalatora.|  
|.NET framework 4.5*x*/4.6*.x*  /4.7 nie można odinstalować za pomocą tego pakietu. Aby odinstalować program .NET Framework 4.5*x*/4.6*x* z komputera, przejdź do **Panelu sterowania**, wybierz **programy i funkcje**, wybierz pozycję **Wyświetl zainstalowane aktualizacje**, wybierz pozycję Update for Microsoft Windows (KB2828152), a następnie wybierz pozycję **Odinstaluj**.|Podczas instalowania pakietu nie Odinstaluj Podgląd lub RC wersje programu .NET Framework.<br /><br /> Odinstaluj Podgląd lub RC zwolnienia z Panelu sterowania.|  
|Nie można odinstalować programu .NET Framework 4.5*x*/4.6*x*/4,7*.x*. Zależą od niego inne aplikacje zainstalowane na tym komputerze.|Ogólnie rzecz biorąc nie należy odinstalować wszelkie wersje programu .NET Framework z tego komputera, ponieważ używanej aplikacji może zależeć od określonej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework dla użytkowników](../../../docs/framework/get-started/index.md#ForUsers) w *wprowadzenie* przewodnik.|  
|.NET Framework 4.5*x*/4.6*x*/4,7*.x* redistributable nie ma zastosowania do tego systemu operacyjnego. Pobierz program .NET Framework 4.5*x*/4.6*x*/4,7*.x* systemu operacyjnego z Microsoft Download Center.|Użytkownik może próbować zainstalować [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, lub 4.7.1 na platformie, która nie jest obsługiwana lub użytkownik wybrał pakietu instalacyjnego, który nie zawiera składników dla wszystkich obsługiwanych systemów operacyjnych. Ponownie uruchom instalację przy użyciu Instalatora w trybie offline ([dla 4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=309493), [dla 4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706), [dla 4.6](http://go.microsoft.com/fwlink/p/?LinkId=528233), [dla 4.6.1](http://go.microsoft.com/fwlink/p/?LinkId=671744), dla [ 4.6.2](http://go.microsoft.com/fwlink/p/?LinkId=780604), dla [4.7](http://go.microsoft.com/fwlink/p/?LinkId=825306)), lub [4.7.1](http://go.microsoft.com/fwlink/p/?LinkId=852090). Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji](../../../docs/framework/install/guide-for-developers.md) i [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.|  
|Aktualizacja odpowiadający KB\<*numer*> musi być zainstalowany przed zainstalowaniem tego produktu.|Instalacja platformy .NET wymaga zainstalowania aktualizacji KB przed zainstalowaniem programu .NET Framework. Zainstaluj aktualizację, a następnie rozpocznij ponownie instalację .NET Framework.<br /><br /> Na przykład instalacji zaktualizowane wersje programu .NET Framework na Windows 8.1, Windows RT 8.1 i Windows Server 2012 R2 wymaga aktualizacji odpowiadający [KB 2919355](https://support.microsoft.com/kb/2919355) można zainstalować.|  
|Na tym komputerze jest obecnie uruchomiona instalacja Server Core systemu operacyjnego Windows Server 2008. .NET Framework 4.5. *x* wymaga nowszej wersji systemu operacyjnego. Zainstaluj system Windows Server 2008 R2 z dodatkiem SP1 lub nowszym i ponownie uruchom środowisko .NET Framework 4.5. *x* Instalatora.|[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] i 4.5.2 są obsługiwane w roli Server Core z systemu Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  
|Nie masz wystarczających uprawnień, aby zakończyć tę operację dla wszystkich użytkowników tego komputera. Zaloguj się jako administrator, a następnie ponownie uruchom **Instalatora**.|Musisz być administratorem na danym komputerze, aby zainstalować program .NET Framework.|  
|Instalator nie może kontynuować działania, ponieważ poprzednia instalacja wymaga ponownego uruchomienia tego komputera. Uruchom ponownie komputer i uruchom ponownie Instalatora.|Czasami jest wymagane ponowne uruchomienie w pełni ukończenie instalacji. Postępuj zgodnie z instrukcjami, aby ponownie uruchomić komputer i uruchom ponownie Instalatora.<br /><br /> W rzadkich przypadkach może się prośba o ponowne uruchomienie systemu więcej niż raz Jeśli wykrył, że liczba brakujących aktualizacji systemu Windows jest uruchamiana ponownie, aby zainstalować Następna aktualizacja w kolejce.|  
|Instalator programu .NET Framework nie może działać w trybie zgodności programów.|Zobacz [problemów zgodności programów](#compat) sekcji w dalszej części tego artykułu.|  
|.NET framework 4.5*x*/4.6*x*/4,7*.x* nie został zainstalowany, ponieważ Magazyn składników jest uszkodzony.|Zobacz [błędy napraw aktualizacji systemu Windows za pomocą narzędzia DISM lub gotowości aktualizacji systemu](https://support.microsoft.com/en-us/kb/947821) Aby uzyskać więcej informacji.|  
|Nie można uruchomić Instalatora, ponieważ na komputerze nie jest dostępna usługa Instalatora Windows.|Zobacz [błąd usługi Instalatora systemu Windows podczas instalowania lub aktualizowania programy](http://go.microsoft.com/fwlink/p/?LinkId=248684) w witrynie sieci Web Microsoft Support.|  
|Instalator może nie działać poprawnie, ponieważ na tym komputerze nie jest dostępna usługa Windows Update.|Komputer mógł zostać skonfigurowany do korzystania z programu Windows Server Update Services (WSUS), a nie z usługi Microsoft Windows Update. Aby uzyskać więcej informacji, zobacz sekcję dla kodu błędu 0x800F0906 w [kody błędów podczas próby zainstalowania programu .NET Framework 3.5 w systemie Windows 8 lub Windows Server 2012](http://support.microsoft.com/kb/2734782).<br /><br /> Zobacz też [jak uzyskać najnowszą wersję programu Windows Update Agent, aby ułatwić zarządzanie aktualizacji na komputerze](http://go.microsoft.com/fwlink/p/?LinkId=248437) w witrynie sieci Web Microsoft Support.|  
|Instalator może nie działać poprawnie, ponieważ na tym komputerze nie jest dostępna usługa inteligentnego transferu w tle.|Zobacz [aktualizacji, aby uniknąć awarii usługi inteligentnego transferu w tle (BITS) na komputerze z systemem Windows Vista](http://go.microsoft.com/fwlink/p/?LinkId=248680) w witrynie sieci Web Microsoft Support.|  
|Instalator może nie działać poprawnie, ponieważ aktualizacja systemu Windows napotkała błąd i wyświetlony kod błędu 0x80070643 lub 0x643.|Zobacz [błąd instalacji aktualizacji dla programu .NET Framework: "0x80070643" lub "0x643"](https://support.microsoft.com/kb/976982) w witrynie sieci Web Microsoft Support.|  
|.NET Framework 4.5. *x*/4.6*x*/4,7*.x* jest już częścią tego systemu operacyjnego. Nie należy zainstalować program .NET Framework 4.5*x*/4.6*x*/4,7*.x* do dystrybucji.|Nie trzeba podejmować żadnych działań.<br /><br /> Aby ustalić, które wersje programu .NET Framework są zainstalowane w systemie, zobacz [porady: ustalić, które .NET Framework są zainstalowane wersje](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md). Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.|  
|.NET Framework 4.5*x*/4.6*x*/4,7*.x* nie jest obsługiwany w tym systemie operacyjnym.|Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.<br /><br /> Dotyczące nieudanych instalacji programu .NET Framework w systemie Windows 7 ten komunikat oznacza zwykle, że nie jest zainstalowany system Windows 7 z dodatkiem SP1. W systemach Windows 7 .NET Framework wymaga systemu Windows 7 z dodatkiem SP1. Jeśli jesteś w systemie Windows 7 i nie został jeszcze zainstalowany dodatek Service Pack 1, należy to zrobić przed zainstalowaniem programu .NET Framework. Aby uzyskać informacje na temat instalowania systemu Windows 7 z dodatkiem SP1, zobacz [Dowiedz się, jak zainstalować dodatek Service Pack 1 (SP1) dla systemu Windows 7](http://windows.microsoft.com/en-us/windows7/install-windows-7-service-pack-1).|  
|Na tym komputerze jest obecnie uruchomiona instalacja Server Core systemu operacyjnego Windows Server 2008. .NET Framework 4.5. *x* wymaga pełnej wersji systemu operacyjnego lub Server Core 2008 R2 z dodatkiem SP1. Zainstaluj pełną wersję programu Windows Server 2008 z dodatkiem SP2 lub Windows Server 2008 R2 z dodatkiem SP1 lub Server Core 2008 R2 z dodatkiem SP1 i uruchom ponownie program .NET Framework 4.5. *x* Instalatora.|Program .NET Framework jest obsługiwany w roli Server Core w systemie Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  
|.NET Framework 4.5. *x* jest już częścią tego systemu operacyjnego, ale jest obecnie wyłączona ([!INCLUDE[winserver8](../../../includes/winserver8-md.md)] tylko).|Zobacz [Włącz lub wyłącz funkcje systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=248438) w witrynie sieci Web systemu Windows.|  
|Ten program instalacyjny wymaga komputera x86. Nie można go zainstalować na komputerze x64 ani IA64.|Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  
|Ten program instalacyjny wymaga komputera x64 lub x86. Nie można go instalować na komputerach IA64.|Zobacz [wymagania systemowe](../../../docs/framework/get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problemy ze zgodnością programu

Instalacja programu .NET Framework 4.5 lub jego wersje punktu kończy się niepowodzeniem z kodu błędu 1603 lub bloków uruchomionej w trybie zgodności programów systemu Windows. **Asystent zgodności programów** wskazuje, że programu .NET Framework mogą nie być zainstalowane poprawnie i wyświetli monit o ponownie ją zainstaluj przy użyciu ustawienia zalecane (tryb zgodności programów). Tryb zgodności programów mógł zostać skonfigurowany przez Asystenta zgodności programów podczas wcześniejszych nieudanych lub anulowanych prób uruchomienia Instalatora programu .NET Framework.

Instalator programu .NET Framework nie może działać w trybie zgodności programów. Aby rozwiązać ten problem blokowania, upewnij się, że ustawienie trybu zgodności nie jest włączone dla całego systemu, używając Edytora rejestru:

1. Wybierz **Start** przycisk, a następnie wybierz pozycję **Uruchom**.

1. W **Uruchom** okno dialogowe, wpisz "regedit", a następnie wybierz pozycję **OK**.

1. W Edytorze rejestru przejdź do następującego podklucza:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. W kolumnie Nazwa Wyszukaj [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7 lub 4.7.1 Pobierz nazwy, w zależności od wersji można jest instalowany i usunąć te wpisy. Pobieranie nazw, zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md) artykułu.

1. Uruchom ponownie Instalator .NET Framework w wersji 4.5, 4.5.1, 4.5.2, lub 4.6, 4.6.1, 4.6.2, 4.7 lub 4.7.1.

## <a name="see-also"></a>Zobacz także

[Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)   
[Porady: Określanie, które wersje programu .NET Framework są zainstalowane](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[Wersje i zależności](../../../docs/framework/migration-guide/versions-and-dependencies.md)
