---
title: Ochrona komunikatów za pomocą zabezpieczeń transportu
ms.date: 03/30/2017
ms.assetid: 9029771a-097e-448a-a13a-55d2878330b8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0ab04326404a4b90e30036594a7152e6118c2138
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556341"
---
# <a name="securing-messages-using-transport-security"></a>Ochrona komunikatów za pomocą zabezpieczeń transportu
W tej sekcji omówiono zabezpieczenia transportu usługi kolejkowania komunikatów (MSMQ) używanego do zabezpieczenia komunikatów wysłanych do kolejki.  
  
> [!NOTE]
>  Przed odczytaniem za pośrednictwem tego tematu, zaleca się przeczytanie [pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Następująca ilustracja przedstawia model koncepcyjny umieszczonych w kolejce komunikacji przy użyciu usługi Windows Communication Foundation (WCF). Ta ilustracja i terminologii służy do wyjaśnienia pojęcia dotyczące zabezpieczeń transportu.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejka rysunek")  
  
 Podczas wysyłania wiadomości w kolejce przy użyciu usługi WCF z <xref:System.ServiceModel.NetMsmqBinding>, wiadomości WCF jest dołączony jako treść wiadomości usługi MSMQ. Zabezpieczenia transportu zabezpiecza całą wiadomości usługi MSMQ (nagłówków wiadomości usługi MSMQ lub właściwości i treść wiadomości). Ponieważ jest ona treści wiadomości usługi MSMQ, również za pomocą zabezpieczeń transportu zabezpiecza komunikatów WCF.  
  
 Kluczową koncepcją za zabezpieczenia transportu jest, że klient ma pod kątem wymagań zabezpieczeń jest wyświetlany komunikat do kolejki docelowej. Jest to w przeciwieństwie do zabezpieczenia komunikatów, której wiadomość jest zabezpieczona dla aplikacji, która odbiera komunikaty.  
  
 Za pomocą zabezpieczeń transportu <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ma wpływ na sposób zabezpieczonych wiadomości usługi MSMQ w drodze między kolejki transmisji i kolejka docelowa w przypadku, gdy chronione oznacza:  
  
-   Podpisywanie komunikat, aby upewnić się, że nie zostanie naruszony.  
  
-   Szyfrowanie wiadomości, aby upewnić się, że nie może być widoczny ani zmodyfikowane. Jest to zalecane, ale opcjonalne.  
  
-   Menedżer kolejki docelowej identyfikuje nadawcy wiadomości na wyłączność podpisu.  
  
 W usłudze MSMQ niezależnie od uwierzytelniania, kolejka docelowa ma listy kontroli dostępu (ACL), aby sprawdzić, czy klient ma uprawnienia do wysyłania wiadomości do kolejki docelowej. Aplikacja jest również sprawdzane pod kątem uprawnienia do odbierania wiadomości z kolejki docelowej.  
  
## <a name="wcf-msmq-transport-security-properties"></a>Właściwości zabezpieczeń transportu WCF MSMQ  
 Usługa MSMQ używa zabezpieczeń Windows do uwierzytelniania. Używa Windows identyfikator zabezpieczeń (SID) do identyfikacji klienta i używa usługi Active Directory jako urzędu certyfikacji podczas uwierzytelniania klienta. Wymaga to usługi MSMQ, które zostaną zainstalowane w integracji usługi Active Directory. Ponieważ identyfikator SID domeny Windows są używane do identyfikacji klienta, ta opcja zabezpieczeń jest przydatny tylko wtedy, gdy klient i usługa są częścią tej samej domenie Windows.  
  
 Usługa MSMQ także możliwość dołączenia certyfikatu z komunikat, który nie jest zarejestrowany w usłudze Active Directory. W tym przypadku gwarantuje, że komunikat został podpisany za pomocą dołączonego certyfikatu.  
  
 WCF zapewnia obie te opcje, jako część zabezpieczenia transportu usługi MSMQ i są kluczowe pivot dla zabezpieczeń transportu.  
  
 Zabezpieczenia transportu jest domyślnie włączona.  
  
 Biorąc pod uwagę te podstawy, następujące sekcje właściwości zabezpieczeń transportu szczegóły powiązane z <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
#### <a name="msmq-authentication-mode"></a>Tryb uwierzytelniania usługi MSMQ  
 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> Określa, czy ma być używany do zabezpieczenia wiadomości zabezpieczeń domeny Windows lub zewnętrznego zabezpieczenia oparte na certyfikatach. W obu trybach uwierzytelniania używa kanał transportowy umieszczonych w kolejce WCF `CertificateValidationMode` określony w konfiguracji usługi. Tryb walidacji certyfikatu określa mechanizm służący do sprawdzania poprawności certyfikatu.  
  
 Po włączeniu zabezpieczeń transportu jest ustawieniem domyślnym <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="windows-domain-authentication-mode"></a>Tryb uwierzytelniania systemu Windows domeny  
 Wybór za pomocą zabezpieczeń Windows wymaga integracji usługi Active Directory. <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain> jest to domyślny tryb zabezpieczeń transport. Gdy ta opcja jest ustawiona, kanału WCF dołącza identyfikator SID Windows do wiadomości usługi MSMQ i używa swojego certyfikatu wewnętrznego uzyskane z usługi Active Directory. Usługa MSMQ używa tego certyfikatu wewnętrznego do zabezpieczenia wiadomości. Odbieranie Menedżer kolejki używa usługi Active Directory do wyszukiwania i znajdowania zgodnego certyfikatu do uwierzytelniania klienta i sprawdza, czy identyfikator SID również architekturze i językowi klienta. W tym kroku uwierzytelniania jest wykonywane, jeśli certyfikat, albo wewnętrznie generowane w przypadku właściwości `WindowsDomain` tryb uwierzytelniania lub zewnętrznie generowane w przypadku właściwości `Certificate` tryb uwierzytelniania jest dołączony do wiadomości, nawet jeśli jest kolejka docelowa nie jest oznaczony jako wymagające uwierzytelniania.  
  
> [!NOTE]
>  Podczas tworzenia kolejki, kolejki można oznaczyć jako uwierzytelniony kolejki, aby wskazać, że kolejka wymaga uwierzytelnienia klienta, wysyłanie komunikatów do kolejki. Daje to gwarancję, że żadne nieuwierzytelnionych wiadomości są akceptowane w kolejce.  
  
 Dołączono identyfikator SID wiadomości służy także do sprawdzania listy ACL do kolejki docelowej, aby upewnić się, że klient ma uprawnienia do wysyłania komunikatów do kolejki.  
  
#### <a name="certificate-authentication-mode"></a>Tryb uwierzytelniania certyfikatów  
 Do wyboru używania trybu uwierzytelniania certyfikatu nie wymaga integracji usługi Active Directory. W rzeczywistości w niektórych przypadkach, np. gdy usługa MSMQ jest zainstalowana w trybie grupy roboczej (bez integracji usługi Active Directory) lub przy użyciu protokołu SOAP Reliable Messaging Protocol (SRMP) podczas transferu protokołu, aby wysyłać komunikaty do kolejki, tylko <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> działa.  
  
 Podczas wysyłania wiadomości WCF za pomocą <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, kanału usługi WCF nie dołączy Windows SID do wiadomości usługi MSMQ. W efekcie kolejka docelowa listy ACL musi umożliwiać korzystanie z `Anonymous` dostęp użytkowników do wysłania do kolejki. Menedżera kolejki odbierającej sprawdza, czy wiadomości usługi MSMQ została podpisana przy użyciu certyfikatu, ale nie wykonuje żadnego uwierzytelniania.  
  
 Certyfikat z oświadczenia i informacje o tożsamości jest wypełniana w <xref:System.ServiceModel.ServiceSecurityContext> przez kanał transportowy umieszczonych w kolejce usługi WCF. Usługa może wykorzystać te informacje do wykonania własnym uwierzytelnianiem nadawcy.  
  
### <a name="msmq-protection-level"></a>Poziom ochrony usługi MSMQ  
 Jak chronić wiadomości usługi MSMQ, aby upewnić się, że nie jest modyfikowany od połączenia z opisywanym poziom ochrony. Jest ono określone w <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> właściwości. Wartość domyślna to <xref:System.Net.Security.ProtectionLevel.Sign>.  
  
#### <a name="sign-protection-level"></a>Poziom ochrony logowania  
 Wiadomości usługi MSMQ jest podpisany przy użyciu certyfikatu wewnętrznie generowane, gdy za pomocą `WindowsDomain` tryb uwierzytelniania lub zewnętrznie wygenerowany certyfikat, korzystając z `Certificate` tryb uwierzytelniania.  
  
#### <a name="sign-and-encrypt-protection-level"></a>Podpisywanie i szyfrowanie poziom ochrony  
 Wiadomości usługi MSMQ jest podpisany przy użyciu certyfikatu wewnętrznie generowane, gdy za pomocą `WindowsDomain` tryb uwierzytelniania lub zewnętrznie wygenerowany certyfikat, korzystając z `Certificate` tryb uwierzytelniania.  
  
 Oprócz podpisywania wiadomości, wiadomości usługi MSMQ są szyfrowane za pomocą klucza publicznego certyfikatu uzyskanego z usługi Active Directory, należącego do odbieranie menedżera kolejek, który jest hostem kolejka docelowa. Menedżer kolejki wysyłania gwarantuje, że wiadomości usługi MSMQ są szyfrowane podczas przesyłania. Odbieranie Menedżer kolejki odszyfrowuje wiadomości usługi MSMQ, za pomocą klucza prywatnego jego certyfikatu wewnętrznego i zapisuje komunikat w kolejce (Jeśli uwierzytelnianie i autoryzowanie) w postaci zwykłego tekstu.  
  
> [!NOTE]
>  Aby zaszyfrować wiadomości, wymagany jest dostęp usługi Active Directory (`UseActiveDirectory` właściwość <xref:System.ServiceModel.NetMsmqBinding> musi być równa `true`) i mogą być używane z obu <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> i <xref:System.ServiceModel.MsmqAuthenticationMode.WindowsDomain>.  
  
#### <a name="none-protection-level"></a>Brak poziomów ochrony  
 To jest implikowane przy <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ustawiono <xref:System.Net.Security.ProtectionLevel.None>. Nie może to być prawidłową wartością dla innych trybów uwierzytelniania.  
  
> [!NOTE]
>  W przypadku wiadomości usługi MSMQ jest podpisany, MSMQ sprawdza, czy komunikat jest podpisany za pomocą dołączonego certyfikatu (wewnętrznego lub zewnętrznego), niezależnie od stanu, kolejki, czyli uwierzytelnianego kolejki lub nie.  
  
### <a name="msmq-encryption-algorithm"></a>Algorytm szyfrowania usługi MSMQ  
 Algorytm szyfrowania określa algorytm używany do szyfrowania wiadomości usługi MSMQ na łączu. Ta właściwość jest używana tylko wtedy, gdy <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ustawiono <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Są obsługiwane algorytmy `RC4Stream` i `AES` i wartość domyślna to `RC4Stream`.  
  
 Możesz użyć `AES` algorytm tylko wtedy, gdy nadawca został zainstalowany w usłudze MSMQ 4.0. Ponadto kolejka docelowa musi być hostowany w usłudze MSMQ 4.0.  
  
### <a name="msmq-hash-algorithm"></a>Algorytm wyznaczania wartości skrótu usługi MSMQ  
 Algorytm wyznaczania wartości skrótu Określa algorytm używany do tworzenia podpisu cyfrowego wiadomości usługi MSMQ. Odbieranie Menedżer kolejki używa tego samego algorytmu do uwierzytelniania wiadomości usługi MSMQ. Ta właściwość jest używana tylko wtedy, gdy <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> ustawiono <xref:System.Net.Security.ProtectionLevel.Sign> lub <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Są obsługiwane algorytmy `MD5`, `SHA1`, `SHA256`, i `SHA512`. Wartość domyślna to `SHA1`.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługa kolejkowania komunikatów](https://msdn.microsoft.com/library/ff917e87-05d5-478f-9430-0f560675ece1)  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
