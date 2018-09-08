---
title: Wybór certyfikatu i sprawdzanie poprawności
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fe3b10e17c3cdf181f0b33b4305008655047fb0f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211921"
---
# <a name="certificate-selection-and-validation"></a>Wybór certyfikatu i sprawdzanie poprawności
<xref:System.Net> Klasy obsługują kilka sposobów, aby wybrać i zweryfikować <xref:System.Security.Cryptography.X509Certificates> dla połączeń Secure Socket Layer (SSL). Klient może wybrać jeden lub kilka certyfikatów, aby uwierzytelniać się z serwerem. Serwer może wymagać, że jeden lub więcej określonych atrybutów do uwierzytelniania certyfikatu klienta.  
  
## <a name="definition"></a>Definicja  
 Certyfikat jest strumień bajtów ASCII, który zawiera klucz publiczny, atrybutów (na przykład numer wersji, numer seryjny i datę wygaśnięcia) i podpis cyfrowy z urzędu certyfikacji. Certyfikaty są używane do nawiązywania zaszyfrowanego połączenia lub do uwierzytelniania klienta do serwera.  
  
## <a name="client-certificate-selection-and-validation"></a>Wyboru certyfikatu klienta i sprawdzanie poprawności  
 Klient może wybrać co najmniej jednego certyfikatu dla określonego połączenia SSL. Certyfikaty klienta można skojarzyć z połączenia SSL na serwerze sieci web lub serwera poczty SMTP. Klient dodaje certyfikaty do kolekcji <xref:System.Security.Cryptography.X509Certificates.X509Certificate> lub <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy obiektów. Za pomocą poczty e-mail, na przykład, kolekcję certyfikatów jest wystąpieniem <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) skojarzony z <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> właściwość <xref:System.Net.Mail.SmtpClient> klasy. <xref:System.Net.HttpWebRequest> Klasa ma podobny <xref:System.Net.HttpWebRequest.ClientCertificates%2A> właściwości.  
  
 Główną różnicą między <xref:System.Security.Cryptography.X509Certificates.X509Certificate> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasa jest, że klucz prywatny musi znajdować się w magazynie certyfikatów dla <xref:System.Security.Cryptography.X509Certificates.X509Certificate> klasy.  
  
 Nawet, jeśli certyfikaty są dodawane do kolekcji i skojarzone z określonego połączenia SSL, certyfikaty nie będą wysyłane do serwera, chyba, że serwer zażąda je. Jeśli w przypadku połączenia wielu certyfikatów klienta, najlepiej, który będzie służyć oparte na algorytm, który uwzględnia zgodność między listy wystawców certyfikatów dostarczonych przez serwer i nazwę wystawcy certyfikatu klienta.  
  
 <xref:System.Net.Security.SslStream> Klasy zapewnia większą kontrolę nad uzgadniania protokołu SSL. Klienta można określić obiekt delegowany, aby wybrać certyfikat klienta.  
  
 Serwer zdalny można sprawdzić, czy certyfikat klienta jest prawidłowy, bieżące i podpisane przez odpowiedni urząd certyfikacji. Obiekt delegowany mogą być dodawane do <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> do wymuszania weryfikacji certyfikatu.  
  
## <a name="client-certificate-selection"></a>Wyboru certyfikatu klienta  
 .NET Framework wybiera certyfikat klienta do przedstawienia na serwer w następujący sposób:  
  
1.  Jeśli certyfikat klienta został przedstawiony wcześniej do serwera, certyfikat są buforowane, gdy najpierw przedstawiony zostanie ponownie użyty dla kolejnych żądań certyfikatów.  
  
2.  Jeśli obiekt delegowany jest obecny, zawsze używać wynikiem delegata jako certyfikat klienta do wybrania. Spróbuj użyć pamięci podręcznej certyfikatu, jeśli jest to możliwe, ale nie należy używać pamięci podręcznej poświadczenia anonimowe, jeśli pełnomocnik ma zwróciła wartość null i kolekcję certyfikatów nie jest pusty.  
  
3.  Jeśli jest to pierwsze wyzwanie dla certyfikatu klienta, Framework wylicza certyfikaty <xref:System.Security.Cryptography.X509Certificates.X509Certificate> lub <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy obiektów skojarzonych z tym połączeniem szuka dopasowania między listy wystawców certyfikatów, dostarczone przez serwer i nazwę wystawcy certyfikatu klienta. Pierwszy certyfikat, który odpowiada są wysyłane do serwera. Jeśli nie dopasowania certyfikatu lub kolekcję certyfikatów jest pusty, a następnie poświadczenia anonimowe są wysyłane do serwera.  
  
## <a name="tools-for-certificate-configuration"></a>Narzędzia do konfiguracji certyfikatu  
 Wiele narzędzi, są dostępne dla klienta i serwera konfiguracji certyfikatu.  
  
 *Winhttpcertcfg.exe* narzędzie może służyć do konfigurowania certyfikatów klienta. *Winhttpcertcfg.exe* narzędzie jest dostarczane jako jedno z narzędzi w programie Windows Server 2003 Resource Kit. To narzędzie jest również dostępny do pobrania w ramach systemu Windows Server 2003 Resource Kit Tools w [www.microsoft.com](https://www.microsoft.com).  
  
*HttpCfg.exe* narzędzie może służyć do konfigurowania certyfikatów serwera wdrażania <xref:System.Net.HttpListener> klasy. *HttpCfg.exe* narzędzie jest dostarczane jako jedno z narzędzi obsługi systemu Windows Server 2003 i Windows XP Service Pack 2. *HttpCfg.exe* i inne narzędzia pomocy technicznej nie są instalowane domyślnie w systemie Windows Server 2003 lub Windows XP. W systemie Windows Server 2003. narzędzia pomocy technicznej są instalowane osobno od następujący folder i plik na dysku CD systemu Windows Server 2003:  
  
 \Support\Tools\Suptools.msi  
  
 Do użytku z systemu Windows XP Service Pack 2, narzędzia obsługi Windows XP są dostępne do pobrania z [www.microsoft.com](https://www.microsoft.com).  
  
 Kod źródłowy do wersji *HttpCfg.exe* narzędzie jest także podany jako przykład z zestawem SDK systemu Windows Server. Kod źródłowy w celu *HttpCfg.exe* próbki jest instalowany domyślnie w z przykładami sieci, jako część zestawu Windows SDK w następującym folderze:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Oprócz tych narzędzi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy udostępnia metody ładowania certyfikatu z systemu plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
