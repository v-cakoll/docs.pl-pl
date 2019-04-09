---
title: Konfigurowanie protokołów HTTP i HTTPS
ms.date: 03/30/2017
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 3decf955748b156b8eff4b5286a70e67d8ac14ad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195153"
---
# <a name="configuring-http-and-https"></a>Konfigurowanie protokołów HTTP i HTTPS
Usługi WCF i klienci mogą komunikować się za pośrednictwem protokołów HTTP i HTTPS. Ustawienia HTTP/HTTPS są skonfigurowane przy użyciu usług Internet Information Services (IIS) lub za pomocą narzędzia wiersza polecenia. Gdy usługa WCF jest hostowana w ustawieniach usług IIS HTTP lub HTTPS można skonfigurować w ramach usług IIS (za pomocą narzędzia inetmgr.exe). Jeśli usługa WCF jest samodzielnie hostowana, ustawienia protokołu HTTP lub HTTPS są konfigurowane za pomocą narzędzia wiersza polecenia.  
  
 Co najmniej należy skonfigurować rejestracji adresu URL, a następnie dodać wyjątek zapory dla adresu URL, będzie korzystać z usługi.  
  
 Narzędzie używane do konfigurowania ustawień protokołu HTTP, zależy od systemu operacyjnego na komputerze jest uruchomiony.  
  
 Podczas uruchamiania [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] automatycznie zainstaluje to narzędzie. Podczas uruchamiania [!INCLUDE[wxp](../../../../includes/wxp-md.md)], możesz pobrać narzędzia z [narzędzia obsługi systemu Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Aby uzyskać więcej informacji, zobacz [Przegląd tak](https://go.microsoft.com/fwlink/?LinkId=88605).  
  
 Podczas uruchamiania [!INCLUDE[wv](../../../../includes/wv-md.md)] lub Windows 7, możesz skonfigurować te ustawienia przy użyciu narzędzia Netsh.exe.  
  
## <a name="configuring-namespace-reservations"></a>Konfigurowanie Namespace rezerwacji  
 Namespace rezerwacji przypisuje uprawnienia dla części nazw adresem URL protokołu HTTP do określonej grupy użytkowników. Rezerwacja zapewnia tych użytkowników, prawa do tworzenia usług, które nasłuchują na część przestrzeni nazw. Rezerwacje są przedrostki adresów URL, co oznacza, że rezerwacji obejmuje wszystkich ścieżek podrzędnych ścieżki rezerwacji. Rezerwacje Namespace zezwalać na dwa sposoby użycia symboli wieloznacznych. W tym artykule opisano w dokumentacji interfejsu API serwera HTTP [kolejność rozpoznawanie między oświadczeń przestrzeni nazw, które obejmują symboli wieloznacznych](https://go.microsoft.com/fwlink/?LinkId=94841).  
  
 Uruchomionej aplikacji można utworzyć żądania podobne do dodawania rejestracji przestrzeni nazw. Rejestracje i zastrzeżenia konkurują o części przestrzeni nazw. Rezerwacja mogą mieć pierwszeństwo nad rejestracji zgodnie z porządkiem rozwiązania podany w [kolejność rozpoznawanie między oświadczeń przestrzeni nazw, które obejmują symboli wieloznacznych](https://go.microsoft.com/fwlink/?LinkId=94841). W tym przypadku rezerwacji blokuje uruchomionej aplikacji odbieranie żądań.  
  
### <a name="running-windows-xp-or-server-2003"></a>Uruchamianie Windows XP lub Server 2003  
 Użyj `httpcfg.exe set urlacl` polecenie, aby zmienić rezerwacji przestrzeni nazw. [Dokumentację Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia Httpcfg.exe. Modyfikowanie uprawnienia rezerwacji dla części obszaru nazw wymaga uprawnień administracyjnych lub własności część przestrzeni nazw. Początkowo cały przestrzeni nazw protokołu HTTP należy do administratora lokalnego.  
  
 Oto składnia polecenia tak, za pomocą `set urlacl` opcji  
  
```console  
httpcfg set urlacl /u {http://URL:Port/ | https://URL:Port/} /a ACL  
```  
  
 `/u` Parametr jest wymagany w przypadku korzystania z `set urlacl`. Potrzebny jest ciąg zawierający w pełni kwalifikowany adres URL, który służy jako klucz rekordu dla rezerwacji wykonywane.  
  
 `/a` Parametr jest wymagany również w przypadku korzystania z `set urlacl`. Potrzebny jest ciąg zawierający kontroli listy dostępu (ACL) w postaci ciągu definicji języka SDDL (Security Descriptor).  
  
 Poniżej przedstawiono przykład użycia tego polecenia.  
  
```console  
httpcfg.exe set urlacl /u http://myhost:8000/ /a "O:AOG:DAD:(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-0-0)"  
```  
  
### <a name="running-windows-vista-windows-server-2008-r2-or-windows-7"></a>Systemem Windows Vista, Windows Server 2008 R2 lub Windows 7  
 Jeśli są uruchomione na [!INCLUDE[wv](../../../../includes/wv-md.md)], Windows Server 2008 R2 lub Windows 7, należy użyć narzędzia Netsh.exe. Poniżej przedstawiono przykład użycia tego polecenia.  
  
```console  
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user  
```  
  
 To polecenie dodaje rezerwację adresu URL dla określonego obszaru nazw adresu URL konta domena\użytkownik.  Aby uzyskać więcej informacji na temat korzystania z polecenia netsh, wpisz "netsh http add urlacl" w wierszu polecenia i naciśnij klawisz wprowadzić.  
  
## <a name="configuring-a-firewall-exception"></a>Konfigurowanie wyjątków zapory  
 Hostując samodzielnie usługi WCF, która komunikuje się za pośrednictwem protokołu HTTP, należy dodać wyjątek do konfiguracji zapory, aby zezwolić na połączenia przychodzące przy użyciu określonego adresu URL. Aby uzyskać więcej informacji, zobacz [otwieranie portu w Zaporze Windows (Windows 7)](https://go.microsoft.com/fwlink/?LinkId=239961)  
  
## <a name="configuring-ssl-certificates"></a>Konfigurowanie certyfikatów protokołu SSL  
 Protokół Secure Sockets Layer (SSL) używa certyfikatów na kliencie i serwerze w celu przechowywania kluczy szyfrowania. Serwer udostępnia swój certyfikat protokołu SSL, po nawiązaniu połączenia, dzięki czemu klient może sprawdzić tożsamość serwera. Serwer można także zażądać certyfikatu od klienta w celu zapewnienia wzajemnego uwierzytelniania obu stronach połączenia.  
  
 Certyfikaty są przechowywane w magazynie scentralizowane zgodnie z liczbą adres i port IP połączenia. Specjalny adres IP 0.0.0.0 pasuje do dowolnego adresu IP dla komputera lokalnego. Należy pamiętać, że magazyn certyfikatów nie rozróżnia adresy URL na podstawie ścieżki. Usługi za pomocą tej samej kombinacji adres i port IP muszą mieć certyfikaty, nawet, jeśli ścieżka w adresie URL dla usług różni się.  
  
 Aby uzyskać instrukcje krok po kroku, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="configuring-the-ip-listen-list"></a>Konfigurowanie listy nasłuchiwania adresów IP  
 Interfejs API serwera HTTP tylko wiąże adres IP i port po użytkownik rejestruje adresu URL. Domyślnie interfejsu API serwera HTTP wiąże się z portem w adresie URL, dla wszystkich adresów IP maszyny. Wystąpi konflikt, jeśli aplikacja, która nie korzysta z interfejsu API serwera HTTP został wcześniej powiązany z tej kombinacji adres IP i port. Lista nasłuchiwania IP pozwala usług WCF pod kątem współistnienia z aplikacji, które używają portu dla niektórych adresów IP maszyny. Jeśli lista nasłuchiwania IP zawiera wszystkie wpisy, interfejsu API serwera HTTP wiąże tylko te adresy IP, które określa listy. Modyfikowanie listy IP nasłuchiwania wymaga uprawnień administracyjnych.  
  
### <a name="running-windows-xp-or-server-2003"></a>Uruchamianie Windows XP lub Server 2003  
 Aby zmodyfikować listę nasłuchiwania adresów IP, należy użyć narzędzia tak, jak pokazano w poniższym przykładzie. [Dokumentację Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia httpcfg.exe.  
  
```console  
httpcfg.exe set iplisten -i 0.0.0.0:8000  
```  
  
### <a name="running-windows-vista-or-windows-7"></a>Systemem Windows Vista lub Windows 7  
 Aby zmodyfikować listę nasłuchiwania adresów IP, należy użyć narzędzia netsh, jak pokazano w poniższym przykładzie.  
  
```console  
netsh http add iplisten ipaddress=0.0.0.0:8000  
```  
  
## <a name="other-configuration-settings"></a>Pozostałe ustawienia konfiguracyjne  
 Korzystając z <xref:System.ServiceModel.WSDualHttpBinding>, wartości domyślne, które są zgodne z rezerwacji przestrzeni nazw i zapory Windows korzysta z połączenia klienta. Jeśli użytkownik chce dostosować adres bazowy podwójnego połączenia klienta, również musisz skonfigurować te ustawienia protokołu HTTP na kliencie, aby dopasować nowy adres.  
  
 Interfejsu API serwera HTTP zawiera niektóre zaawansowane ustawienia konfiguracji, które nie są dostępne za pośrednictwem tak. Te ustawienia są przechowywane w rejestrze i dotyczą wszystkich aplikacji działających w systemach, które używają interfejsów API serwera HTTP. Aby uzyskać informacje o tych ustawieniach, zobacz [ustawienia rejestru Http.sys w usługach IIS](https://go.microsoft.com/fwlink/?LinkId=94843). Większość użytkowników nie powinna trzeba zmienić te ustawienia.  
  
## <a name="issues-specific-to-windows-xp"></a>Problemy specyficzne dla Windows XP  
 Usługi IIS nie obsługuje udostępniania portów na [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Jeśli usługi IIS zostały uruchomione i usługi WCF podejmują próbę użycia przestrzeni nazw za pomocą tego samego portu, usługi WCF nie powiedzie się. Usługi IIS i WCF jest domyślnie przy użyciu portu 80. Zmień przypisania portów dla usług lub użyj adresu IP nasłuchiwania listy, aby przypisać usługi WCF do karty sieciowej nie jest używany przez usługi IIS. Usług IIS 6.0 lub nowszym mają został przeprojektowany w celu użycia interfejsów API serwera HTTP.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
