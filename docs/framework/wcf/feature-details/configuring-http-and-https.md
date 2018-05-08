---
title: Konfigurowanie protokołów HTTP i HTTPS
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 70c947724abf8da68ec8f7e6d858e26fec62dce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-http-and-https"></a>Konfigurowanie protokołów HTTP i HTTPS
Usługi WCF i klienci mogą komunikować się za pośrednictwem protokołu HTTP i HTTPS. Ustawienia HTTP i HTTPS są skonfigurowane przy użyciu usługi Internet Information Services (IIS) lub za pomocą narzędzia wiersza polecenia. Gdy usługa WCF jest hostowana w ustawieniach usług IIS HTTP lub HTTPS można skonfigurować w ramach usług IIS (przy użyciu narzędzia inetmgr.exe). Jeśli usługa WCF jest samodzielnie hostowana, ustawienia protokołu HTTP lub HTTPS są konfigurowane za pomocą narzędzia wiersza polecenia.  
  
 Co najmniej można skonfigurować rejestracji adresu URL, a następnie dodać wyjątek zapory dla usługi będą używać adresu URL.  
  
 Narzędzie używane do konfigurowania ustawień protokołu HTTP, zależy od systemu operacyjnego na komputerze jest zainstalowany.  
  
 Podczas uruchamiania [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] automatycznie zainstaluje to narzędzie. Podczas uruchamiania [!INCLUDE[wxp](../../../../includes/wxp-md.md)], możesz pobrać narzędzia z [narzędzia obsługi systemu Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=88606). Aby uzyskać więcej informacji, zobacz [omówienie tak](http://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Podczas uruchamiania [!INCLUDE[wv](../../../../includes/wv-md.md)]lub Windows 7, te ustawienia można skonfigurować za pomocą narzędzia Netsh.exe.  
  
## <a name="configuring-namespace-reservations"></a>Konfigurowanie Namespace zastrzeżenia  
 Zastrzeżenia Namespace przypisuje uprawnienia dla części nazw adresu URL HTTP do określonej grupy użytkowników. Zastrzeżenie daje tych użytkowników prawo do tworzenia usług, które nasłuchują na część przestrzeni nazw. Zastrzeżenia są prefiksy URL, co oznacza, że zastrzeżenia obejmuje wszystkie ścieżki podrzędne ścieżki rezerwacji. Zastrzeżenia Namespace zezwolenie na dwa sposoby używania symboli wieloznacznych. W tym artykule opisano w dokumentacji interfejsu API serwera HTTP [kolejność rozpoznawania między oświadczenia przestrzeni nazw, które obejmują symboli wieloznacznych](http://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Uruchomionej aplikacji można utworzyć żądanie podobne do dodawania nazw rejestracji. Rejestracje i zastrzeżenia konkurować dla części przestrzeni nazw. Zastrzeżenie może mają pierwszeństwo przed rejestracji w kolejności rozwiązania podany w [kolejność rozpoznawania między oświadczenia przestrzeni nazw, które obejmują symboli wieloznacznych](http://go.microsoft.com/fwlink/?LinkId=94841). W takim przypadku rezerwacji blokuje działającej aplikacji z żądania odbierania.  
  
### <a name="running-windows-xp-or-server-2003"></a>Uruchomiony system Windows XP lub Server 2003  
 Użyj `httpcfg.exe set urlacl` polecenie, aby zmienić rezerwacji przestrzeni nazw. [Dokumentacji narzędzia obsługi systemu Windows](http://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia Httpcfg.exe. Modyfikowanie prawa rezerwacji dla części obszaru nazw wymaga uprawnień administracyjnych lub własność część przestrzeni nazw. Początkowo całej przestrzeni nazw protokołu HTTP należy do administratora lokalnego.  
  
 Oto składnia polecenia tak z `set urlacl` opcji  
  
```  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /aACL  
```  
  
 `/u` Parametr jest wymagany w przypadku korzystania z `set urlacl`. Trwa ciąg, który zawiera w pełni kwalifikowany adres URL, który służy jako klucz rekordu dla rezerwacji została wprowadzona.  
  
 `/a` Parametr jest wymagany również przy użyciu `set urlacl`. Trwa ciąg, który zawiera listy kontroli dostępu (ACL) w formie ciągu definicji języka SDDL (Security Descriptor).  
  
 Poniżej przedstawiono przykład użycia tego polecenia.  
  
```  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Systemem Windows Vista, Windows Server 2008 R2 lub Windows 7  
 Jeśli są uruchomione na [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Server 2008 R2 lub Windows 7, użyj narzędzia Netsh.exe. Poniżej przedstawiono przykład użycia tego polecenia.  
  
```  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 To polecenie dodaje rezerwację adresu URL dla określonego obszaru nazw adresu URL dla konta domena\użytkownik.  Aby uzyskać więcej informacji na temat używania tego polecenia netsh, wpisz "netsh http add urlacl" w wierszu polecenia i naciśnij klawisz wprowadź.  
  
## <a name="configuring-a-firewall-exception"></a>Konfigurowanie wyjątków zapory  
 Podczas hostingu samodzielnego usługi WCF, która komunikuje się za pośrednictwem protokołu HTTP, należy dodać wyjątek do konfiguracji zapory, aby zezwolić na połączenia przychodzące przy użyciu określonego adresu URL. Aby uzyskać więcej informacji, zobacz [otwarcie portu w Zaporze systemu Windows (Windows 7)](http://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>Konfigurowanie certyfikatów SSL  
 Protokół Secure Sockets Layer (SSL) używa certyfikatów na kliencie i serwerze do przechowywania kluczy szyfrowania. Serwer zawiera swojego certyfikatu SSL, po nawiązaniu połączenia, dzięki czemu klient może sprawdzić tożsamości serwera. Serwer można również zażądać certyfikatu od klienta w celu zapewnienia wzajemnego uwierzytelniania obu stronach połączenia.  
  
 Certyfikaty są przechowywane w magazynie scentralizowane zgodnie z liczbą adres i port IP połączenia. Specjalne adres IP 0.0.0.0 filtruje dowolnego adresu IP dla komputera lokalnego. Należy pamiętać, że magazynu certyfikatów nie rozróżnia adresy URL na podstawie ścieżki. Usługi o tej samej kombinacja adresu IP oraz portu muszą współdzielić certyfikaty, nawet jeśli różni się ścieżki w adresie URL dla usług.  
  
 Aby uzyskać instrukcje, zobacz [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>Konfigurowanie na liście nasłuchiwania adresów IP  
 Interfejsu API serwera HTTP jest powiązany z adresu IP i portu tylko gdy użytkownik rejestruje adresu URL. Domyślnie interfejsu API serwera HTTP wiąże się z portem w adresie URL, dla wszystkich adresów IP maszyny. Wystąpi konflikt, jeśli aplikacja, która nie używa interfejsu API serwera HTTP ma wcześniej powiązany z tym kombinację adresu IP i portu. Na liście nasłuchiwania adresów IP umożliwia usług WCF pod kątem współistnieć z aplikacji, które używają portu dla niektórych adresów IP maszyny. Jeśli na liście nasłuchiwania adresów IP zawiera wszystkie pozycje, interfejsu API serwera HTTP wiąże tylko tych adresów IP, które określają listy. Modyfikowanie na liście nasłuchiwania adresów IP wymaga uprawnień administracyjnych.  
  
### <a name="running-windows-xp-or-server-2003"></a>Uruchomiony system Windows XP lub Server 2003  
 Użyj narzędzia tak, aby na liście adresów IP nasłuchiwania, jak pokazano w poniższym przykładzie. [Dokumentacji narzędzia obsługi systemu Windows](http://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia httpcfg.exe.  
  
```  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Systemem Windows Vista lub Windows 7  
 Aby zmodyfikować na liście adresów IP nasłuchiwania, należy użyć narzędzia netsh, jak pokazano w poniższym przykładzie.  
  
```  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Inne ustawienia konfiguracji  
 Korzystając z <xref:System.ServiceModel.WSDualHttpBinding>, połączenie klienta używa ustawień domyślnych, które są zgodne z rezerwacji przestrzeni nazw i zapory systemu Windows. Jeśli zdecydujesz się na adres podstawowy klienta połączenia dwa Dostosuj, następnie również skonfiguruj te ustawienia HTTP na kliencie, aby dopasować nowego adresu.  
  
 Interfejs API serwera HTTP ma niektóre ustawienia konfiguracji zaawansowanej, które nie są dostępne za pośrednictwem tak. Te ustawienia są przechowywane w rejestrze i dotyczą wszystkich aplikacji działających w systemach, które używają interfejsów API serwera HTTP. Aby uzyskać informacje o tych ustawieniach, zobacz [ustawień rejestru Http.sys w usługach IIS](http://go.microsoft.com/fwlink/?LinkId=94843). Aby zmienić te ustawienia nie konieczne większości użytkowników.  
  
## <a name="issues-specific-to-windows-xp"></a>Problemy specyficzne dla systemu Windows XP  
 Usługi IIS nie obsługuje udostępniania portów na [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Jeśli uruchomiony jest program IIS i usługi WCF próbuje użyć przestrzeni nazw z tego samego portu, usługi WCF nie powiedzie się. Usługi IIS i WCF jest domyślnie używa portu 80. Zmiana przypisania portów dla usług albo użyj na liście nasłuchiwania adresów IP można przypisać do karty sieciowej nie jest używany przez usługi IIS usługi WCF. Usługi IIS 6.0 lub nowszym przeprojektowano użycia interfejsów API serwera HTTP.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
