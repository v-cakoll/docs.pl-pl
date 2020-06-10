---
title: 'Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 103d68d4ccb4cc243d28037260c1f9f380485ff6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600312"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)
Gdy Windows Communication Foundation (WCF) odbiera komunikat protokołu SOAP podpisany przy użyciu certyfikatu X. 509, domyślnie weryfikuje, czy certyfikat X. 509 został wystawiony przez zaufany urząd certyfikacji. Jest to realizowane przez wyszukanie magazynu certyfikatów i określenie, czy certyfikat dla tego urzędu certyfikacji został wystawiony jako zaufany. Aby umożliwić programowi WCF przeznaczenie tego ustalenia, łańcuch certyfikatów urzędu certyfikacji musi być zainstalowany w prawidłowym magazynie certyfikatów.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Aby zainstalować łańcuch certyfikatów urzędu certyfikacji  
  
- Dla każdego urzędu certyfikacji, który odbiorca wiadomości protokołu SOAP ma ufać certyfikatom X. 509 wystawionym z, zainstaluj łańcuch certyfikatów urzędu certyfikacji w magazynie certyfikatów, który jest skonfigurowany do pobierania certyfikatów X. 509.  
  
     Na przykład jeśli odbiorca wiadomości protokołu SOAP zamierza ufać certyfikatom X. 509 wystawionym przez firmę Microsoft, łańcuch certyfikatów urzędu certyfikacji dla firmy Microsoft musi być zainstalowany w magazynie certyfikatów, który jest skonfigurowany przez funkcję WCF do wyszukiwania certyfikatów X. 509. Magazyn certyfikatów, w którym funkcja WCF szuka certyfikatów X. 509, można określić w kodzie lub konfiguracji. Na przykład można to określić w kodzie przy użyciu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody lub konfiguracji kilka sposobów, w tym [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Ponieważ system Windows jest dostarczany z zestawem domyślnych łańcuchów certyfikatów dla zaufanych urzędów certyfikacji, może nie być konieczne zainstalowanie łańcucha certyfikatów dla wszystkich urzędów certyfikacji.  
  
    1. Wyeksportuj łańcuch certyfikatów urzędu certyfikacji.  
  
         Dokładnie ten sposób zależy od urzędu certyfikacji. Jeśli urząd certyfikacji ma uruchomione usługi certyfikatów firmy Microsoft, wybierz pozycję **Pobierz certyfikat urzędu certyfikacji, łańcuch certyfikatów lub listę CRL**, a następnie wybierz pozycję **Pobierz certyfikat urzędu certyfikacji**.  
  
    2. Zaimportuj łańcuch certyfikatów urzędu certyfikacji.  
  
         W programie Microsoft Management Console (MMC) Otwórz przystawkę Certyfikaty. W przypadku magazynu certyfikatów, który usługa WCF jest skonfigurowana do pobierania certyfikatów X. 509 z, wybierz folder **Zaufane główne** urzędy **certyfikacji** . W folderze **Zaufane główne** urzędy certyfikacji kliknij prawym przyciskiem myszy **folder certyfikaty** , wskaż **wszystkie zadania**, a następnie kliknij przycisk **Importuj**. Podaj plik wyeksportowany w kroku a.  
  
         Aby uzyskać więcej informacji o korzystaniu z przystawki Certyfikaty w programie MMC, zobacz [How to: View Certificates with MMC](how-to-view-certificates-with-the-mmc-snap-in.md)przystawka.  
  
## <a name="see-also"></a>Zobacz też

- [Praca z certyfikatami](working-with-certificates.md)
