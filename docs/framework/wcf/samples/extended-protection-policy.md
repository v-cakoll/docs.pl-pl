---
title: Zasady ochrony rozszerzonej
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 645b48b3c7ce3daaaedac372ba5ba6fd5edfc8f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990174"
---
# <a name="extended-protection-policy"></a>Zasady ochrony rozszerzonej
Rozszerzona ochrona jest inicjatywy zabezpieczeń, ochrony przed atakami typu man-in--middle (MITM). Ataki MITM to zagrożenie bezpieczeństwa, w którym MITM przyjmuje poświadczeń klienta i przekazuje je do serwera.  
  
## <a name="demonstrates"></a>Demonstracje  
 Ochrona rozszerzona  
  
## <a name="discussion"></a>Dyskusja  
 Aplikacje uwierzytelniania przy użyciu protokołu Kerberos, szyfrowane lub NTLM przy użyciu protokołu HTTPS, ustanawiania kanału zabezpieczeń TLS (Transport Level), a następnie uwierzytelnianie odbywa się przy użyciu bezpiecznego kanału. Jednakże nie istnieje żadne powiązanie między kluczem sesji, wygenerowane za pomocą protokołu SSL i klucza sesji generowane podczas uwierzytelniania. Wszelkie MITM mogą nawiązać się między klientem a serwerem i Rozpocznij przekazywanie żądania od klienta, nawet wtedy, gdy sam kanał transportu jest bezpieczne, ponieważ serwer nie ma żadnej możliwość określenia, czy została ustanowiona bezpieczny kanał między klientem lub MITM. Rozwiązania, w tym scenariuszu ma powiązania zewnętrzne kanał TLS z kanałem wewnętrznego uwierzytelniania w taki sposób, że serwer może wykryć, czy MITM.  
  
> [!NOTE]
>  W tym przykładzie tylko działa w przypadku hostowania w usługach IIS i nie może działać na Cassini — serwera wdrożeniowego Visual Studio, ponieważ Cassini nie obsługuje protokołu HTTPS.  
  
> [!NOTE]
>  Ta funkcja tylko jest obecnie dostępna w systemie Windows 7. Poniższe kroki są specyficzne dla Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Zainstalować Internetowe usługi informacyjne z **Panel sterowania**, **dodawania/usuwania programów**, **funkcji Windows**.  
  
2. Zainstaluj **uwierzytelniania Windows** w **funkcji Windows**, **Internetowe usługi informacyjne**, **usługi World Wide Web**,  **Zabezpieczenia**, i **uwierzytelniania Windows**.  
  
3. Zainstaluj **Windows Communication Foundation HTTP aktywacji** w **funkcji Windows**, **Microsoft .NET Framework 3.5.1**, i **komunikacji Windows Aktywacja Foundation HTTP**.  
  
4. Ten przykładowy skrypt wymaga klienta do nawiązania bezpiecznego kanału z serwerem, dzięki czemu wymaga obecności certyfikatu serwera, które mogą być instalowane z Menedżera usług Internet Information Services (IIS).  
  
    1. Otwórz Menedżera usług IIS. Otwórz **certyfikaty serwera**, który pojawia się w **widok funkcji** karcie po wybraniu węzła głównego (nazwa komputera).  
  
    2. Na potrzeby testowania w tym przykładzie, należy utworzyć certyfikat z podpisem własnym. Jeśli chcesz, aby program Internet Explorer będzie wyświetlany monit o certyfikat nie jest bezpieczne, należy zainstalować certyfikat w magazynie zaufanego certyfikatu głównego urzędu.  
  
5. Otwórz **akcje** okienko dla domyślnej witryny sieci Web. Kliknij przycisk **edytowanie witryny**, **powiązania**. Dodawanie protokół HTTPS jako typu Jeśli nie są jeszcze zainstalowane, numer portu 443. Przypisz certyfikat SSL utworzony w poprzednim kroku.  
  
6. Tworzenie usługi. Tworzy katalog wirtualny w usługach IIS i kopiuje pliki .dll i .svc .config zgodnie z wymaganiami dla usługa jest hostowana w sieci Web.  
  
7. Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy katalog wirtualny (**ExtendedProtection**), która została utworzona w poprzednim kroku. Wybierz **Konwertuj na aplikację**.  
  
8. Otwórz **uwierzytelniania** modułu w Menedżerze usług IIS dla tego katalogu wirtualnego i Włącz **uwierzytelniania Windows**.  
  
9. Otwórz **Zaawansowane ustawienia** w obszarze **uwierzytelniania Windows** dla tego katalogu wirtualnego i ustaw ją na **wymagane**.  
  
10. Można testować usługę, uzyskując dostęp do adresu URL HTTPS w oknie przeglądarki (podaj w pełni kwalifikowaną nazwą domeny). Jeśli chcesz, aby przejść do tego adresu URL z komputera zdalnego, upewnij się, że Zapora jest otwarta dla wszystkich połączeń przychodzących HTTP i HTTPS.  
  
11. Otwórz plik konfiguracji klienta i podaj w pełni kwalifikowanej nazwy domeny dla atrybutu adresów klienta lub punkt końcowy, który zastępuje `<<full_machine_name>>`.  
  
12. Uruchom klienta. Klient komunikuje się z usługi, która ustanawia bezpiecznego kanału i używa ochrony rozszerzonej.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
