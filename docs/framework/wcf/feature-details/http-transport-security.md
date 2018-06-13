---
title: Zabezpieczenia transportu HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: cc284f82f974d9b34ff1cf6732d2ee7b95528c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495925"
---
# <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP
Korzystając z protokołu HTTP jako transportu, zabezpieczenia przez implementację protokołu Secure Sockets Layer (SSL). Protokół SSL jest powszechnie używany w Internecie do uwierzytelniania usługi na kliencie, a następnie zapewnienie poufności (szyfrowanie) do kanału. W tym temacie wyjaśniono, jak działa protokół SSL i jak jest zaimplementowana w systemie Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Podstawowy protokołu SSL  
 Jak działa protokół SSL jest najlepsze objaśnione przez typowy scenariusz, w takim przypadku banku witryny sieci Web. Lokacji umożliwia klientowi zalogować się przy użyciu nazwy użytkownika i hasła. Po uwierzytelniony, użytkownik może wykonywać transakcje, takie jak widok środki na koncie, zwrócić rachunków i przenieść pieniędzy z jednego konta.  
  
 Gdy użytkownik odwiedza najpierw lokacji, mechanizmu SSL rozpoczyna się szereg negocjacji o nazwie *uzgadniania*, z klientem przez użytkownika (w tym przypadku program Internet Explorer). Protokół SSL po raz pierwszy uwierzytelnia lokacji bank do klienta. Jest to kluczowy etap, ponieważ klienci najpierw musi wiedzieć, czy komunikują się z lokacji, a nie fałszywe, który próbuje nakłonić do wpisanie nazwy użytkownika i hasła. Protokół SSL jest uwierzytelnianie przy użyciu certyfikatu SSL dostarczonego przez zaufany urząd, takich jak VeriSign. Logika przechodzi następująco: VeriSign poręcza tożsamość lokacji bank. Ponieważ program Internet Explorer ufa VeriSign, witryna jest zaufany. Jeśli chcesz sprawdzić z VeriSign, należy więc również, klikając logo firmy VeriSign. Przedstawiający instrukcji autentyczności z jej daty wygaśnięcia i który jest wystawiony dla (lokacja banku).  
  
 Aby zainicjować bezpiecznej sesji, klient wysyła odpowiednikiem "hello" do serwera oraz algorytmów kryptograficznych, można go użyć do podpisania, generowanie skrótów i szyfrowania i odszyfrowywania z listy. W odpowiedzi lokacji odsyła potwierdzenia i wybór jednego z mechanizmów algorytmów. Podczas tego początkowego uzgadniania obie strony wysyłania i odbierania identyfikatorów jednorazowych. A *identyfikator jednorazowy* jest losowo wygenerowany element danych, który jest używany w połączeniu z użyciem klucza publicznego dla lokacji, aby utworzyć skrót. A *skrótu* jest nowy numer pochodzącej z dwóch liczb przy użyciu algorytmu standardowe, takie jak SHA1. (Klient i lokacji również wymieniają komunikaty, aby zaakceptować który algorytm wyznaczania wartości skrótu do użycia.) Wartość skrótu jest unikatowa i jest używany tylko w przypadku sesji między klientem a lokacją, do szyfrowania i odszyfrowywania wiadomości. Zarówno klient, jak i usługa ma oryginalny identyfikator jednorazowy i klucz publiczny certyfikatu, aby obie strony może wygenerować tego samego wyznaczania wartości skrótu. W związku z tym klient sprawdza poprawność skrótu wysłanych przez usługę () Obliczanie przy użyciu uzgodnionych na algorytmu wyznaczania wartości skrótu z danych i (b) należy go porównać do wyznaczania wartości skrótu, wysłanych przez usługę; Jeśli dwa są zgodne, klient ma gwarancji, że nie została naruszona skrót. Klient może następnie używać ten skrót jako klucz szyfrowania wiadomości zawierający kolejnego nowego skrótu. Usługę można odszyfrować wiadomości za pomocą skrótu i odzyskać ten skrót second-final. Skumulowany informacji (identyfikatorów jednorazowych, klucz publiczny i innych danych) jest teraz znane obie strony, a można utworzyć skrótu końcowego (lub klucz główny). Ten klucz końcowego są wysyłane zaszyfrowane przy użyciu skrótu dalej do ostatniego. Klucz główny jest następnie używany do szyfrowania i odszyfrowywania wiadomości do resetowania sesji. Ponieważ zarówno klient, jak i usługi używają tego samego klucza, to jest również nazywany *klucza sesji*.  
  
 Klucz sesji jest również określana jako klucza symetrycznego lub "wspólny klucz tajny." Po klucz symetryczny jest ważne, ponieważ zmniejsza obliczenia wymagane przez obie strony transakcji. Każdej wiadomości na żądanie nowego wymiany identyfikatorów jednorazowych i skróty czy pogorszenia wydajności. W związku z tym kiedy ostatecznym celem jest protokół SSL jest użyć klucza symetrycznego, który pozwala dowolnie przepływ między partnerami większy poziom zabezpieczeń i wydajności.  
  
 Opis poprzedniego jest uproszczone co się stanie, ponieważ protokół może się różnić od witryny. Istnieje również możliwość, że zarówno klient, jak i witryny obie generowanie identyfikatorów jednorazowych, które tworzą algorithmically podczas uzgadniania, aby dodać więcej złożoność i w związku z tym ochrony, do procesu wymiany danych.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certyfikaty i infrastruktury kluczy publicznych  
 Podczas uzgadniania usługa wysyła swój certyfikat SSL do klienta. Certyfikat zawiera informacje, takie jak jego data wygaśnięcia wystawiania Urząd i danych lokacji identyfikator URI (Uniform Resource). Klient porównuje identyfikator URI do identyfikatora URI pierwotnie skontaktowała się do zapewnienia zgodności i sprawdza również daty i urząd wystawiający.  
  
 Każdy certyfikat ma dwa klucze, klucza prywatnego i klucz publiczny i dwa są określane jako *exchange pary kluczy*. Krótko mówiąc klucza prywatnego jest znany tylko do właściciela certyfikatu klucza publicznego jest do odczytu z certyfikatu. Albo klucz może służyć do szyfrowania lub odszyfrowywania digest, wyznaczania wartości skrótu, lub innego klucza, ale tylko jako sprzeczne operacje. Na przykład jeśli klienta są szyfrowane przy użyciu klucza publicznego, tylko witryna może odszyfrować wiadomości przy użyciu klucza prywatnego. Podobnie jeśli w lokacji są szyfrowane przy użyciu klucza prywatnego, klient może odszyfrować przy użyciu klucza publicznego. To gwarantuje klientowi czy komunikaty wymianie tylko z Właściciel klucza prywatnego ponieważ mogły być odszyfrowane tylko komunikatów szyfrowanych za pomocą klucza prywatnego z kluczem publicznym. Witryny jest pewność, że jest wymiana komunikatów z klienta, który został zaszyfrowany za pomocą klucza publicznego. Tego programu exchange jest zabezpieczone tylko w przypadku początkowego uzgadniania, czyli Dlaczego wiele innych odbywa się do tworzenia rzeczywistych klucza symetrycznego. Niemniej jednak cała komunikacja są zależne od usługi o certyfikat SSL.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementacja protokołu SSL z programem WCF  
 Zabezpieczenia transportu HTTP (lub SSL) zapewnia zewnętrznie WCF. Protokół SSL można zaimplementować w jeden z dwóch sposobów; decydującym czynnikiem jest jak aplikacja jest hostowana:  
  
-   Jeśli korzystasz z usług Internet Information Services (IIS) jako hosta usługi WCF, umożliwia konfigurowanie usługi SSL infrastruktury usługi IIS.  
  
-   Jeśli tworzysz aplikację hostowania samoobsługowego WCF można powiązać certyfikatu SSL z adresu przy użyciu narzędzia HttpCfg.exe.  
  
### <a name="using-iis-for-transport-security"></a>Za pomocą usług IIS zabezpieczeń transportu  
  
#### <a name="iis-70"></a>IIS 7.0  
 Aby skonfigurować [!INCLUDE[iisver](../../../../includes/iisver-md.md)] jako bezpieczne hosta (przy użyciu protokołu SSL), zobacz [usług IIS 7.0 Beta: Konfigurowanie Secure Sockets Layer w usługach IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88600).  
  
 Aby skonfigurować certyfikaty do użycia z [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [usług IIS 7.0 Beta: Konfigurowanie certyfikatów serwerów w usługach IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
#### <a name="iis-60"></a>IIS 6,0  
 Aby skonfigurować [!INCLUDE[iis601](../../../../includes/iis601-md.md)] jako bezpieczne hosta (przy użyciu protokołu SSL), zobacz [Konfigurowanie Secure Sockets Layer](http://go.microsoft.com/fwlink/?LinkId=88601).  
  
 Aby skonfigurować certyfikaty do użycia z [!INCLUDE[iis601](../../../../includes/iis601-md.md)], zobacz [Certificates_IIS_SP1_Ops](http://go.microsoft.com/fwlink/?LinkId=88602).  
  
### <a name="using-httpcfg-for-ssl"></a>Za pomocą tak dla protokołu SSL  
 Jeśli tworzysz aplikację hostowania samoobsługowego WCF, Pobierz narzędzia HttpCfg.exe dostępne pod adresem [lokacji narzędzia obsługi systemu Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=29002).  
  
 Aby uzyskać więcej informacji o konfigurowaniu portów za pomocą certyfikatu X.509 przy użyciu narzędzia HttpCfg.exe, zobacz [porady: Konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
