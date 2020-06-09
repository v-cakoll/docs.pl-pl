---
title: Zabezpieczenia transportu HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 28d0ac164022f585f25b44b16c68994b592ef041
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592726"
---
# <a name="http-transport-security"></a>Zabezpieczenia transportu HTTP
W przypadku korzystania z protokołu HTTP jako transportu zabezpieczenia są zapewniane przez implementację SSL (SSL). Protokół SSL jest szeroko używany przez Internet do uwierzytelniania usługi dla klienta, a następnie do zapewnienia poufności (szyfrowania) kanału. W tym temacie opisano sposób działania protokołu SSL i sposobu ich implementacji w programie Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Podstawowy protokół SSL  
 Sposób działania protokołu SSL najlepiej wyjaśniono w typowym scenariuszu, w tym przypadku w witrynie sieci Web banku. Lokacja pozwala klientowi na logowanie się przy użyciu nazwy użytkownika i hasła. Po uwierzytelnieniu użytkownik może wykonywać transakcje, takie jak Wyświetlanie sald kont, płatność rachunków i przenoszenie pieniędzy z jednego konta do innego.  
  
 Gdy użytkownik najpierw odwiedza lokację, mechanizm protokołu SSL rozpoczyna serię negocjacji o nazwie *uzgadnianie*z klientem użytkownika (w tym przypadku Internet Explorer). Protokół SSL najpierw uwierzytelnia lokację banku dla klienta. Jest to istotny krok, ponieważ klienci muszą najpierw znać, że komunikują się z rzeczywistą lokacją, a nie z fałszerstwem próbującym połączyć je w celu wpisania nazwy użytkownika i hasła. Protokół SSL jest uwierzytelniany przy użyciu certyfikatu SSL dostarczonego przez zaufany urząd, na przykład VeriSign. Logika przebiega następująco: Firma VeriSign gwarantuje tożsamość witryny bankowej. Ponieważ program Internet Explorer ufa VeriSign, lokacja jest zaufana. Jeśli chcesz się skontaktować z firmą VeriSign, możesz to zrobić również, klikając logo VeriSign. Przedstawia on informacje o autentyczności i dacie wygaśnięcia oraz o tym, kto jest wystawiony (w witrynie banku).  
  
 Aby zainicjować bezpieczną sesję, klient wysyła odpowiednik "Hello" do serwera wraz z listą algorytmów kryptograficznych, za pomocą których można podpisać, generować skróty oraz szyfrować i odszyfrowywać przy użyciu. W odpowiedzi witryna wysyła potwierdzenie i wybór jednego z pakietów algorytmów. Podczas tego wstępnego uzgadniania obie strony wysyłają i odbierają identyfikatorów jednorazowych. Identyfikator *jednorazowy* to losowo wygenerowany element danych, który jest używany w połączeniu z kluczem publicznym lokacji, aby utworzyć skrót. *Skrót* to nowa liczba, która pochodzi od dwóch liczb przy użyciu standardowego algorytmu, takiego jak SHA1. (Klient i lokacja również wymieniają komunikaty, aby wyrazić zgodę na użycie algorytmu wyznaczania wartości skrótu). Skrót jest unikatowy i służy tylko do sesji między klientem a lokacją w celu szyfrowania i odszyfrowywania wiadomości. Zarówno klient, jak i usługa mają oryginalny identyfikator jednorazowy i klucz publiczny certyfikatu, więc obie strony mogą generować ten sam skrót. W związku z tym klient sprawdza poprawność skrótu wysyłanego przez usługę przez (a) przy użyciu uzgodnionego algorytmu, aby obliczyć wartość skrótu z danych, i (b) porównać ją z skrótem wysyłanym przez usługę. Jeśli dwa dopasowania, klient ma gwarancję, że skrót nie został naruszony. Klient może następnie użyć tego skrótu jako klucza do szyfrowania wiadomości, która zawiera jeszcze inny nowy skrót. Usługa może odszyfrować komunikat przy użyciu skrótu i odzyskać ten drugi do ostatniego skrótu. Informacje zebrane (identyfikatorów jednorazowych, klucz publiczny i inne dane) są teraz znane obu stronom i można utworzyć końcowy skrót (lub klucz główny). Ten końcowy klucz jest przesyłany w postaci zaszyfrowanej przy użyciu skrótu następnym do ostatniego. Klucz główny jest następnie używany do szyfrowania i odszyfrowywania wiadomości dla pozostałej części sesji. Ponieważ zarówno klient, jak i usługa używają tego samego klucza, jest to również nazywane *kluczem sesji*.  
  
 Klucz sesji jest również scharakteryzowany jako klucz symetryczny lub "wspólny klucz tajny". Klucz symetryczny jest ważny, ponieważ zmniejsza obliczenia wymagane przez obie strony transakcji. Jeśli każdy komunikat wymaga nowej wymiany identyfikatorów jednorazowych i skrótów, wydajność może się pogorszyć. W związku z tym ostatecznym celem protokołu SSL jest użycie klucza symetrycznego, który pozwala na swobodne przepływanie komunikatów między obiema stronami.  
  
 Poprzedni opis to uproszczona wersja, co się dzieje, ponieważ protokół może się różnić od lokacji do lokacji. Istnieje również możliwość, że zarówno klient, jak i witryna generują identyfikatorów jednorazowych, które są algorithmically połączone podczas uzgadniania, aby zwiększyć złożoność, a tym samym ochronę, do procesu wymiany danych.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certyfikaty i infrastruktura kluczy publicznych  
 Podczas uzgadniania usługa wysyła również do klienta certyfikat SSL. Certyfikat zawiera informacje, takie jak data wygaśnięcia, Urząd wystawiania i Uniform Resource Identifier witryny (URI). Klient porównuje identyfikator URI z identyfikatorem URI, który pierwotnie skontaktował się w celu zapewnienia dopasowania, a także sprawdza datę i urząd wystawiający.  
  
 Każdy certyfikat ma dwa klucze, klucz prywatny i klucz publiczny, a dwa są znane jako *para kluczy wymiany*. W skrócie klucz prywatny jest znany tylko właścicielowi certyfikatu, podczas gdy klucz publiczny jest odczytywany z certyfikatu. Każdy klucz może służyć do szyfrowania lub odszyfrowywania skrótu, skrótu lub innego klucza, ale tylko jako operacje sprzeczne. Na przykład jeśli klient jest szyfrowany przy użyciu klucza publicznego, tylko lokacja może odszyfrować komunikat przy użyciu klucza prywatnego. Podobnie, Jeśli lokacja jest zaszyfrowana przy użyciu klucza prywatnego, klient może odszyfrować przy użyciu klucza publicznego. Zapewnia to klientowi gwarancję, że komunikaty są wymieniane tylko z posiadaczem klucza prywatnego, ponieważ tylko wiadomości zaszyfrowane za pomocą klucza prywatnego można odszyfrować przy użyciu klucza publicznego. Lokacja jest zapewniana przez wymianę komunikatów z klientem, który został zaszyfrowany przy użyciu klucza publicznego. Ta wymiana jest zabezpieczona tylko w przypadku wstępnego uzgadniania, ale co jest znacznie więcej, aby utworzyć rzeczywisty klucz symetryczny. Niemniej jednak cała komunikacja zależy od usługi, która ma prawidłowy certyfikat SSL.  
  
## <a name="implementing-ssl-with-wcf"></a>Implementowanie protokołu SSL za pomocą programu WCF  
 Zabezpieczenia transportu HTTP (lub SSL) są udostępniane zewnętrznie do programu WCF. Protokół SSL można zaimplementować w jeden z dwóch sposobów: czynnik decydujący to sposób, w jaki aplikacja jest hostowana:  
  
- Jeśli używasz programu Internet Information Services (IIS) jako hosta WCF, użyj infrastruktury usług IIS do skonfigurowania usługi SSL.  
  
- W przypadku tworzenia własnej aplikacji WCF można powiązać certyfikat SSL z adresem za pomocą narzędzia HttpCfg. exe.  
  
### <a name="using-iis-for-transport-security"></a>Korzystanie z usług IIS do zabezpieczenia transportu  
  
#### <a name="iis-70"></a>IIS 7.0  
 Aby skonfigurować usługi IIS 7,0 jako bezpieczny Host (przy użyciu protokołu SSL), zobacz [konfigurowanie SSL w usługach IIS 7,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10)).  
  
Aby skonfigurować certyfikaty do użycia z usługami IIS 7,0, zobacz [Konfigurowanie certyfikatów serwera w usługach iis 7,0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="iis-60"></a>IIS 6,0  
 Aby skonfigurować usługi IIS 6,0 jako bezpieczny Host (przy użyciu protokołu SSL), zobacz [konfigurowanie SSL](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736992(v=ws.10)).  
  
 Aby skonfigurować certyfikaty do użycia z usługami IIS 6,0, zobacz [Certificates_IIS_SP1_Ops](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757474(v=ws.10)).  
  
### <a name="using-httpcfg-for-ssl"></a>Korzystanie z HttpCfg dla protokołu SSL  

 W przypadku tworzenia własnej aplikacji WCF należy użyć narzędzia [HttpCfg. exe](/windows/win32/http/httpcfg-exe) .
  
 Aby uzyskać więcej informacji o używaniu narzędzia HttpCfg. exe do konfigurowania portu za pomocą certyfikatu X. 509, zobacz [How to: Configure a port with SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia transportu](transport-security.md)
- [Zabezpieczenia komunikatów](message-security-in-wcf.md)
