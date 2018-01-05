---
title: "Wybór certyfikatu i sprawdzania poprawności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 54d1409b74793a8539f432ce0b43f410d578e934
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-selection-and-validation"></a>Wybór certyfikatu i sprawdzania poprawności
<xref:System.Net> Klasy obsługuje kilka sposobów, aby wybrać i zweryfikować <xref:System.Security.Cryptography.X509Certificates> dla połączeń Secure Socket Layer (SSL). Klient może wybrać co najmniej jednego certyfikatu do samodzielnego uwierzytelnienia do serwera. Serwer może wymagać, aby certyfikat klienta ma jeden lub więcej atrybutów określonych dla uwierzytelniania.  
  
## <a name="definition"></a>Definicja  
 Certyfikat jest strumień bajtów ASCII, który zawiera klucz publiczny, atrybuty (takie jak numer wersji, numer seryjny i datę wygaśnięcia) i podpis cyfrowy z urzędu certyfikacji. Certyfikaty są używane do nawiązywania zaszyfrowanego połączenia lub do uwierzytelniania klienta na serwerze.  
  
## <a name="client-certificate-selection-and-validation"></a>Wyboru certyfikatu klienta i sprawdzania poprawności  
 Klient może wybrać co najmniej jednego certyfikatu dla określonego połączenia SSL. Certyfikaty klienta można skojarzyć z połączenia SSL z serwerem sieci web lub serwera poczty SMTP. Klient dodaje certyfikaty do kolekcji <xref:System.Security.Cryptography.X509Certificates.X509Certificate> lub <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy obiektów. Na przykład za pomocą poczty e-mail, kolekcję certyfikatów jest wystąpieniem <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>) skojarzone z <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> właściwość <xref:System.Net.Mail.SmtpClient> klasy. <xref:System.Net.HttpWebRequest> Klasa ma podobne <xref:System.Net.HttpWebRequest.ClientCertificates%2A> właściwości.  
  
 Główną różnicą między <xref:System.Security.Cryptography.X509Certificates.X509Certificate> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy jest, że klucz prywatny musi znajdować się w magazynie certyfikatów dla <xref:System.Security.Cryptography.X509Certificates.X509Certificate> klasy.  
  
 Nawet jeśli certyfikaty są dodawane do kolekcji i skojarzone z określonego połączenia SSL, certyfikaty nie będą wysyłane do serwera, chyba że serwer zażąda ich. Jeśli wiele certyfikatów klienta są skonfigurowane na połączenie, najlepiej, który będzie służyć oparte na algorytm uwzględnia pasuje do listy wystawców certyfikatów dostarczanych przez serwer i nazwę wystawcy certyfikatu klienta.  
  
 <xref:System.Net.Security.SslStream> Klasy zapewnia większą kontrolę nad procedury uzgadniania protokołu SSL. Klienta można określić pełnomocnika, aby wybrać certyfikat klienta.  
  
 Serwer zdalny można sprawdzić, czy certyfikat klienta jest prawidłowa, bieżący i podpisany przez urząd certyfikacji odpowiednie. Delegat mogą być dodawane do <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> wymusić sprawdzanie poprawności certyfikatu.  
  
## <a name="client-certificate-selection"></a>Wyboru certyfikatu klienta  
 .NET Framework wybiera certyfikatu klienta, aby przekazać do serwera w następujący sposób:  
  
1.  Jeśli certyfikat klienta został przedstawiony wcześniej na serwerze, certyfikat jest buforowany podczas najpierw przedstawione i zostanie ponownie użyty dla kolejnych żądań certyfikatów.  
  
2.  Jeśli delegat jest obecny, zawsze używać wyniku delegata jako certyfikat klienta do wybrania. Spróbuj użyć buforowanego certyfikatu, jeśli to możliwe, ale nie należy używać pamięci podręcznej poświadczeń anonimowego, jeśli obiekt delegowany zwrócił wartość zerową i kolekcję certyfikatów nie jest pusta.  
  
3.  Jeśli jest to pierwsze żądanie certyfikatu klienta, platformę wylicza certyfikaty <xref:System.Security.Cryptography.X509Certificates.X509Certificate> lub <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy obiektów skojarzonych z tym połączeniem, wyszukiwanie dopasowanie między lista wystawców certyfikatów dostarczone przez serwer i nazwę wystawcy certyfikatu klienta. Pierwszy certyfikatu, który odpowiadałby są wysyłane do serwera. Jeśli odpowiedników certyfikatu lub kolekcji certyfikatu jest pusty, a następnie anonimowe poświadczenia są wysyłane do serwera.  
  
## <a name="tools-for-certificate-configuration"></a>Narzędzia do konfiguracji certyfikatów  
 Wiele narzędzi dostępnych dla klienta i serwera konfiguracji certyfikatu.  
  
 *Winhttpcertcfg.exe* narzędzie służy do konfigurowania certyfikatów klienta. *Winhttpcertcfg.exe* narzędzie jest dostępna w jednym z narzędzi z systemem Windows Server 2003 Resource Kit. To narzędzie jest również dostępny do pobrania jako część narzędzi systemu Windows Server 2003 Resource Kit, na www.microsoft.com.  
  
 *HttpCfg.exe* narzędzie służy do konfigurowania certyfikatów serwera dla <xref:System.Net.HttpListener> klasy. *HttpCfg.exe* narzędzie jest dostarczane jako jednego z narzędzi obsługi systemu Windows Server 2003 i Windows XP z dodatkiem Service Pack 2. *HttpCfg.exe* i inne narzędzia pomocy technicznej nie są instalowane domyślnie w systemie Windows Server 2003 lub Windows XP. W systemie Windows Server 2003. Narzędzia obsługi są instalowane osobno z następującego folderu i pliku na dysku CD systemu Windows Server 2003:  
  
 \Support\Tools\Suptools.msi  
  
 Do użytku z systemem Windows XP Service Pack 2 narzędzi obsługi systemu Windows XP są dostępne do pobrania z www.microsoft.com.  
  
 Kod źródłowy do wersji *HttpCfg.exe* narzędzie jest również udostępniany jako próbka przy użyciu zestawu SDK serwera systemu Windows. Aby kod źródłowy *HttpCfg.exe* próbki jest instalowany domyślnie z sieci próbek, jako część zestawu Windows SDK w następującym folderze:  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Oprócz tych narzędzi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy udostępnia metody ładowania certyfikatu w systemie plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia w programowaniu sieciowym](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [Programowanie dla sieci w programie .NET Framework](../../../docs/framework/network-programming/index.md)
