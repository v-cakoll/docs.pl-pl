---
title: 'Instrukcje: pobieranie odcisku palca certyfikatu'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: f59fad86287e89b0a573a6e3ee8420f384b0bc3b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601208"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Instrukcje: pobieranie odcisku palca certyfikatu
Podczas pisania aplikacji Windows Communication Foundation (WCF) używającej certyfikatu X. 509 do uwierzytelniania często konieczne jest określenie oświadczeń znalezionych w certyfikacie. Na przykład, należy podać odciskiem palca podczas korzystania z <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> wyliczenia w <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metodzie. Znalezienie wartości Claim wymaga wykonania dwóch kroków. Najpierw otwórz przystawkę Microsoft Management Console (MMC) dla certyfikatów. (Zobacz [How to: View Certificates z przystawką programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md)). Po drugie, zgodnie z opisem w tym miejscu, Znajdź odpowiedni certyfikat i skopiuj jego odcisk palca (lub inne wartości zgłoszeń).  
  
 Jeśli używasz certyfikatu do uwierzytelniania usługi, pamiętaj, aby zanotować wartość kolumny **wystawiony dla** (pierwsza kolumna w konsoli). W przypadku korzystania z SSL (SSL) jako zabezpieczenia transportu jeden z pierwszych testów polega na porównaniu adresu podstawowego Uniform Resource Identifier (URI) usługi do wartości **wystawiony dla** . Wartości muszą być zgodne lub proces uwierzytelniania jest zatrzymany.  
  
 Możesz również użyć polecenia cmdlet New-SelfSignedCertificate programu PowerShell, aby utworzyć tymczasowe certyfikaty do użycia tylko podczas opracowywania. Jednak ten certyfikat nie jest wystawiony przez urząd certyfikacji i nie można go wykorzystać do celów produkcyjnych. Aby uzyskać więcej informacji, zobacz [How to: Create Temporary Certificates for use in Development](how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Aby pobrać odcisk palca certyfikatu  
  
1. Otwórz przystawkę Microsoft Management Console (MMC) dla certyfikatów. (Zobacz [How to: View Certificates z przystawką programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md)).  
  
2. W lewym okienku okna **głównego konsoli** kliknij pozycję **Certyfikaty (komputer lokalny)**.  
  
3. Kliknij folder **osobiste** , aby go rozwinąć.  
  
4. Kliknij folder **Certyfikaty** , aby go rozwinąć.  
  
5. Na liście certyfikatów Zanotuj pozycję **zamierzone cele** . Znajdź certyfikat, który wyświetla listę **uwierzytelniania klienta** jako zamierzony cel.  
  
6. Kliknij dwukrotnie certyfikat.  
  
7. W oknie dialogowym **certyfikat** kliknij kartę **szczegóły** .  
  
8. Przewiń listę pól i kliknij pozycję **odcisk palca**.  
  
9. Skopiuj znaki szesnastkowe z pola. Jeśli ten odcisk palca jest używany w kodzie dla `X509FindType` , Usuń spacje między liczbami szesnastkowymi. Na przykład odcisk palca "A9 09 50 2D D8 2a E4 14 33 E6 F8 38 86 B0 0D 42 77 a3 2a 7b" powinien być określony jako "a909502dd82ae41433e6f83886b00d4277a32a7b" w kodzie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [Instrukcje: konfigurowanie portu z certyfikatem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Instrukcje: Wyświetlanie certyfikatów w przystawce programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania](how-to-create-temporary-certificates-for-use-during-development.md)
