---
title: Zasady ochrony rozszerzonej
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 0e6c2bdac3880b12a1b447fe3caf07c4a81a8d80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961483"
---
# <a name="extended-protection-policy"></a>Zasady ochrony rozszerzonej
Ochrona rozszerzona to inicjatywa zabezpieczeń chroniąca przed atakami typu man-in-the-Middle (MITM). Atak MITM polega na zagrożeniu bezpieczeństwa, w którym MITM Pobiera poświadczenia klienta i przekazuje je do serwera.  
  
## <a name="demonstrates"></a>Demonstracje  
 Ochrona rozszerzona  
  
## <a name="discussion"></a>Dyskusji  
 Gdy aplikacje są uwierzytelniane przy użyciu protokołu Kerberos, szyfrowanego lub NTLM przy użyciu protokołu HTTPS, najpierw zostaje ustanowiony kanał zabezpieczenia na poziomie transportu (TLS), a następnie uwierzytelnianie odbywa się przy użyciu bezpiecznego kanału. Nie ma jednak powiązania między kluczem sesji wygenerowanym przez protokół SSL i kluczem sesji wygenerowanym podczas uwierzytelniania. Każdy MITM może nawiązać się z klientem i serwerem, a następnie rozpocząć przekazywanie żądań od klienta, nawet jeśli sam kanał transportu jest bezpieczny, ponieważ serwer nie ma możliwości poznania, czy bezpieczny kanał został ustanowiony przez klienta lub MITM. Rozwiązaniem w tym scenariuszu jest powiązanie zewnętrznego kanału TLS z wewnętrznym kanałem uwierzytelniania w taki sposób, aby serwer mógł wykryć, czy istnieje MITM.  
  
> [!NOTE]
> Ten przykład działa tylko wtedy, gdy jest hostowany w usługach IIS i nie może działać na Cassini — Visual Studio Development Server, ponieważ Cassini nie obsługuje protokołu HTTPS.  
  
> [!NOTE]
> Ta funkcja jest obecnie dostępna tylko w systemie Windows 7. Poniższe kroki dotyczą systemu Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Zainstaluj Internet Information Services z **Panelu sterowania**, **Dodaj/Usuń programy**, **funkcje systemu Windows**.  
  
2. Zainstaluj **uwierzytelnianie systemu Windows** w **funkcjach systemu Windows**, **Internet Information Services**, **World Wide Web usług**, **zabezpieczeń**i **uwierzytelniania systemu Windows**.  
  
3. Zainstaluj **Windows Communication Foundation aktywację http** w **funkcjach systemu Windows**, **Microsoft .NET Framework 3.5.1**i **Windows Communication Foundation Aktywacja HTTP**.  
  
4. Ten przykład wymaga od klienta ustanowienia bezpiecznego kanału z serwerem, dlatego wymaga obecności certyfikatu serwera, który można zainstalować z Menedżera Internet Information Services (IIS).  
  
    1. Otwórz Menedżera usług IIS. Otwórz przystawkę **Certyfikaty serwera**, która jest wyświetlana na karcie **Widok funkcji** po wybraniu węzła głównego (nazwa komputera).  
  
    2. Na potrzeby testowania tego przykładu Utwórz certyfikat z podpisem własnym. Jeśli nie chcesz, aby program Internet Explorer monitował o certyfikat, który nie jest zabezpieczony, Zainstaluj certyfikat w magazynie głównego urzędu certyfikacji zaufanych certyfikatów.  
  
5. Otwórz okienko **Akcje** dla domyślnej witryny sieci Web. Kliknij pozycję **Edytuj witrynę**, **powiązania**. Dodaj port HTTPS jako typ, jeśli jeszcze nie istnieje, z numerem portu 443. Przypisz certyfikat SSL utworzony w poprzednim kroku.  
  
6. Tworzenie usługi. Spowoduje to utworzenie katalogu wirtualnego w usługach IIS, a następnie skopiowanie plików. dll,. svc i. config, zgodnie z potrzebami, aby usługa była hostowana w sieci Web.  
  
7. Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy katalog wirtualny (**kiedy**), który został utworzony w poprzednim kroku. Wybierz pozycję **Konwertuj na aplikację**.  
  
8. Otwórz moduł **uwierzytelniania** w Menedżerze usług IIS dla tego katalogu wirtualnego i Włącz **uwierzytelnianie systemu Windows**.  
  
9. Otwórz **Ustawienia zaawansowane** w obszarze **uwierzytelnianie systemu Windows** dla tego katalogu wirtualnego i ustaw dla niego wartość **wymagane**.  
  
10. Możesz przetestować usługę, uzyskując dostęp do adresu URL HTTPS z okna przeglądarki (podaj w pełni kwalifikowaną nazwę domeny). Jeśli chcesz uzyskać dostęp do tego adresu URL z komputera zdalnego, upewnij się, że Zapora jest otwarta dla wszystkich przychodzących połączeń HTTP i HTTPS.  
  
11. Otwórz plik konfiguracji klienta i podaj w pełni kwalifikowaną nazwę domeny dla atrybutu adresu klienta lub punktu końcowego, który zastępuje `<<full_machine_name>>`.  
  
12. Uruchom klienta programu. Klient komunikuje się z usługą, która ustanawia bezpieczny kanał i używa ochrony rozszerzonej.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
