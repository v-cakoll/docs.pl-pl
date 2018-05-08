---
title: Ochrona komunikatów za pomocą zabezpieczeń transportu
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 50e450f4241abc7d8b688c58a121f64c3ca0e709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="securing-messages-using-transport-security"></a>Ochrona komunikatów za pomocą zabezpieczeń transportu
W tej sekcji omówiono zabezpieczenia transportu usługi kolejkowania komunikatów (MSMQ), który służy do zabezpieczania komunikatów wysłanych do kolejki.  
  
> [!NOTE]
>  Przed przeczytaniem za pośrednictwem tego tematu, zaleca się przeczytanie [pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Następująca ilustracja przedstawia model koncepcyjny umieszczonych w kolejce komunikacji przy użyciu usługi Windows Communication Foundation (WCF). Ta ilustracja i terminologia służy do opisano pojęcia zabezpieczeń transportu.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejki — rysunek")  
  
 Podczas wysyłania wiadomości z kolejki przy użyciu programu WCF z <xref:System.ServiceModel.NetMsmqBinding>, wiadomości WCF jest dołączony jako treść wiadomości MSMQ. Zabezpieczenia transportu zabezpiecza cały wiadomości MSMQ (nagłówki wiadomości usługi MSMQ lub właściwości i treść komunikatu). Treść wiadomości MSMQ, dlatego też za pomocą zabezpieczeń transportu zabezpiecza wiadomości WCF.  
  
 Koncepcja klucza za zabezpieczeń transportu jest, że klient musi spełniać wymagania dotyczące zabezpieczeń na komunikat do kolejki docelowej. W przeciwieństwie do zabezpieczenia komunikatów to, gdy wiadomość jest zabezpieczona dla aplikacji, która odbiera wiadomości.  
  
 Za pomocą zabezpieczeń transportu <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ma wpływ na sposób zabezpieczonych wiadomości usługi MSMQ podczas przesyłania danych między kolejki transmisji i kolejki docelowej w przypadku, gdy zabezpieczone oznacza:  
  
-   Podpisywanie komunikat, aby upewnić się, że nie jest modyfikowany.  
  
-   Szyfrowanie wiadomości, aby upewnić się, że nie może być widoczne ani przez osoby niepowołane. Jest to zalecane, ale opcjonalne.  
  
-   Menedżera kolejki docelowej identyfikuje nadawcy wiadomości na wyłączność podpisu.  
  
 W usłudze MSMQ niezależnie od uwierzytelniania, kolejka docelowa ma listy kontroli dostępu (ACL), aby sprawdzić, czy klient ma uprawnienia do wysyłania wiadomości do kolejki docelowej. Aplikacja jest również sprawdzane pod kątem uprawnienia do odbierania wiadomości z kolejki docelowej.  
  
## <a name="wcf-msmq-transport-security-properties"></a>Właściwości zabezpieczeń transportu WCF MSMQ  
 Usługa MSMQ do uwierzytelniania używa zabezpieczenia systemu Windows. Używa identyfikatora zabezpieczeń systemu Windows (SID) w celu identyfikacji klienta, a używa usługi katalogowej Active Directory jako urząd certyfikacji do uwierzytelniania klienta. Wymaga usługi MSMQ, które zostaną zainstalowane w integracji usługi Active Directory. Ponieważ identyfikator SID domeny systemu Windows są używane do identyfikacji klienta, ta opcja zabezpieczeń jest przydatny tylko wtedy, gdy klient i usługa są częścią tej samej domeny systemu Windows.  
  
 Usługa MSMQ także możliwość dołączenia certyfikatu z komunikat, który nie jest zarejestrowany w usłudze Active Directory. W takim przypadku gwarantuje, że komunikat był podpisany przy użyciu certyfikatu dołączone.  
  
 Usługi WCF zapewnia obie te opcje jako część zabezpieczeń transportu MSMQ i są one klucza pivot zabezpieczeń transportu.  
  
 Zabezpieczenia transportu jest domyślnie włączona.  
  
 Podana tych podstaw, w poniższych sekcjach przedstawiono właściwości zabezpieczeń transportu szczegółów powiązany z <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Tryb uwierzytelniania usługi MSMQ  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> Określa, czy ma być używany do zabezpieczenia wiadomości zabezpieczeń domeny systemu Windows lub zewnętrznego zabezpieczeń oparte na certyfikatach. W obu tych trybach uwierzytelniania, używa kanału transport z kolejką usługi WCF `CertificateValidationMode` określony w konfiguracji usługi. Tryb walidacji certyfikatu określa mechanizm używany do sprawdzania poprawności certyfikatu.  
  
 Po włączeniu zabezpieczeń transportu jest ustawieniem domyślnym <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Tryb uwierzytelniania domeny systemu Windows  
 Wybór przy użyciu zabezpieczeń systemu Windows wymaga integracji usługi Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> jest to domyślny tryb zabezpieczeń transport. Gdy ta opcja jest ustawiona, kanału WCF dołącza do wiadomości MSMQ identyfikatora SID systemu Windows i używa swojego certyfikatu wewnętrznego uzyskane z usługi Active Directory. Usługa MSMQ używa tego certyfikatu wewnętrznego do zabezpieczenia wiadomości. Odbierającego menedżera kolejek używa usługi Active Directory można wyszukiwać i znalezienia zgodnego certyfikatu uwierzytelniania klienta i sprawdza, czy identyfikator SID również zgodna z wersją klienta. Ten krok uwierzytelniania jest wykonywana w przypadku certyfikatu, albo zostały wygenerowane wewnętrznie w odniesieniu `WindowsDomain` tryb uwierzytelniania lub zewnętrznie wygenerowanych w odniesieniu `Certificate` tryb uwierzytelniania jest dołączony do wiadomości, nawet jeśli jest kolejka docelowa nie jest oznaczone jako wymagające uwierzytelniania.  
  
> [!NOTE]
>  Podczas tworzenia kolejki, kolejki można oznaczyć jako uwierzytelniony kolejki, aby wskazać, że kolejka wymaga uwierzytelnienia klienta, wysyłanie komunikatów do kolejki. Dzięki temu, że nie nieuwierzytelnione komunikaty są akceptowane w kolejce.  
  
 Identyfikator SID podłączonych do komunikatu służy również do sprawdzania zgodności ACL kolejki docelowej, aby upewnić się, że klient ma uprawnienia do wysyłania wiadomości do kolejki.  
  
#### <a name="certificate-authentication-mode"></a>Tryb uwierzytelniania certyfikatów  
 Wybór przy użyciu trybu uwierzytelniania certyfikatu nie wymaga integracji usługi Active Directory. W rzeczywistości w niektórych przypadkach, takich jak kiedy usługa MSMQ jest zainstalowana w trybie grupy roboczej (bez integracji usługi Active Directory) lub gdy przy użyciu protokołu SOAP Reliable Messaging Protocol (SRMP) transfer protocol do wysyłania wiadomości do kolejki, tylko <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> działa.  
  
 Podczas wysyłania wiadomości WCF z <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, kanału WCF nie dołączyć identyfikatora SID systemu Windows do wiadomości MSMQ. Tak, kolejka docelowa ACL musi umożliwić `Anonymous` użytkownikowi dostęp do wysyłania do kolejki. Odbierającego menedżera kolejek sprawdza, czy wiadomości MSMQ została podpisana przy użyciu certyfikatu, ale nie wykonuje żadnego uwierzytelniania.  
  
 Certyfikat z jego oświadczenia i informacje o tożsamości jest wypełniana w <xref:System.ServiceModel.ServiceSecurityContext> przez transport z kolejką kanału WCF. Usługa może wykorzystać te informacje do jego własnej uwierzytelniania nadawcy.  
  
### <a name="msmq-protection-level"></a>Poziom ochrony usługi MSMQ  
 Poziom ochrony mówią, jak chronić wiadomości MSMQ, aby upewnić się, że nie jest modyfikowany od. Jest on określony w <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> właściwości. Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Poziom ochrony logowania  
 Wiadomości MSMQ jest podpisany przy użyciu wewnętrznie wygenerowanego certyfikatu, używając `WindowsDomain` tryb uwierzytelniania lub zewnętrznie wygenerowany certyfikat, używając `Certificate` tryb uwierzytelniania.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Podpisywanie i szyfrowanie z poziomu ochrony  
 Wiadomości MSMQ jest podpisany przy użyciu wewnętrznie wygenerowanego certyfikatu, używając `WindowsDomain` tryb uwierzytelniania lub zewnętrznie wygenerowany certyfikat przy użyciu `Certificate` tryb uwierzytelniania.  
  
 Oprócz podpisywania wiadomości, wiadomości usługi MSMQ są szyfrowane za pomocą klucza publicznego certyfikatu uzyskanego z usługi Active Directory należy odbierającego menedżera kolejek obsługującego kolejki docelowej. Wysyłanie menedżera kolejek zapewnia, że wiadomości usługi MSMQ są szyfrowane podczas przesyłania. Odbierającego menedżera kolejek odszyfrowuje wiadomości MSMQ przy użyciu klucza prywatnego jego wewnętrznego certyfikatu i przechowuje wiadomości w kolejce (jeśli uwierzytelnieniu i autoryzacji) w postaci zwykłego tekstu.  
  
> [!NOTE]
>  Do szyfrowania wiadomości, wymagany jest dostęp do usługi Active Directory (`UseActiveDirectory` właściwość <xref:System.ServiceModel.NetMsmqBinding> musi mieć ustawioną `true`) i może być używany z obu <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> i <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Brak poziomu ochrony  
 Jest to domyślna podczas <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ma ustawioną wartość <xref:System.Net.Security.ProtectionLevel.None>. Nie może to być prawidłową wartością dla innych metod uwierzytelniania.  
  
> [!NOTE]
>  Jeśli wiadomość MSMQ jest podpisana, MSMQ sprawdza, czy komunikat jest podpisany za pomocą dołączonego certyfikatu lub nie (wewnętrzne lub zewnętrzne) niezależnie od stan kolejki, czyli uwierzytelnianego kolejki.  
  
### <a name="msmq-encryption-algorithm"></a>Algorytm szyfrowania usługi MSMQ  
 Algorytm szyfrowania określa algorytm używany do szyfrowania wiadomości MSMQ w sieci. Ta właściwość jest używana tylko wtedy, gdy <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ma ustawioną wartość <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Są obsługiwane algorytmy `RC4Stream` i `AES` , a wartość domyślna to `RC4Stream`.  
  
 Można użyć `AES` algorytm tylko wtedy, gdy nadawca zainstalowaną MSMQ 4.0. Ponadto kolejka docelowa musi być hostowany na MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algorytm wyznaczania wartości skrótu usługi MSMQ  
 Algorytm wyznaczania wartości skrótu Określa algorytm używany do tworzenia podpisu cyfrowego wiadomości MSMQ. Odbierającego menedżera kolejek używa tego samego algorytmu do uwierzytelniania wiadomości MSMQ. Ta właściwość jest używana tylko wtedy, gdy <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ustawiono <xref:System.Net.Security.ProtectionLevel.Sign> lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Są obsługiwane algorytmy `MD5`, `SHA1`, `SHA256`, i `SHA512`. Wartość domyślna to `SHA1`.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi kolejkowania komunikatów](http://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
