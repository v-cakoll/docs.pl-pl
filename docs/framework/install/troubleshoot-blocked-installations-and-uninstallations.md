---
title: Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework
ms.date: 04/18/2019
ms.custom: updateeachrelease
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
ms.openlocfilehash: e602e0f0603637659b7d18d75e66547dcd946c54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123759"
---
# <a name="troubleshoot-blocked-net-framework-installations-and-uninstallations"></a>Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework

Po uruchomieniu [Instalatora sieci Web lub offline](guide-for-developers.md) dla .NET Framework 4,5 lub nowszej wersji może wystąpić problem, który uniemożliwia lub blokuje instalację .NET Framework. Poniższa tabela zawiera listę możliwych problemów z blokowaniem oraz łącza do informacji dotyczących rozwiązywania problemów.

W systemie Windows 8 i nowszych .NET Framework to składnik systemu operacyjnego i nie może zostać odinstalowany niezależnie. Aktualizacje .NET Framework są wyświetlane na karcie **zainstalowane aktualizacje** w aplecie **programy i funkcje** aplikacji. W przypadku systemów operacyjnych, w których nie zainstalowano .NET Framework, .NET Framework pojawia się na karcie **Odinstaluj lub zmień program** (lub kartę **Dodaj/Usuń programy** ) w aplikacji **program i funkcje** w panelu sterowania. Aby uzyskać informacje na temat wersji systemu Windows, na których zainstalowano .NET Framework, zobacz [wymagania systemowe](../get-started/system-requirements.md).

> [!IMPORTANT]
> Ponieważ wersje 4. x .NET Framework są aktualizacjami w miejscu, nie można zainstalować starszej wersji .NET Framework 4. x w systemie, na którym jest już zainstalowana nowsza wersja. Na przykład w systemie z aktualizacją dla twórców systemu Windows 10 nie można zainstalować .NET Framework 4.6.2, ponieważ .NET Framework 4.7.1 jest preinstalowany z systemem operacyjnym.

Możesz określić, które wersje .NET Framework są zainstalowane w systemie. Zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md) , aby uzyskać więcej informacji.

W tej tabeli 4.5. x odnosi się do .NET Framework 4,5 i jego punktów, 4.5.1 i 4.5.2, 4.6. x odnosi się do .NET Framework 4,6 i jego wydań punktowych, 4.6.1 i 4.6.2, 4,7. x odnosi się do .NET Framework 4,7 i jego wydań punktów, 4.7.1 i 4.7.2 , i 4,8 odnosi się do .NET Framework 4,8.

|Komunikat związany z blokowaniem|Aby uzyskać więcej informacji lub rozwiązać problem|  
|----------------------|--------------------------------------------------|  
|Odinstalowanie programu Microsoft .NET Framework może spowodować, że niektóre aplikacje przestaną działać.|Ogólnie rzecz biorąc, nie należy odinstalowywać żadnych wersji programu .NET Framework, które są zainstalowane na komputerze, ponieważ używana aplikacja może zależeć od określonej wersji programu .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework dla użytkowników](../get-started/index.md#ForUsers) w przewodniku *wprowadzenie* .|  
|Na tym komputerze jest już zainstalowana .NET Framework 4.5. x/4.6. x/4.7. x (plk) lub nowsza.|Nie trzeba podejmować żadnych działań.<br /><br /> Aby określić, które wersje .NET Framework są zainstalowane w systemie, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md).|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 (*Język*) wymaga .NET Framework 4.5. x/4.6. x/4.7. x/4.8. Zainstaluj .NET Framework 4.5. x/4.6. x/4.7. x/4.8 z centrum pobierania i uruchom ponownie Instalatora.|Przed zainstalowaniem pakietu językowego należy zainstalować angielską wersję .NET Framework określonej wersji. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [instalowania pakietów językowych](guide-for-developers.md#to-install-language-packs) w podręczniku instalacji programu.|  
|Nie można zainstalować .NET Framework 4.5. x/4.6. x/4.7. x/4.8. Inne aplikacje na komputerze są niezgodne z tym programem.<br /><br /> —lub—<br /><br /> Inne aplikacje na komputerze są niezgodne z tym programem.|Najbardziej prawdopodobną przyczyną tego komunikatu jest to, że na komputerze została zainstalowana wersja zapoznawcza lub wersja RC programu .NET Framework. Odinstaluj wersję zapoznawczą lub RC i uruchom ponownie Instalatora.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 nie można odinstalować za pomocą tego pakietu. Aby odinstalować .NET Framework 4.5. x/4.6. x/4.7. x/4.8 z komputera, przejdź do **Panelu sterowania**, wybierz **aplet Programy i funkcje**, wybierz opcję **Wyświetl zainstalowane aktualizacje**, wybierz pozycję Aktualizuj dla systemu Microsoft Windows (KB2828152), a następnie wybierz pozycję  **Odinstaluj**.|Instalowany pakiet nie Odinstalowuje wersji zapoznawczej ani wersji RC .NET Framework.<br /><br /> Odinstaluj wersję zapoznawczą lub wydanie RC z panelu sterowania.|  
|Nie można odinstalować .NET Framework 4.5. x/4.6. x/4.7. x/4.8. Zależą od niego inne aplikacje zainstalowane na tym komputerze.|Ogólnie rzecz biorąc nie należy odinstalowywać żadnych wersji .NET Framework z komputera, ponieważ używana aplikacja może zależeć od określonej wersji .NET Framework. Aby uzyskać więcej informacji, zobacz [.NET Framework dla użytkowników](../get-started/index.md#ForUsers) w przewodniku *wprowadzenie* .|  
|Pakiet redystrybucyjny .NET Framework 4.5. x/4.6. x/4.7. x/4.8 nie ma zastosowania do tego systemu operacyjnego. Pobierz .NET Framework 4.5. x/4.6. x/4.7. x/4.8 dla systemu operacyjnego z centrum pobierania Microsoft.|Być może podjęto próbę instalacji .NET Framework 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1, 4.7.2 lub 4,8 na platformie, która nie jest obsługiwana, lub wybrano pakiet instalacyjny, który nie zawiera składników dla wszystkich obsługiwanych systemów operacyjnych. Uruchom instalację [ponownie, korzystając](https://go.microsoft.com/fwlink/p/?LinkId=397706)z Instalatora w trybie offline ([dla wersji 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=309493)dla wersji [4,6](https://go.microsoft.com/fwlink/p/?LinkId=528233), dla wersji [4.6.1](https://go.microsoft.com/fwlink/p/?LinkId=671744)dla [4.6.2](https://go.microsoft.com/fwlink/p/?LinkId=780604), dla [4,7](https://go.microsoft.com/fwlink/p/?LinkId=825306)), dla [4.7.1](https://go.microsoft.com/fwlink/p/?LinkId=852090), dla [4.7.2](https://go.microsoft.com/fwlink/p/?LinkId=863265)lub dla [4,8](https://go.microsoft.com/fwlink/?linkid=2088631). Aby uzyskać więcej informacji, zobacz [Przewodnik instalacji](guide-for-developers.md) i [wymagania systemowe](../get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.|  
|Aby można było zainstalować ten produkt, należy zainstalować aktualizację odpowiadającą\<KB > *numer*.|Instalacja .NET Framework wymaga zainstalowania aktualizacji KB przed zainstalowaniem .NET Framework. Zainstaluj aktualizację, a następnie ponownie rozpocznij instalację .NET Framework.<br /><br /> Na przykład instalacja zaktualizowanych wersji .NET Framework w systemach Windows 8.1, Windows RT 8,1 i Windows Server 2012 R2 wymaga zainstalowania aktualizacji odpowiadającej [KB 2919355](https://support.microsoft.com/kb/2919355) .|  
|Na tym komputerze jest obecnie uruchomiona instalacja Server Core systemu operacyjnego Windows Server 2008. .NET Framework 4.5. x wymaga nowszej wersji systemu operacyjnego. Zainstaluj system Windows Server 2008 R2 z dodatkiem SP1 lub nowszy i uruchom ponownie Instalatora programu .NET Framework 4.5. x.|.NET Framework 4.5.1 i 4.5.2 są obsługiwane w roli Server Core z systemem Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [wymagania systemowe](../get-started/system-requirements.md).|  
|Nie masz wystarczających uprawnień, aby zakończyć tę operację dla wszystkich użytkowników tego komputera. Zaloguj się jako administrator i ponownie uruchom **Instalatora**.|Musisz być administratorem na danym komputerze, aby zainstalować program .NET Framework.|  
|Instalator nie może kontynuować działania, ponieważ poprzednia instalacja wymaga ponownego uruchomienia tego komputera. Uruchom ponownie komputer i uruchom ponownie Instalatora.|Czasami wymagane jest ponowne uruchomienie w celu pełnego ukończenia instalacji. Postępuj zgodnie z instrukcjami, aby ponownie uruchomić komputer i ponownie uruchomić Instalatora.<br /><br /> W rzadkich przypadkach może zostać wyświetlony monit o ponowne uruchomienie systemu więcej niż raz, jeśli system Windows wykryje liczbę brakujących aktualizacji i ponownie uruchomi instalację następnej aktualizacji w kolejce.|  
|Instalator programu .NET Framework nie może działać w trybie zgodności programów.|Zobacz sekcję [problemy ze zgodnością programu](#compat) w dalszej części tego artykułu.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 nie został zainstalowany, ponieważ magazyn składników został uszkodzony.|Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z błędami Windows Update przy użyciu narzędzia DISM lub gotowości aktualizacji systemu](https://support.microsoft.com/kb/947821) .|  
|Nie można uruchomić Instalatora, ponieważ na komputerze nie jest dostępna usługa Instalatora Windows.|Zobacz [błąd usługi Instalator Windows podczas instalowania lub aktualizowania programów](https://go.microsoft.com/fwlink/p/?LinkId=248684) w witrynie Pomoc techniczna firmy Microsoft.|  
|Instalator może nie działać poprawnie, ponieważ na tym komputerze nie jest dostępna usługa Windows Update.|Komputer mógł zostać skonfigurowany do korzystania z programu Windows Server Update Services (WSUS), a nie z usługi Microsoft Windows Update. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą kodu błędu 0x800F0906 w [kodach błędów podczas próby zainstalowania .NET Framework 3,5 w systemie Windows 8 lub Windows Server 2012](https://support.microsoft.com/kb/2734782).<br /><br /> Zobacz również [, jak uzyskać najnowszą wersję agenta Windows Update, aby ułatwić zarządzanie aktualizacjami na komputerze](https://go.microsoft.com/fwlink/p/?LinkId=248437) w witrynie Pomoc techniczna firmy Microsoft.|  
|Instalator może nie działać poprawnie, ponieważ na tym komputerze nie jest dostępna usługa inteligentnego transferu w tle.|Zapoznaj się z [aktualizacją, aby zapobiec awarii usługa inteligentnego transferu w tle (BITS) na komputerze z systemem Windows Vista](https://go.microsoft.com/fwlink/p/?LinkId=248680) w witrynie sieci Pomoc techniczna firmy Microsoft.|  
|Instalator może nie działać prawidłowo, ponieważ usługa Windows Update napotkała błąd i został wyświetlony kod błędu 0x80070643 lub 0x643.|Zobacz [.NET Framework błąd instalacji aktualizacji: "0x80070643" lub "0x643"](https://support.microsoft.com/kb/976982) w witrynie Pomoc techniczna firmy Microsoft.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 jest już częścią tego systemu operacyjnego. Nie trzeba instalować pakietu redystrybucyjnego programu .NET Framework 4.5. x/4.6. x/4.7. x/4.8.|Nie trzeba podejmować żadnych działań.<br /><br /> Aby określić, które wersje .NET Framework są zainstalowane w systemie, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md). Zobacz [wymagania systemowe](../get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.|  
|.NET Framework 4.5. x/4.6. x/4.7. x/4.8 nie jest obsługiwany w tym systemie operacyjnym.|Zobacz [wymagania systemowe](../get-started/system-requirements.md) dla obsługiwanych systemów operacyjnych.<br /><br /> W przypadku nieudanych instalacji .NET Framework w systemie Windows 7 ten komunikat zazwyczaj wskazuje, że nie zainstalowano systemu Windows 7 z dodatkiem SP1. W systemach Windows 7 .NET Framework wymaga systemu Windows 7 z dodatkiem SP1. Jeśli korzystasz z systemu Windows 7 i jeszcze nie zainstalowano dodatku Service Pack 1, musisz to zrobić przed zainstalowaniem .NET Framework. Aby uzyskać więcej informacji na temat instalowania systemu Windows 7 z dodatkiem SP1, zobacz temat [jak zainstalować system Windows 7 z dodatkiem Service Pack 1 (SP1)](https://windows.microsoft.com/windows7/install-windows-7-service-pack-1).|  
|Na tym komputerze jest obecnie uruchomiona instalacja Server Core systemu operacyjnego Windows Server 2008. .NET Framework 4.5. x wymaga pełnej wersji systemu operacyjnego lub Server Core 2008 R2 z dodatkiem SP1. Zainstaluj pełną wersję systemu Windows Server 2008 z dodatkiem SP2 lub Windows Server 2008 R2 z dodatkiem SP1 lub Server Core 2008 R2 SP1 i ponownie uruchom Instalatora programu .NET Framework 4.5. x.|Program .NET Framework jest obsługiwany w roli Server Core w systemie Windows Server 2008 R2 z dodatkiem SP1 lub nowszym. Zobacz [wymagania systemowe](../get-started/system-requirements.md).|  
|.NET Framework 4.5. x jest już częścią tego systemu operacyjnego, ale jest obecnie wyłączony (tylko[!INCLUDE[winserver8](../../../includes/winserver8-md.md)]).|Zobacz [Włączanie lub wyłączanie funkcji systemu Windows](https://go.microsoft.com/fwlink/p/?LinkId=248438) w witrynie sieci Web systemu Windows.|  
|Ten program instalacyjny wymaga komputera x86. Nie można go zainstalować na komputerze x64 ani IA64.|Zobacz [wymagania systemowe](../get-started/system-requirements.md).|  
|Ten program instalacyjny wymaga komputera x64 lub x86. Nie można go instalować na komputerach IA64.|Zobacz [wymagania systemowe](../get-started/system-requirements.md).|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>Problemy ze zgodnością programu

Instalacja .NET Framework 4,5 lub jego wydań punktów kończy się niepowodzeniem z kodem błędu 1603 lub bloków, gdy jest uruchomiony w trybie zgodności programów systemu Windows. **Asystent zgodności programu** wskazuje, że .NET Framework być może nie został poprawnie zainstalowany i zostanie wyświetlony komunikat z prośbą o jej ponowne zainstalowanie przy użyciu zalecanego ustawienia (tryb zgodności programów). Tryb zgodności programów mógł zostać skonfigurowany przez Asystenta zgodności programów podczas wcześniejszych nieudanych lub anulowanych prób uruchomienia Instalatora programu .NET Framework.

Instalator programu .NET Framework nie może działać w trybie zgodności programów. Aby rozwiązać ten problem blokowania, należy użyć Edytora rejestru, aby upewnić się, że ustawienie trybu zgodności nie jest włączone dla całego systemu:

1. Wybierz przycisk **Start** , a następnie wybierz polecenie **Uruchom**.

1. W oknie dialogowym **Uruchamianie** wpisz ciąg "regedit", a następnie wybierz przycisk **OK**.

1. W Edytorze rejestru przejdź do następującego podklucza:

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. W kolumnie Nazwa poszukaj .NET Framework 4,5, 4.5.1, 4.5.2, 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1 lub 4.7.2, w zależności od tego, która wersja jest instalowana, i usuń te wpisy. Aby uzyskać nazwy plików do pobrania, zobacz artykuł [Install the .NET Framework for Developers](guide-for-developers.md) .

1. Uruchom ponownie Instalatora .NET Framework w wersji 4,5, 4.5.1, 4.5.2 lub 4,6, 4.6.1, 4.6.2, 4,7, 4.7.1 lub 4.7.2.

## <a name="see-also"></a>Zobacz także

- [Zainstaluj .NET Framework dla deweloperów](guide-for-developers.md)
- [Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane](../migration-guide/how-to-determine-which-versions-are-installed.md)
- [Wersje i zależności](../migration-guide/versions-and-dependencies.md)
