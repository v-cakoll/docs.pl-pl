---
title: Zasady ochrony rozszerzonej
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef77df0681f7177a3b006b84d5ed3b60b7954555
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="extended-protection-policy"></a>Zasady ochrony rozszerzonej
Ochrona rozszerzona jest inicjatywą zabezpieczeń w celu ochrony przed atakami typu man-in--middle (MITM). Ataki MITM to zagrożenie bezpieczeństwa, w którym MITM przyjmuje poświadczenia klienta i przekazuje je do serwera.  
  
## <a name="demonstrates"></a>Demonstracje  
 Ochrona rozszerzona  
  
## <a name="discussion"></a>Omówienie  
 Aplikacje uwierzytelniania przy użyciu protokołu Kerberos, szyfrowane lub NTLM przy użyciu protokołu HTTPS, najpierw zostanie nawiązane kanał zabezpieczeń TLS (Transport Level), a następnie uwierzytelnianie odbywa się przy użyciu bezpiecznego kanału. Jednakże nie istnieje żadne powiązanie między kluczem sesji wygenerowane za pomocą protokołu SSL i klucza sesji generowane podczas uwierzytelniania. Wszelkie MITM mogą nawiązać się między klientem a serwerem i Rozpocznij przesyłanie żądań z klienta, nawet jeśli sam kanał transportu jest bezpieczne, ponieważ serwer nie ma możliwości wiedzy czy bezpiecznego kanału została ustanowiona z klienta lub MITM. To rozwiązanie w tym scenariuszu można powiązać zewnętrzne kanał TLS z kanałem wewnętrzny uwierzytelniania w taki sposób, że serwer może wykryć, czy jest MITM.  
  
> [!NOTE]
>  W tym przykładzie tylko działa, gdy hostowanych w usługach IIS i nie może działać na Cassini — serwera wdrożeniowego Visual Studio, ponieważ Cassini nie obsługuje protokołu HTTPS.  
  
> [!NOTE]
>  Ta funkcja jest obecnie tylko dostępne w systemie Windows 7. Poniższe kroki są specyficzne dla systemu Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstalować Internetowe usługi informacyjne z **Panel sterowania**, **Dodaj/Usuń programy**, **funkcje systemu Windows**.  
  
2.  Zainstaluj **uwierzytelniania systemu Windows** w **funkcje systemu Windows**, **Internetowe usługi informacyjne**, **usługi sieci World Wide Web**,  **Zabezpieczenia**, i **uwierzytelniania systemu Windows**.  
  
3.  Zainstaluj **aktywacji systemu Windows Communication Foundation HTTP** w **funkcje systemu Windows**, **Microsoft .NET Framework 3.5.1**, i **komunikacji z systemem Windows Aktywacja Foundation HTTP**.  
  
4.  W tym przykładzie wymaga klienta do ustanowienia bezpiecznego kanału z serwerem, dzięki czemu wymaga obecności certyfikat serwera, które można zainstalować z programu Internet Information Services (IIS) Manager.  
  
    1.  Otwórz Menedżera usług IIS. Otwórz **certyfikaty serwera**, która jest wyświetlana w **widoku funkcji** karcie po wybraniu węzła głównego (nazwa komputera).  
  
    2.  Na potrzeby testowania tego przykładu, należy utworzyć certyfikat z podpisem własnym. Jeśli chcesz, aby program Internet Explorer będzie wyświetlany monit o certyfikat nie jest bezpieczne, należy zainstalować certyfikat w magazynie zaufanego certyfikatu głównego urzędu.  
  
5.  Otwórz **akcje** okienko dla domyślnej witryny sieci Web. Kliknij przycisk **edytowanie witryny**, **powiązania**. Dodaj HTTPS jako typ Jeśli nie są jeszcze zainstalowane, z numerem portu 443. Przypisania certyfikatu SSL utworzony w poprzednim kroku.  
  
6.  Tworzenie usługi. Tworzy katalog wirtualny w usługach IIS i kopiuje pliki dll, SVC i config zgodnie z wymogami usługa jest hostowana w sieci Web.  
  
7.  Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy folder wirtualny (**ochrona rozszerzona**), który został utworzony w poprzednim kroku. Wybierz **Konwertuj na aplikację**.  
  
8.  Otwórz **uwierzytelniania** modułu w Menedżerze usług IIS dla tego katalogu wirtualnego i Włącz **uwierzytelniania systemu Windows**.  
  
9. Otwórz **Zaawansowane ustawienia** w obszarze **uwierzytelniania systemu Windows** dla tego katalogu wirtualnego i ustaw ją na **wymagane**.  
  
10. Można testować usługę, uzyskując dostęp do adresu URL HTTPS z okna przeglądarki (podaj w pełni kwalifikowaną nazwą domeny). Aby uzyskać dostęp do tego adresu URL z komputera zdalnego, upewnij się, że zapory jest otwarty dla wszystkich połączeń przychodzących HTTP i HTTPS.  
  
11. Otwórz plik konfiguracji klienta i podaj nazwę domeny w pełni kwalifikowaną atrybut adresu klienta lub punkt końcowy, który zastępuje `<<full_machine_name>>`.  
  
12. Uruchom klienta. Klient komunikuje się z usługą, ustanawia bezpiecznego kanału, która używa ochrony rozszerzonej.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
