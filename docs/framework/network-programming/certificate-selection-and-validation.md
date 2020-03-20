---
title: Wybór i sprawdzanie poprawności certyfikatu
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: aea47360ab1bb9dad446a5a7b19a91ea688953c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048750"
---
# <a name="certificate-selection-and-validation"></a>Wybór i sprawdzanie poprawności certyfikatu
Klasy <xref:System.Net> obsługują kilka sposobów, aby <xref:System.Security.Cryptography.X509Certificates> wybrać i sprawdzić poprawność dla połączeń SSL (Secure Socket Layer). Klient może wybrać jeden lub więcej certyfikatów do uwierzytelnienia się na serwerze. Serwer może wymagać, aby certyfikat klienta miał co najmniej jeden określony atrybut uwierzytelniania.  
  
## <a name="definition"></a>Definicja  
 Certyfikat jest strumieniem bajtów ASCII, który zawiera klucz publiczny, atrybuty (takie jak numer wersji, numer seryjny i data wygaśnięcia) oraz podpis cyfrowy urzędu certyfikacji. Certyfikaty są używane do ustanawiania połączenia szyfrowanego lub uwierzytelniania klienta na serwerze.  
  
## <a name="client-certificate-selection-and-validation"></a>Wybór i sprawdzanie poprawności certyfikatu klienta  
 Klient może wybrać jeden lub więcej certyfikatów dla określonego połączenia SSL. Certyfikaty klienta mogą być skojarzone z połączeniem SSL z serwerem sieci web lub serwerem poczty SMTP. Klient dodaje certyfikaty do <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> kolekcji lub obiektów klasy. Za pomocą wiadomości e-mail jako przykład, <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection>kolekcja certyfikatów <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> jest <xref:System.Net.Mail.SmtpClient> wystąpieniem ) skojarzone z właściwością klasy. Klasa <xref:System.Net.HttpWebRequest> ma podobną <xref:System.Net.HttpWebRequest.ClientCertificates%2A> właściwość.  
  
 Podstawową różnicą <xref:System.Security.Cryptography.X509Certificates.X509Certificate> między <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasą a klasą jest to, że <xref:System.Security.Cryptography.X509Certificates.X509Certificate> klucz prywatny musi znajdować się w magazynie certyfikatów dla klasy.  
  
 Nawet jeśli certyfikaty są dodawane do kolekcji i skojarzone z określonym połączeniem SSL, żadne certyfikaty nie będą wysyłane do serwera, chyba że serwer ich zażąda. Jeśli w połączeniu ustawiono wiele certyfikatów klienta, najlepiej będzie używany na podstawie algorytmu, który uwzględnia dopasowanie między listą wystawców certyfikatów dostarczonych przez serwer a nazwą wystawcy certyfikatu klienta.  
  
 Klasa <xref:System.Net.Security.SslStream> zapewnia jeszcze większą kontrolę nad uzgadniania SSL. Klient może określić pełnomocnika, który ma wybrać certyfikat klienta do użycia.  
  
 Serwer zdalny może sprawdzić, czy certyfikat klienta jest prawidłowy, aktualny i podpisany przez odpowiedni urząd certyfikacji. Pełnomocnika można dodać <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> do wymuszania sprawdzania poprawności certyfikatu.  
  
## <a name="client-certificate-selection"></a>Wybór certyfikatu klienta  
 Program .NET Framework wybiera certyfikat klienta do zaprezentowania serwerowi w następujący sposób:  
  
1. Jeśli certyfikat klienta został wcześniej przedstawiony serwerowi, certyfikat jest buforowany po pierwszym przedstawieniu i jest ponownie odtwarzany dla kolejnych żądań certyfikatów klienta.  
  
2. Jeśli pełnomocnik jest obecny, zawsze należy użyć wyniku z pełnomocnika jako certyfikat klienta, aby wybrać. Spróbuj użyć buforowanego certyfikatu, jeśli to możliwe, ale nie należy używać buforowanych poświadczeń anonimowych, jeśli pełnomocnik zwrócił wartość null, a kolekcja certyfikatów nie jest pusta.  
  
3. Jeśli jest to pierwsze wyzwanie dla certyfikatu klienta, framework <xref:System.Security.Cryptography.X509Certificates.X509Certificate> wylicza certyfikaty w lub obiektów <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy skojarzonych z połączeniem, szukając dopasowania między listą wystawców certyfikatów dostarczonych przez serwer a nazwą wystawcy certyfikatu klienta. Pierwszy certyfikat, który pasuje, jest wysyłany do serwera. Jeśli żaden certyfikat nie jest zgodny lub kolekcja certyfikatów jest pusta, do serwera są wysyłane anonimowe poświadczenia.  
  
## <a name="tools-for-certificate-configuration"></a>Narzędzia do konfiguracji certyfikatów  
 Wiele narzędzi jest dostępnych dla konfiguracji certyfikatu klienta i serwera.  
  
 Narzędzie *Winhttpcertcfg.exe* może służyć do konfigurowania certyfikatów klientów. Narzędzie *Winhttpcertcfg.exe* jest dostarczane jako jedno z narzędzi z zestawem zasobów systemu Windows Server 2003. To narzędzie jest również dostępne do pobrania w ramach narzędzi zestawu zasobów systemu Windows Server 2003 w [www.microsoft.com](https://www.microsoft.com).  
  
Narzędzie *HttpCfg.exe* może służyć do konfigurowania <xref:System.Net.HttpListener> certyfikatów serwera dla tej klasy. Narzędzie *HttpCfg.exe* jest dostępne jako jedno z narzędzi pomocy technicznej dla systemów Windows Server 2003 i Windows XP z dodatkiem Service Pack 2. *Program HttpCfg.exe* i inne narzędzia pomocy technicznej nie są domyślnie instalowane w systemie Windows Server 2003 lub Windows XP. W systemie Windows Server 2003. narzędzia pomocnicze są instalowane oddzielnie od następującego folderu i pliku na dysku CD-ROM systemu Windows Server 2003:  
  
 \Support\Narzędzia\Suptools.msi  
  
 Do użytku z systemem Windows XP z dodatkiem Service Pack 2 narzędzia pomocy technicznej systemu Windows XP są dostępne do pobrania z [www.microsoft.com](https://www.microsoft.com).  
  
 Kod źródłowy do wersji narzędzia *HttpCfg.exe* jest również dostarczany jako przykład z zestawem SDK systemu Windows Server. Kod źródłowy do przykładu *httpCfg.exe* jest instalowany domyślnie z próbkami sieci w ramach zestawu Windows SDK w następującym folderze:  
  
 *C:\Pliki programów\Zestaw microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Oprócz tych narzędzi <xref:System.Security.Cryptography.X509Certificates.X509Certificate> i <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> klasy zawiera metody ładowania certyfikatu z systemu plików.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia w programowaniu sieciowym](security-in-network-programming.md)
- [Programowanie dla sieci w programie .NET Framework](index.md)
