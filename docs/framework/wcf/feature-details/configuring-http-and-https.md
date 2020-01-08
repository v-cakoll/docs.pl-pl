---
title: Konfigurowanie protokołów HTTP i HTTPS
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: f7fd2bad6ced09b638cc1bb5d539fab1b9ce7d25
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75336702"
---
# <a name="configuring-http-and-https"></a>Konfigurowanie protokołów HTTP i HTTPS

Usługi i klienci WCF mogą komunikować się za pośrednictwem protokołów HTTP i HTTPS. Ustawienia protokołu HTTP/HTTPS są konfigurowane przy użyciu Internet Information Services (IIS) lub przy użyciu narzędzia wiersza polecenia. Gdy usługa WCF jest hostowana w obszarze Ustawienia HTTP lub HTTPS usługi IIS, można skonfigurować w ramach usług IIS (za pomocą narzędzia inetmgr. exe). Jeśli usługa WCF jest samodzielna, ustawienia protokołu HTTP lub HTTPS są konfigurowane przy użyciu narzędzia wiersza polecenia.

Aby skonfigurować rejestrację adresów URL i dodać wyjątek zapory dla adresu URL, który będzie używany przez usługę, należy określić co najmniej. Te ustawienia można skonfigurować za pomocą narzędzia Netsh. exe.

## <a name="configuring-namespace-reservations"></a>Konfigurowanie rezerwacji przestrzeni nazw

Rezerwacja przestrzeni nazw przypisuje prawa dla części przestrzeni nazw HTTP URL do określonej grupy użytkowników. Rezerwacja daje tym użytkownikom prawo do tworzenia usług, które nasłuchują na tej części przestrzeni nazw. Rezerwacje są prefiksami adresów URL, co oznacza, że rezerwacja obejmuje wszystkie ścieżki podrzędne ścieżki rezerwacji. Rezerwacje przestrzeni nazw zezwalają na dwa sposoby używania symboli wieloznacznych. Dokumentacja interfejsu API serwera HTTP opisuje [kolejność rozpoznawania oświadczeń między przestrzeniami nazw, które obejmują symbole wieloznaczne](/windows/desktop/Http/routing-incoming-requests).

Działająca aplikacja może utworzyć podobne żądanie, aby dodać rejestracje przestrzeni nazw. Rejestracje i rezerwacje konkurują w przypadku części przestrzeni nazw. Rezerwacja może mieć pierwszeństwo przed rejestracją zgodnie z kolejnością rozwiązywania [między oświadczeniami przestrzeni nazw, które obejmują symbole wieloznaczne](/windows/desktop/Http/routing-incoming-requests). W takim przypadku rezerwacja blokuje uruchomioną aplikację z otrzymywania żądań.

Poniższy przykład używa narzędzia Netsh. exe:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

To polecenie dodaje rezerwację adresu URL dla określonego obszaru nazw URL dla konta domena\nazwa użytkownika. Aby uzyskać więcej informacji na temat korzystania z polecenia netsh, wpisz `netsh http add urlacl /?` w wierszu polecenia i naciśnij klawisz ENTER.

## <a name="configuring-a-firewall-exception"></a>Konfigurowanie wyjątku zapory

Podczas samodzielnego udostępniania usługi WCF, która komunikuje się za pośrednictwem protokołu HTTP, należy dodać do konfiguracji zapory wyjątek, aby zezwolić na połączenia przychodzące przy użyciu określonego adresu URL.

## <a name="configuring-ssl-certificates"></a>Konfigurowanie certyfikatów SSL

Protokół SSL (SSL) używa certyfikatów na kliencie i serwerze do przechowywania kluczy szyfrowania. Serwer udostępnia swój certyfikat SSL podczas ustanawiania połączenia, aby klient mógł zweryfikować tożsamość serwera. Serwer może również zażądać certyfikatu od klienta, aby zapewnić wzajemne uwierzytelnienie obu stron połączenia.

Certyfikaty są przechowywane w scentralizowanym magazynie zgodnie z adresem IP i numerem portu połączenia. Specjalny adres IP 0.0.0.0 jest zgodny z dowolnym adresem IP komputera lokalnego. Należy pamiętać, że magazyn certyfikatów nie rozróżnia adresów URL na podstawie ścieżki. Usługi o tej samej kombinacji adresów IP i portów muszą udostępniać certyfikaty nawet wtedy, gdy ścieżka w adresie URL usług jest inna.

Instrukcje krok po kroku znajdują się w temacie [How to: Configure a port with a SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>Konfigurowanie listy nasłuchiwania adresów IP

Interfejs API serwera HTTP wiąże się tylko z adresem IP i portem, gdy użytkownik zarejestruje adres URL. Domyślnie interfejs API serwera HTTP wiąże się z portem w adresie URL dla wszystkich adresów IP maszyny. Występuje konflikt, jeśli aplikacja, która nie korzysta z interfejsu API serwera HTTP, została wcześniej powiązana z tą kombinacją adresu IP i portu. Lista nasłuchiwania adresów IP pozwala usługom WCF współistnieć z aplikacjami, które używają portu dla niektórych adresów IP maszyny. Jeśli lista nasłuchu IP zawiera jakieś wpisy, interfejs API serwera HTTP tworzy powiązanie tylko z tymi adresami IP, które określa lista. Modyfikowanie listy nasłuchiwania adresów IP wymaga uprawnień administracyjnych.

Użyj narzędzia Netsh, aby zmodyfikować listę nasłuchiwania adresów IP, jak pokazano w następującym przykładzie:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Inne ustawienia konfiguracji

W przypadku korzystania z <xref:System.ServiceModel.WSDualHttpBinding>połączenie klienta wykorzystuje wartości domyślne, które są zgodne z rezerwacjami przestrzeni nazw i Zaporą systemu Windows. W przypadku wybrania opcji dostosowania adresu podstawowego klienta podwójnego połączenia należy również skonfigurować te ustawienia protokołu HTTP na kliencie, aby odpowiadały nowemu adresowi.

Interfejs API serwera HTTP zawiera niektóre zaawansowane ustawienia konfiguracji, które nie są dostępne za pośrednictwem usługi HttpCfg. Te ustawienia są przechowywane w rejestrze i stosowane do wszystkich aplikacji działających w systemach, które używają interfejsów API serwera HTTP. Aby uzyskać informacje na temat tych ustawień, zobacz [Ustawienia rejestru http. sys dla usług IIS](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows). Większość użytkowników nie musi zmieniać tych ustawień.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Instrukcje: konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
