---
title: 'Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 9e2ba9f3550442602cab217fec329e6c19efd3b3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080828"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)
Gdy Windows Communication Foundation (WCF) odbiera wiadomości SOAP podpisany przy użyciu certyfikatu X.509, domyślnie ją sprawdza, czy certyfikat X.509 został wystawiony przez zaufany urząd certyfikacji. Odbywa się przez wyszukiwanie w magazynie certyfikatów i określenia, jeśli certyfikat dla tego urzędu certyfikacji został wyznaczony jako zaufane. Aby WCF określić to łańcuch certyfikatów urzędu certyfikacji musi być zainstalowany w magazynie certyfikatów poprawny.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Aby zainstalować łańcuch certyfikatów urzędu certyfikacji  
  
-   Dla każdego urzędu certyfikacji, że odbiorca wiadomości SOAP zamierza zaufania certyfikatów X.509 wystawionych, zainstaluj łańcuch certyfikatów urzędu certyfikacji do magazynu certyfikatów, czy WCF jest skonfigurowany do pobierania certyfikatu x.509 z.  
  
     Na przykład jeśli adresat wiadomości SOAP zamierza zaufania certyfikatów X.509 wystawionych przez firmę Microsoft, łańcuch certyfikatów urzędu certyfikacji firmy Microsoft należy zainstalować w magazynie certyfikatów ustawionej WCF do wyszukania certyfikatów X.509 z. Magazyn certyfikatów, w którym WCF wyszukuje certyfikatów X.509 można określić w kodzie lub konfiguracji. Na przykład, można wybrać w kodzie za pomocą <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody lub w konfiguracji na kilka sposobów, w tym [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Ponieważ Windows jest dostarczany z zestawem domyślne łańcuchów certyfikatu dla zaufanych urzędów certyfikacji, nie może być konieczne zainstalowanie wszystkich urzędów certyfikacji w łańcuchu certyfikatów.  
  
    1.  Wyeksportuj łańcuch certyfikatów urzędu certyfikacji.  
  
         Dokładnie tak jak to zrobić zależy od urzędu certyfikacji. Jeśli urząd certyfikacji działa usług certyfikatów firmy Microsoft, wybierz opcję **Pobierz certyfikat urzędu certyfikacji, łańcuch certyfikatów lub listę CRL**, a następnie wybierz **Pobierz certyfikat urzędu certyfikacji**.  
  
    2.  Importować łańcuch certyfikatów urzędu certyfikacji.  
  
         W programie Microsoft Management Console (MMC), otwórz przystawkę Certyfikaty. Magazynu certyfikatów tej usługi WCF jest skonfigurowany do pobierania certyfikatu x.509 z wybierz opcję **zaufanego certyfikatu głównego** **urzędów certyfikacji** folderu. W obszarze **zaufane główne urzędy certyfikacji** folderu, kliknij prawym przyciskiem myszy **certyfikaty** folderu, wskaż **wszystkie zadania**, a następnie kliknij przycisk **importu** . Określ plik wyeksportowany w kroku.  
  
         Aby uzyskać więcej informacji o użyciu przystawki Certyfikaty programu MMC, zobacz [porady: wyświetlanie certyfikatów za pomocą przystawki programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
