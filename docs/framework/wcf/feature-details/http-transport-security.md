---
title: Zabezpieczenia transportu HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 26d72bf234e66ccbf60305d7681f181077589ed0
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55739517"
---
# <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP
Podczas korzystania z protokołu HTTP jako transportu zabezpieczeń jest dostarczana przez implementację protokołu Secure Sockets Layer (SSL). Protokół SSL jest powszechnie używanych w Internecie uwierzytelniania usługi do klienta, a następnie, aby zapewnić poufność (szyfrowanie) do kanału. W tym temacie wyjaśniono, jak działa protokół SSL oraz jego implementacji w Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Podstawowe protokołu SSL  
 Jak działa protokół SSL jest najlepsze wyjaśnione przez typowy scenariusz, w tym przypadku banku witryny sieci Web. Witryna pozwala klientowi logują się przy użyciu nazwy użytkownika i hasła. Po uwierzytelniony, użytkownik może wykonywać transakcje, takie jak widok salda konta, opłacić rachunki i przenieść pieniądze z jednego konta do innego.  
  
 Gdy użytkownik najpierw odwiedza witryny, mechanizm SSL rozpoczyna się szereg negocjacji o nazwie *uzgadnianie*, za pomocą klienta użytkownika (w tym przypadku program Internet Explorer). SSL umożliwiają uwierzytelnienie najpierw bank lokacji klienta. Jest to kluczowy etap, ponieważ klienci najpierw trzeba znać komunikują się przy użyciu rzeczywistej lokacji i nie fałszywe, który próbuje nakłonić do wpisując ich nazwy użytkownika i hasła. Protokół SSL jest to uwierzytelnianie za pomocą certyfikatu SSL dostarczone przez zaufany urząd, takich jak VeriSign. Logika wykracza następująco: VeriSign poręcza tożsamość lokacji bank. Ponieważ program Internet Explorer ufa VeriSign, witryna jest zaufany. Aby skontaktować się z VeriSign, należy więc również, klikając VeriSign logo. Instrukcja autentyczności przedstawiające daty wygaśnięcia i który jest wystawiony dla (lokacja bankowe).  
  
 Aby zainicjować bezpiecznej sesji, klient wysyła wielokrotność "hello" na serwerze z listą algorytmów kryptograficznych, można go użyć do podpisania, generowania skrótów i szyfrowania i odszyfrowywania za pomocą. W odpowiedzi witryny wysyła z powrotem po potwierdzeniu i wybór jednego z zestawów algorytmów. Podczas tej początkowej uzgadniania obie strony wysyłania i odbierania poprawni. A *jednorazowego* to generowany losowo danych, który jest używany w połączeniu z klucza publicznego lokacji, aby utworzyć skrót. A *skrótu* jest nowy numer, który jest tworzony na podstawie dwóch liczb, przy użyciu standardowego algorytmu, takie jak SHA1. (Klient i lokacji również wymiany wiadomości zgody na algorytm wyznaczania wartości skrótu.) Wartość skrótu jest unikatowa i jest używana tylko dla sesji między klientem a lokacją, do szyfrowania i odszyfrowywania wiadomości. Zarówno klient, jak i usługi mają oryginalnego identyfikatora jednorazowego i klucz publiczny certyfikatu, dlatego obie strony może wygenerować ten sam skrót. W związku z tym klient sprawdza poprawność wyznaczania wartości skrótu, wysłanych przez usługę, () przy użyciu uzgodnionych na algorytm obliczania skrótu z danych i (b) porównanie do wyznaczania wartości skrótu, wysłanych przez usługę; Jeśli dwa dopasowania, klient ma gwarancji, że skrót nie zostały naruszone. Klient może następnie używać ten skrót jako klucz szyfrowania wiadomości, która zawiera kolejny nowy skrót. Usługi można odszyfrować wiadomości przy użyciu skrótu i odzyskać ten skrót second-final. Zebranych informacji (identyfikatorów jednorazowych, klucz publiczny i innych danych) jest teraz znane obie strony, a można utworzyć skrótu końcowego (lub klucz główny). Ten klucz końcowego jest szyfrowany i przesyłany przy użyciu skrótu dalej do ostatniego. Klucz główny jest następnie używany do szyfrowania i odszyfrowywania wiadomości w pozostałej części sesji. Ponieważ zarówno klient, jak i usługi używają tego samego klucza, jest to również nazywane *klucza sesji*.  
  
 Klucz sesji jest również określana jako klucza symetrycznego lub "wspólny klucz tajny." Klucz symetryczny jest ważne, ponieważ zwalnia obliczeń wymagana przez obie strony transakcji. Każdej wiadomości na żądanie nowego wymiany poprawni i skróty może pogarszać wydajność. W związku z tym ostatecznym celem jest protokół SSL jest używać kluczem symetrycznym, który pozwala łatwo przepływ między partnerami z większego stopnia bezpieczeństwa i wydajności.  
  
 Opis poprzedniego jest uproszczoną wersję, co się stanie, ponieważ protokół mogą się różnić od witryny. Istnieje również możliwość, że zarówno klient, jak i witryny zarówno generowanie identyfikatorów jednorazowych, które są łączone za algorithmically podczas uzgadniania, aby dodać więcej złożoność i w związku z tym ochrony, do procesu wymiany danych.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certyfikaty i infrastruktury kluczy publicznych  
 Podczas uzgadniania usługa wysyła swój certyfikat SSL do klienta. Certyfikat zawiera informacje, takie jak daty wygaśnięcia wydawania urzędu i jej identyfikator (URI). Klient porównuje identyfikatora URI do identyfikatora URI pierwotnie skontaktowała się zapewnienie dopasowania i sprawdza również, datę i urząd wystawiający.  
  
 Każdy certyfikat ma dwa klucze, klucza prywatnego i kluczem publicznym i dwa są znane jako *wymiany pary kluczy*. Krótko mówiąc klucz prywatny jest znane tylko właścicielowi certyfikat, natomiast klucz publiczny jest do odczytu z certyfikatu. Żadnego z nich może służyć do szyfrowania lub odszyfrowywania podsumowanie, skrót, lub inny klawisz, ale tylko jako sprzeczne operacje. Na przykład w klienta są szyfrowane przy użyciu klucza publicznego, tylko witryna może odszyfrować wiadomości przy użyciu klucza prywatnego. Podobnie jeśli w lokacji są szyfrowane przy użyciu klucza prywatnego, klient może odszyfrować przy użyciu klucza publicznego. To zapewnia klientowi, komunikaty wymianie tylko w przypadku inicjator kluczem prywatnym ponieważ tylko wiadomości zaszyfrowane przy użyciu klucza prywatnego można odszyfrować przy użyciu klucza publicznego. Witryna ma pewność, że jest to wymiana komunikatów z klientem, który zawiera zaszyfrowane przy użyciu klucza publicznego. Ten program exchange jest bezpieczne tylko w przypadku początkowego uzgadniania, co jest dlaczego do tworzenia rzeczywistych klucz symetryczny odbywa się m.in. Niemniej jednak cała komunikacja zależą od usługę, której ważnego certyfikatu SSL.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementowanie protokołu SSL z usługą WCF  
 Zabezpieczenia transportu HTTP (lub SSL) jest udostępniony zewnętrznie do programu WCF. Można zaimplementować protokół SSL w jeden z dwóch sposobów; decydującym czynnikiem jest to, jak aplikacja jest hostowana:  
  
-   Korzystania z usług Internet Information Services (IIS) jako host usługi WCF umożliwia konfigurowanie protokołu SSL usługi infrastruktury usługi IIS.  
  
-   W przypadku tworzenia własnego aplikacji WCF adresu za pomocą narzędzia HttpCfg.exe można powiązać certyfikatu SSL.  
  
### <a name="using-iis-for-transport-security"></a>Korzystanie z usług IIS dla zabezpieczeń transportu  
  
#### <a name="iis-70"></a>IIS 7.0  
 Aby skonfigurować [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jako bezpiecznego hosta (przy użyciu protokołu SSL), zobacz [IIS 7.0 Beta: Konfigurowanie protokołu Secure Sockets Layer w usługach IIS 7.0](https://go.microsoft.com/fwlink/?LinkId=88600).  
  
 Konfigurowanie certyfikatów do użytku z programem [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [IIS 7.0 Beta: Konfigurowanie certyfikatów serwera w usługach IIS 7.0](https://go.microsoft.com/fwlink/?LinkID=88595).  
  
#### <a name="iis-60"></a>IIS 6,0  
 Aby skonfigurować [!INCLUDE[iis601](../../../../includes/iis601-md.md)] jako bezpiecznego hosta (przy użyciu protokołu SSL), zobacz [Konfigurowanie Secure Sockets Layer](https://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Konfigurowanie certyfikatów do użytku z programem [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [Certificates_IIS_SP1_Ops](https://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>Za pomocą tak dla protokołu SSL  
 W przypadku tworzenia własnego aplikacji WCF, Pobierz narzędzia HttpCfg.exe dostępne pod adresem [narzędzia obsługi systemu Windows XP Service Pack 2 lokacji](https://go.microsoft.com/fwlink/?LinkId=29002).  
  
 Aby uzyskać więcej informacji o konfigurowaniu portów za pomocą certyfikatu X.509 przy użyciu narzędzia HttpCfg.exe, zobacz [jak: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
