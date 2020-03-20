---
title: Zasady ochrony rozszerzonej
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 3a5b1c7f296c68d407f0217963dec56f53e9a08a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144725"
---
# <a name="extended-protection-policy"></a>Zasady ochrony rozszerzonej
Extended Protection to inicjatywa bezpieczeństwa chroniąca przed atakami typu man-in-the-middle (MITM). Atak MITM jest zagrożeniem bezpieczeństwa, w którym MITM pobiera poświadczenia klienta i przekazuje go do serwera.  
  
## <a name="demonstrates"></a>Demonstracje  
 Rozszerzona ochrona  
  
## <a name="discussion"></a>Dyskusji  
 Gdy aplikacje uwierzytelniają się przy użyciu protokołu Kerberos, Digest lub NTLM przy użyciu protokołu HTTPS, najpierw ustanawia się kanał TLS (Transport Level Security), a następnie uwierzytelnianie odbywa się przy użyciu bezpiecznego kanału. Jednak nie ma powiązania między kluczem sesji generowanym przez SSL a kluczem sesji wygenerowanym podczas uwierzytelniania. Każdy MITM może ustanowić się między klientem a serwerem i rozpocząć przekazywanie żądań od klienta, nawet jeśli sam kanał transportu jest bezpieczny, ponieważ serwer nie ma możliwości poznania, czy bezpieczny kanał został ustanowiony od klienta lub MITM. Rozwiązaniem w tym scenariuszu jest powiązanie zewnętrznego kanału TLS z wewnętrznym kanałem uwierzytelniania, tak aby serwer mógł wykryć, czy istnieje MITM.  
  
> [!NOTE]
> Ten przykład działa tylko wtedy, gdy jest obsługiwany w u usług IIS i nie może działać na Cassini — Visual Studio Development Server, ponieważ Cassini nie obsługuje protokołu HTTPS.  
  
> [!NOTE]
> Ta funkcja jest obecnie dostępna tylko w systemie Windows 7. Poniższe kroki są specyficzne dla systemu Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Instalowanie internetowych usług informacyjnych z **Panelu sterowania**, **Dodawanie/usuwanie programów**, **Funkcje systemu Windows**.  
  
2. Instalowanie **uwierzytelniania systemu Windows** w **funkcjach systemu Windows,** **internetowych usługach informacyjnych,** **usługach sieci World Wide Web**, **zabezpieczeniach**i **uwierzytelnianiu systemu Windows**.  
  
3. Zainstaluj **aktywację HTTP Programu Windows Communication Foundation** w **funkcjach systemu Windows**, Microsoft **.NET Framework 3.5.1**i **Aktywacja HTTP Programu Windows Communication Foundation**.  
  
4. Ten przykład wymaga od klienta ustanowienia bezpiecznego kanału z serwerem, więc wymaga obecności certyfikatu serwera, który można zainstalować z Menedżera internetowych usług informacyjnych (IIS).  
  
    1. Otwórz Menedżera usług IIS. Otwórz **certyfikaty serwera**, który pojawia się na karcie **Widok funkcji** po wybraniu węzła głównego (nazwa komputera).  
  
    2. Na potrzeby testowania tego przykładu należy utworzyć certyfikat z podpisem własnym. Jeśli nie chcesz, aby program Internet Explorer monity o certyfikat nie jest bezpieczny, zainstaluj certyfikat w magazynie urzędów głównych zaufanych certyfikatów.  
  
5. Otwórz okienko **Akcje** dla domyślnej witryny sieci Web. Kliknij **pozycję Edytuj witrynę**, **Powiązania**. Dodaj protokół HTTPS jako typ, jeśli jeszcze go nie ma, z numerem portu 443. Przypisz certyfikat SSL utworzony w poprzednim kroku.  
  
6. Zbuduj usługę. Spowoduje to utworzenie katalogu wirtualnego w usługach IIS i skopiowanie plików .dll, .svc i .config zgodnie z wymaganiami dla usługi hostowanej w sieci Web.  
  
7. Otwórz Menedżera usług IIS. Kliknij prawym przyciskiem myszy katalog wirtualny **(ExtendedProtection),** który został utworzony w poprzednim kroku. Wybierz **opcję Konwertuj na aplikację**.  
  
8. Otwórz moduł **Uwierzytelniania** w Menedżerze usług IIS dla tego katalogu wirtualnego i włącz **uwierzytelnianie systemu Windows**.  
  
9. Otwórz **pozycję Ustawienia zaawansowane** w obszarze **Uwierzytelnianie systemu Windows** dla tego katalogu **wirtualnego**i ustaw go na Wymagane .  
  
10. Usługę można przetestować, uzyskując dostęp do adresu URL HTTPS w oknie przeglądarki (Podaj w pełni kwalifikowaną nazwę domeny). Jeśli chcesz uzyskać dostęp do tego adresu URL z komputera zdalnego, upewnij się, że zapora jest otwarta dla wszystkich przychodzących połączeń HTTP i HTTPS.  
  
11. Otwórz plik konfiguracji klienta i podaj w pełni kwalifikowaną nazwę domeny `<<full_machine_name>>`dla atrybutu adresu klienta lub punktu końcowego, który zastępuje .  
  
12. Uruchom klienta. Klient komunikuje się z usługą, która ustanawia bezpieczny kanał i korzysta z rozszerzonej ochrony.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
