---
title: Interpretowanie kodów błędów zwróconych przez program wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 9df059618b45ae65ffb3e6e31a87d5531c79d947
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretowanie kodów błędów zwróconych przez program wsatConfig.exe
W tym temacie wymieniono wszystkie kody błędów wygenerowanych przez narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe) i zalecane akcje do wykonania.  
  
## <a name="list-of-error-codes"></a>Listę kodów błędów  
  
|Kod błędu|Opis|Zalecana akcja do wykonania|  
|----------------|-----------------|------------------------------------|  
|0|Operacja zakończyła się pomyślnie|Brak|  
|1|Wystąpił nieoczekiwany błąd|Kontakt z firmą Microsoft|  
|2|Wystąpił nieoczekiwany błąd podczas próby skontaktowania się z usługi MSDTC, aby pobrać jego ustawień zabezpieczeń.|Upewnij się, że usługa MSDTC nie jest wyłączone i rozwiąż wszystkie problemy na liście zwrócony wyjątek.|  
|3|Konto, z którego uruchomiono WsatConfig.exe nie miał wystarczających uprawnień do odczytu ustawień zabezpieczeń sieci.|Wykonanie WsatConfig.exe przy użyciu konta użytkownika Administrator.|  
|4|Włącz "Usługa DTC Network Access" dla usługi MSDTC, przed podjęciem próby włączyć obsługę protokołu WS-AT.|Włącz "Usługa DTC Network Access" dla usługi MSDTC i uruchom ponownie narzędzie.|  
|5|Wprowadzona portu jest poza zakresem. Wartość musi należeć do zakresu od 1 do 65535.|Popraw `-port:<portNum>`<br /><br /> Opcja wiersza polecenia opisane w komunikacie o błędzie.|  
|6|Certyfikat nieprawidłowy punkt końcowy został określony w wierszu polecenia.  Nie można odnaleźć certyfikatu lub nie przeszedł pomyślnie weryfikacji.|Popraw `-endpointCert` opcji wiersza polecenia. Upewnij się, że certyfikat ma klucz prywatny, jest przeznaczona do użycia dla uwierzytelniania klienta i ServerAuthentication jest zainstalowany w magazynie certyfikatów LocalMachine\MY i jest w pełni zaufany.|  
|7|Certyfikat nieprawidłowe konta została określona w wierszu polecenia.|Popraw `-accountsCerts` opcji wiersza polecenia. Określony certyfikat został niepoprawnie określone lub nie można go znaleźć.|  
|8|Domyślny limit czasu został określony do zakresu od 1 do 3600 sekund.|Wprowadź poprawną domyślną wartość limitu czasu wskazane.|  
|10|Wystąpił nieoczekiwany błąd podczas próby uzyskania dostępu do rejestru.|Sprawdź komunikat o błędzie i kod błędu dla elementów z możliwością wykonania akcji|  
|11|Nie można zapisać w rejestrze.|Sprawdź, czy klucz wymienionych w komunikacie o błędzie jest możliwość dostępu do rejestru z konta, które WsatConfig.exe zostało wykonane w obszarze.|  
|12|Wystąpił nieoczekiwany błąd podczas próby uzyskania dostępu do magazynu certyfikatów.|Użyj kod błędu zwrócony do mapowania na błąd odpowiednie systemu.|  
|13|Konfiguracja pliku http.sys nie powiodło się. Nie można utworzyć nowego rezerwacji portu HTTPS dla usługi MSDTC.|Użyj kod błędu zwrócony do mapowania na błąd odpowiednie systemu.|  
|14|Konfiguracja pliku http.sys nie powiodło się. Nie można usunąć poprzedniej rezerwacji portu HTTPS dla usługi MSDTC.|Użyj kod błędu zwrócony do mapowania na błąd odpowiednie systemu.|  
|15|Konfiguracja pliku http.sys nie powiodło się. Poprzedniej rezerwacji portu HTTPS już istnieje dla określonego portu.|Inna aplikacja miała już prawa własności określonego portu. Zmień na inny port lub Odinstaluj lub ponownie skonfigurować bieżącej aplikacji.|  
|16|Konfiguracja pliku http.sys nie powiodło się. Nie można powiązać certyfikatu określonego portu.|Użyj kod błędu zwrócony komunikat o błędzie do mapowania na błąd odpowiednie systemu|  
|17|Konfiguracja pliku http.sys nie powiodło się. Nie można usunąć powiązania certyfikatu SSL z poprzedniego portu.|Użyj kod błędu zwrócony komunikat o błędzie do mapowania na błąd odpowiednie systemu. Jeśli to konieczne, umożliwia httpcfg.exe lub netsh.exe usunięcie rezerwacji portu błędne.|  
|18|Konfiguracja pliku http.sys nie powiodło się. Nie można powiązać określonego certyfikatu do portu, ponieważ poprzednie SSL powiązanie już istnieje.|Inna aplikacja miała już prawa własności określonego portu. Zmień na inny port lub Odinstaluj lub ponownie skonfigurować bieżącej aplikacji.|  
|19|Ponowne uruchamianie usługi MSDTC nie powiodło się.|Ręcznie uruchom ponownie usługi MSDTC, jeśli to konieczne. Jeśli problem będzie się powtarzać, skontaktuj się z firmy Microsoft.|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nie jest zainstalowany na zdalnym komputerze lub nie został poprawnie zainstalowany.|Zainstaluj [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na tym komputerze.|  
|21|Konfigurowanie zdalnego nie powiodło się z powodu przekroczenia limitu czasu operacji.|Wywołanie do skonfigurowania na maszynie zdalnej usługi WS-AT powinno trwać dłużej niż 90 sekund.|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nie jest zainstalowany na zdalnym komputerze lub nie został poprawnie zainstalowany.|Zainstaluj [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na tym komputerze.|  
|23|Konfiguracja zdalnego nie powiodła się z powodu wyjątku na komputerze zdalnym.|Sprawdź komunikat o błędzie dla elementów z możliwością wykonania akcji|  
|26|Do WsatConfig.exe przekazano nieprawidłowy argument.|Sprawdź wiersz polecenia dla błędów.|  
|27|`-accounts` Opcji wiersza polecenia jest nieprawidłowy.|Popraw`accounts` opcji wiersza polecenia, aby prawidłowo określić konto użytkownika.|  
|28|`-network` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-network` opcji wiersza polecenia, aby prawidłowo określić "Włącz" lub "Wyłącz".|  
|29|`-maxTimeout` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-maxTimeout` opcji wiersza polecenia wskazane.|  
|30|`-timeout` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-timeout` opcji wiersza polecenia wskazane.|  
|31|`-traceLevel` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-traceLevel` opcji wiersza polecenia, aby określić prawidłową wartość z następujących wartości,<br /><br /> — Wyłączone<br />— Błąd<br />-Krytyczne<br />— Ostrzeżenie<br />— Informacje<br />-Verbose<br />-Wszystkie|  
|32|`-traceActivity` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-traceActivity` opcji wiersza polecenia, określając opcję "Włącz" lub "Wyłącz".|  
|33|`-traceProp` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-traceProp` opcji wiersza polecenia, określając opcję "Włącz" lub "Wyłącz".|  
|34|`-tracePII` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-tracePII` opcji wiersza polecenia, określając opcję "Włącz" lub "Wyłącz".|  
|37|WsatConfig.exe nie mógł określić certyfikatu komputera dokładne. Taka sytuacja może wystąpić, jeśli istnieje więcej niż jednego kandydata lub nie istnieje.|Podaj odcisk palca lub parę Issuer\SubjectName poprawnie zidentyfikować dokładną certyfikatu do skonfigurowania.|  
|38|Proces lub użytkownik nie ma wystarczających uprawnień do zmiany konfiguracji zapory.|Wykonanie WsatConfig.exe przy użyciu konta użytkownika Administrator.|  
|39|WsatConfig.exe napotkał błąd podczas aktualizacji konfiguracji zapory.|Sprawdź komunikat o błędzie dla elementów z możliwością wykonania akcji.|  
|40|Nie ma możliwości daje dostęp do pliku klucza prywatnego certyfikatu usługi MSDTC odczytu WsatConfig.exe|Wykonanie WsatConfig.exe przy użyciu konta użytkownika Administrator.|  
|41|Albo nie instalacji [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] można odnaleźć lub wersji znaleziono niezgodny co narzędzie jest w stanie Konfigurowanie.|Upewnij się, [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] jest poprawnie zainstalowana i tylko Użyj narzędzia WsatConfig.exe dołączony do tej wersji [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] do konfigurowania usługi WS-AT.|  
|42|Argument została określona więcej niż raz w wierszu polecenia.|Tylko jeden raz określić każdy argument podczas wykonywania WsatConfig.exe.|  
|43|WsatConfig.exe nie można zaktualizować ustawień usługi WS-AT, jeśli nie włączono usługi WS-AT.|Określ `-network:enable` jako argument wiersza polecenia.|  
|44|Brakuje wymaganej poprawki i nie można skonfigurować usługi WS-AT, dopóki nie zostanie zainstalowana poprawka.|Zobacz [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] wersji, aby uzyskać instrukcje dotyczące instalowania wymaganej poprawki.|  
|45|`-virtualServer` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-virtualServer` opcji wiersza polecenia, określając nazwę sieciową zasobu klastra, w której chcesz skonfigurować.|  
|46|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW|Użyj kod błędu zwrócony do mapowania na błąd odpowiednie systemu.|  
|47|Proces lub użytkownik nie ma wystarczających uprawnień, aby włączyć sesję śledzenia funkcji ETW.|Wykonanie WsatConfig.exe przy użyciu konta użytkownika Administrator.|  
|48|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|49|Nie można utworzyć nowego pliku dziennika z powodu niewystarczającej ilości miejsca na % systemdrive %|Upewnij się, że z % systemdrive % ma wystarczającym miejscem dla pliku dziennika.|  
|51|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|52|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|53|Kopii zapasowej poprzedniego pliku dziennika sesji funkcji ETW nie powiodła się.|Upewnij się, że z % systemdrive % ma wystarczającym miejscem dla pliku dziennika i kopii zapasowej poprzedniego pliku dziennika (jeśli istnieje). Ręcznie usuń poprzedniego pliku dziennika w razie potrzeby.|  
|55|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|56|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
