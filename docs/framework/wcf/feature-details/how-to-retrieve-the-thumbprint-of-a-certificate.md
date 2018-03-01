---
title: 'Porady: Pobieranie odcisku palca certyfikatu'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f6d00d31023aa8d6dbfec4a8306f1cb9da17c74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Porady: Pobieranie odcisku palca certyfikatu
Podczas zapisywania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji, która używa certyfikatu X.509 do uwierzytelniania, często jest niezbędne do określenia oświadczenia, znalezione w certyfikacie. Na przykład, należy podać oświadczenie odcisk palca podczas przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> wyliczanie w <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody. Znajdowanie wartość oświadczenia wymaga wykonania dwóch kroków. Po pierwsze Otwórz przystawkę Microsoft Management Console (MMC) dla certyfikatów. (Zobacz [porady: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Po drugie zgodnie z opisem w tym miejscu, Znajdź odpowiedni certyfikat i skopiuj jego odcisk palca (lub inne wartości oświadczenia).  
  
 Jeśli używasz certyfikatu dla usługi uwierzytelniania, ważne jest, aby Zanotuj wartość ustawienia **wystawiony** kolumny (pierwszej kolumny w konsoli). Gdy przy użyciu protokołu Secure Sockets Layer (SSL), zgodnie z zabezpieczeń transportu, jeden najpierw sprawdza, czy wykonywane jest porównanie bazie adres URI Uniform Resource Identifier () do usługi **wystawiony** wartość. Wartości muszą być zgodne, lub proces uwierzytelniania jest zatrzymany.  
  
 Można także użyć narzędzia Makecert.exe z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zestawu SDK do tworzenia certyfikatów tymczasowych do użytku tylko podczas programowania. Domyślnie jednak taki certyfikat nie jest wystawiany przez urząd certyfikacji, a nie nadaje się do celów produkcyjnych. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Tworzenie certyfikatów tymczasowych do użycia podczas tworzenia](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Aby pobrać odcisk palca certyfikatu  
  
1.  Otwórz przystawkę Microsoft Management Console (MMC) dla certyfikatów. (Zobacz [porady: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2.  W **katalog główny konsoli** okna na lewe okienko, kliknij przycisk **certyfikaty (komputer lokalny)**.  
  
3.  Kliknij przycisk **osobistych** folderu, aby go rozwinąć.  
  
4.  Kliknij przycisk **certyfikaty** folderu, aby go rozwinąć.  
  
5.  Lista certyfikatów, zanotuj **zamierzone cele** nagłówka. Znalezienie certyfikatu, który zawiera listę **uwierzytelnianie klienta** jako przeznaczenie.  
  
6.  Kliknij dwukrotnie certyfikat.  
  
7.  W **certyfikatu** okno dialogowe, kliknij przycisk **szczegóły** kartę.  
  
8.  Przewiń listę pól, a następnie kliknij przycisk **odcisk palca**.  
  
9. Kopiowanie znaków szesnastkowych, w polu. Jeśli taki odcisk palca jest używana w kodzie `X509FindType`, Usuń spacje między cyfry szesnastkowe. Na przykład odciskiem palca "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" powinny być określone jako "a909502dd82ae41433e6f83886b00d4277a32a7b" w kodzie.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Instrukcje: konfigurowanie portu z certyfikatem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Instrukcje: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
