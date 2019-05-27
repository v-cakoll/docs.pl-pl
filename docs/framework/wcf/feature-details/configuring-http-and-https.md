---
title: Konfigurowanie protokołów HTTP i HTTPS - WCF
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 4bfdbbc19bb9ed72bc50ebeeac114241ccd47c25
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053413"
---
# <a name="configuring-http-and-https"></a>Konfigurowanie protokołów HTTP i HTTPS

Usługi WCF i klienci mogą komunikować się za pośrednictwem protokołów HTTP i HTTPS. Ustawienia HTTP/HTTPS są skonfigurowane przy użyciu usług Internet Information Services (IIS) lub za pomocą narzędzia wiersza polecenia. Gdy usługa WCF jest hostowana w ustawieniach usług IIS HTTP lub HTTPS można skonfigurować w ramach usług IIS (za pomocą narzędzia inetmgr.exe). Jeśli usługa WCF jest samodzielnie hostowana, ustawienia protokołu HTTP lub HTTPS są konfigurowane za pomocą narzędzia wiersza polecenia.

Co najmniej, dla których chcesz skonfigurować rejestracji adresu URL i dodać wyjątek zapory dla adresu URL, będzie korzystać z usługi. Te ustawienia można skonfigurować za pomocą narzędzia Netsh.exe.

## <a name="configuring-namespace-reservations"></a>Konfigurowanie rezerwacji przestrzeni nazw

Namespace rezerwacji przypisuje uprawnienia dla części nazw adresem URL protokołu HTTP do określonej grupy użytkowników. Rezerwacja zapewnia tych użytkowników, prawa do tworzenia usług, które nasłuchują na część przestrzeni nazw. Rezerwacje są przedrostki adresów URL, co oznacza, że rezerwacji obejmuje wszystkie podrzędne ścieżki rezerwacji. Rezerwacje Namespace zezwalać na dwa sposoby użycia symboli wieloznacznych. W tym artykule opisano w dokumentacji interfejsu API serwera HTTP [kolejność rozpoznawanie między oświadczeń przestrzeni nazw, które obejmują symboli wieloznacznych](/windows/desktop/Http/routing-incoming-requests).

Uruchomionej aplikacji można utworzyć żądania podobne do dodawania rejestracji przestrzeni nazw. Rejestracje i zastrzeżenia konkurują o części przestrzeni nazw. Rezerwacja mogą mieć pierwszeństwo nad rejestracji zgodnie z porządkiem rozwiązania podany w [kolejność rozpoznawanie między oświadczeń przestrzeni nazw, które obejmują symboli wieloznacznych](/windows/desktop/Http/routing-incoming-requests). W tym przypadku rezerwacji blokuje uruchomionej aplikacji odbieranie żądań.

W poniższym przykładzie użyto narzędzia Netsh.exe:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

To polecenie dodaje rezerwację adresu URL, dla określonego obszaru nazw adresu URL konta domena\użytkownik. Aby uzyskać więcej informacji na temat korzystania z polecenia netsh, wpisz `netsh http add urlacl /?` w wierszu polecenia i naciśnij klawisz Enter.

## <a name="configuring-a-firewall-exception"></a>Konfigurowanie wyjątków zapory

Hostując samodzielnie usługi WCF, która komunikuje się za pośrednictwem protokołu HTTP, należy dodać wyjątek do konfiguracji zapory, aby zezwolić na połączenia przychodzące przy użyciu określonego adresu URL.

## <a name="configuring-ssl-certificates"></a>Konfigurowanie certyfikatów protokołu SSL

Protokół Secure Sockets Layer (SSL) używa certyfikatów na kliencie i serwerze w celu przechowywania kluczy szyfrowania. Serwer udostępnia swój certyfikat protokołu SSL, po nawiązaniu połączenia, dzięki czemu klient może sprawdzić tożsamość serwera. Serwer można także zażądać certyfikatu od klienta w celu zapewnienia wzajemnego uwierzytelniania obu stronach połączenia.

Certyfikaty są przechowywane w magazynie scentralizowane zgodnie z liczbą adres i port IP połączenia. Specjalny adres IP 0.0.0.0 pasuje do dowolnego adresu IP dla komputera lokalnego. Należy pamiętać, że magazyn certyfikatów nie odróżnić adresy URL na podstawie ścieżki. Usługi za pomocą tej samej kombinacji adres i port IP muszą mieć certyfikaty, nawet, jeśli ścieżka w adresie URL dla usług różni się.

Aby uzyskać instrukcje krok po kroku, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>Konfigurowanie listy nasłuchiwania adresów IP

Interfejs API serwera HTTP tylko wiąże adres IP i port po użytkownik rejestruje adresu URL. Domyślnie interfejsu API serwera HTTP wiąże się z portem w adresie URL, dla wszystkich adresów IP maszyny. Wystąpi konflikt, jeśli aplikacja, która nie korzysta z interfejsu API serwera HTTP został wcześniej powiązany z tej kombinacji adres IP i port. Lista nasłuchiwania IP pozwala usług WCF pod kątem współistnienia z aplikacji, które używają portu dla niektórych adresów IP maszyny. Jeśli lista nasłuchiwania IP zawiera wszystkie wpisy, interfejsu API serwera HTTP wiąże tylko te adresy IP, które określa listy. Modyfikowanie listy IP nasłuchiwania wymaga uprawnień administracyjnych.

Aby zmodyfikować listę nasłuchiwania adresów IP, należy użyć narzędzia netsh, jak pokazano w poniższym przykładzie:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Pozostałe ustawienia konfiguracyjne

Korzystając z <xref:System.ServiceModel.WSDualHttpBinding>, wartości domyślne, które są zgodne z rezerwacji przestrzeni nazw i zapory Windows korzysta z połączenia klienta. Jeśli użytkownik chce dostosować adres bazowy podwójnego połączenia klienta, również musisz skonfigurować te ustawienia protokołu HTTP na kliencie, aby dopasować nowy adres.

Interfejs API serwera HTTP zawiera niektóre zaawansowane ustawienia konfiguracji, które nie są dostępne za pośrednictwem tak. Te ustawienia są przechowywane w rejestrze i dotyczą wszystkich aplikacji działających w systemach, które używają interfejsów API serwera HTTP. Aby uzyskać informacje o tych ustawieniach, zobacz [ustawienia rejestru Http.sys w usługach IIS](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows). Większość użytkowników nie muszą zmieniać te ustawienia.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Instrukcje: Konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
