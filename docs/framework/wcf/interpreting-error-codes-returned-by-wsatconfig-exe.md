---
title: Interpretowanie kodów błędów zwróconych przez program wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 47db39f2b350c2fa8c655a041ec0239e5d297644
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151635"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretowanie kodów błędów zwróconych przez program wsatConfig.exe
W tym temacie wymieniono wszystkie kody błędów wygenerowanych przez narzędzie konfiguracji WS-AtomicTransaction (wsatConfig.exe) i zalecane akcje do wykonania.  
  
## <a name="list-of-error-codes"></a>Listę kodów błędów  
  
|Kod błędu|Opis|Zalecana akcja do wykonania|  
|----------------|-----------------|------------------------------------|  
|0|Operacja zakończyła się pomyślnie|Brak|  
|1|Nieoczekiwany błąd|Kontakt z firmą Microsoft|  
|2|Wystąpił nieoczekiwany błąd podczas próby nawiązania kontaktu z MSDTC można pobrać jej ustawienia zabezpieczeń.|Upewnij się, że usługa MSDTC nie jest wyłączona i rozwiązać wszystkie problemy na liście zwrócony wyjątek.|  
|3|Konto, z którego uruchomiono WsatConfig.exe nie miał wystarczających uprawnień do odczytu ustawień zabezpieczeń sieci.|Wykonywanie WsatConfig.exe w ramach konta administratora.|  
|4|Włącz "Dostęp sieciowy DTC" MSDTC, przed podjęciem próby włączyć obsługę WS-AT.|Włącz "Dostęp sieciowy DTC" dla usługi MSDTC i ponownie uruchom narzędzie.|  
|5|Wprowadzony port jest poza zakresem. Wartość musi być z zakresu od 1 do 65535.|Popraw `-port:<portNum>`<br /><br /> Opcja wiersza polecenia, zgodnie z instrukcjami w komunikacie o błędzie.|  
|6|Certyfikat nieprawidłowy punkt końcowy został określony w wierszu polecenia.  Nie można odnaleźć certyfikatu lub nie przeszedł weryfikacji.|Popraw `-endpointCert` opcji wiersza polecenia. Upewnij się, że certyfikat ma klucz prywatny, jest przeznaczona do użytku z ServerAuthentication i rozszerzenie, jest zainstalowany w magazynie certyfikatów LocalMachine\MY i jest w pełni zaufany.|  
|7|Certyfikat nieprawidłowych kont została określona w wierszu polecenia.|Popraw `-accountsCerts` opcji wiersza polecenia. Określony certyfikat albo został niepoprawnie określony lub nie można go znaleźć.|  
|8|Domyślny limit czasu został określony poza zakresem od 1 do 3600 sekund.|Wprowadź wartość limitu czasu poprawną wartość domyślną, wskazane.|  
|10|Wystąpił nieoczekiwany błąd podczas próby uzyskania dostępu do rejestru.|Sprawdź komunikat o błędzie i kod błędu dla elementów z możliwością wykonywania akcji|  
|11|Nie można zapisać do rejestru.|Upewnij się, że klucz komunikat o błędzie na liście zdolność do obsługi dostępu do rejestru od konta którego WsatConfig.exe została wykonana w ścieżce.|  
|12|Wystąpił nieoczekiwany błąd podczas próby uzyskania dostępu do magazynu certyfikatów.|Użyj kod błędu zwrócony do mapowania na błąd systemowy odpowiednie.|  
|13|Nie można skonfigurować http.sys. Nie można utworzyć nowe zastrzeżenie port HTTPS dla usługi MSDTC.|Użyj kod błędu zwrócony do mapowania na błąd systemowy odpowiednie.|  
|14|Nie można skonfigurować http.sys. Nie można usunąć poprzedniej rezerwacji portu HTTPS do usługi MSDTC.|Użyj kod błędu zwrócony do mapowania na błąd systemowy odpowiednie.|  
|15|Nie można skonfigurować http.sys. Poprzednie rezerwacji portu HTTPS już istnieje dla określonego portu.|Inna aplikacja miała już własności określonego portu. Zmień na innym porcie lub odinstalować lub ponownie skonfigurować bieżącej aplikacji.|  
|16|Nie można skonfigurować http.sys. Nie można powiązać certyfikat z określonego portu.|Umożliwia mapowania na błąd systemowy odpowiedni kod błędu zwrócony komunikat o błędzie|  
|17|Nie można skonfigurować http.sys. Nie można usunąć powiązania certyfikatu SSL z poprzedniego portu.|Umożliwia mapowania na błąd systemowy odpowiedni kod błędu zwrócony komunikat o błędzie. Jeśli to konieczne, użyj httpcfg.exe lub netsh.exe, aby usunąć rezerwacje błędne portu.|  
|18|Nie można skonfigurować http.sys. Nie można powiązać określony certyfikat z portem, ponieważ poprzednie SSL powiązanie już istnieje.|Inna aplikacja miała już własności określonego portu. Zmień na innym porcie lub odinstalować lub ponownie skonfigurować bieżącej aplikacji.|  
|19|Ponowne uruchamianie usługi MSDTC nie powiodło się.|Ręcznie uruchom ponownie usługi MSDTC, jeśli to konieczne. Jeśli problem będzie się powtarzać, skontaktuj się z pomocą firmy Microsoft.|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nie jest zainstalowany na zdalnym komputerze lub nie został poprawnie zainstalowany.|Zainstaluj [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na maszynie.|  
|21|Konfiguracja zdalnego nie powiodło się z powodu limitu czasu operacji.|Wywołania do skonfigurowania WS-AT na maszynie zdalnej powinna trwać dłużej niż 90 sekund.|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nie jest zainstalowany na zdalnym komputerze lub nie został poprawnie zainstalowany.|Zainstaluj [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na maszynie.|  
|23|Konfiguracja zdalnego nie powiodło się z powodu wyjątku na komputerze zdalnym.|Sprawdź komunikat o błędzie dla elementów z możliwością wykonywania akcji|  
|26|Do WsatConfig.exe przekazano nieprawidłowy argument.|Sprawdź wiersz polecenia dla błędów.|  
|27|`-accounts` Opcji wiersza polecenia jest nieprawidłowy.|Popraw`accounts` opcji wiersza polecenia, aby prawidłowo określić konto użytkownika.|  
|28|`-network` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-network` opcji wiersza polecenia, prawidłowo określać "Włącz" lub "Wyłącz".|  
|29|`-maxTimeout` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-maxTimeout` opcji wiersza polecenia, jak wskazano.|  
|30|`-timeout` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-timeout` opcji wiersza polecenia, jak wskazano.|  
|31|`-traceLevel` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-traceLevel` opcję wiersza polecenia, aby określić prawidłową wartość z następujących wartości,<br /><br /> — Wyłączone<br />— Błąd<br />-Krytyczne<br />-Ostrzeżenie<br />-Informacje<br />-Verbose<br />— Wszystkie|  
|32|`-traceActivity` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-traceActivity` opcji wiersza polecenia, określając wartość "Włącz" lub "Wyłącz".|  
|33|`-traceProp` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-traceProp` opcji wiersza polecenia, określając wartość "Włącz" lub "Wyłącz".|  
|34|`-tracePII` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-tracePII` opcji wiersza polecenia, określając wartość "Włącz" lub "Wyłącz".|  
|37|WsatConfig.exe nie był w stanie określić certyfikat komputera dokładne. Może się to zdarzyć, gdy istnieje więcej niż jeden Release candidate lub jeśli żadna nie istnieje.|Określ odcisk palca certyfikatu lub parę Issuer\SubjectName poprawnie zidentyfikować dokładny certyfikatu umożliwiającego skonfigurowanie.|  
|38|Proces lub użytkownik nie ma wystarczających uprawnień do zmiany konfiguracji zapory.|Wykonywanie WsatConfig.exe w ramach konta administratora.|  
|39|WsatConfig.exe napotkał błąd podczas aktualizowania konfiguracji zapory.|Sprawdź komunikat o błędzie dla elementów z możliwością wykonywania akcji.|  
|40|WsatConfig.exe nie będzie mógł udzielić dostępu do odczytu usługi MSDTC do pliku klucza prywatnego certyfikatu|Wykonywanie WsatConfig.exe w ramach konta administratora.|  
|41|Albo nie instalacji [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] można odnaleźć lub znaleziono wersji nie jest zgodny, co to narzędzie jest w stanie konfiguracji.|Upewnij się, [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] jest poprawnie zainstalowane i tylko narzędzie WsatConfig.exe, dołączonej do wersji [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] skonfigurować WS-AT.|  
|42|Argument została określona więcej niż raz w wierszu polecenia.|Tylko raz określić każdy argument podczas wykonywania WsatConfig.exe.|  
|43|WsatConfig.exe nie można zaktualizować ustawień WS-AT, jeśli nie włączono WS-AT.|Określ `-network:enable` jako argument wiersza polecenia.|  
|44|Brakuje wymaganej poprawki i nie można skonfigurować WS-AT, dopóki nie zostanie zainstalowana poprawka.|Zobacz [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] wersji, aby uzyskać instrukcje dotyczące instalowania wymaganej poprawki.|  
|45|`-virtualServer` Opcji wiersza polecenia jest nieprawidłowy.|Popraw `-virtualServer` opcji wiersza polecenia, określając nazwę sieciową zasobu klastra, w której chcesz skonfigurować.|  
|46|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesji śledzenia zdarzeń systemu Windows|Użyj kod błędu zwrócony do mapowania na błąd systemowy odpowiednie.|  
|47|Proces lub użytkownik nie ma wystarczających uprawnień, aby włączyć sesji śledzenia zdarzeń systemu Windows.|Wykonywanie WsatConfig.exe w ramach konta administratora.|  
|48|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|49|Nie można utworzyć nowy plik dziennika z powodu niewystarczającej ilości miejsca na % systemdrive %|Upewnij się, że % systemdrive % ma wystarczającej ilości miejsca dla pliku dziennika.|  
|51|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|52|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|53|Kopia zapasowa poprzedniej pliku dziennika sesji funkcji ETW nie powiodło się.|Upewnij się, czy Twoje dysk % systemdrive % ma wystarczającej ilości miejsca dla pliku dziennika i kopia zapasowa poprzedniej pliku dziennika (jeśli istnieje). Usuń poprzedni plik dziennika ręcznie, jeśli to konieczne.|  
|55|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
|56|Wystąpił nieoczekiwany błąd podczas próby uruchomienia sesję śledzenia funkcji ETW.|Kontakt z firmą Microsoft.|  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzie do konfiguracji elementu WS-AtomicTransaction (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
