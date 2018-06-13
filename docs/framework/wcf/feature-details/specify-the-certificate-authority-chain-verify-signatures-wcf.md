---
title: 'Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 14f7691046f9512e25006bd6cd02749eed825003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498078"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)
Windows Communication Foundation (WCF) odebrania wiadomości SOAP podpisany przy użyciu certyfikatu X.509, domyślnie sprawdza czy certyfikatu X.509 został wystawiony przez zaufany urząd certyfikacji. Jest to realizowane przez wyszukiwanie w magazynie certyfikatów i określenia, czy certyfikat dla tego urzędu certyfikacji został wyznaczony jako zaufany. Aby dla usługi WCF określić to łańcucha certyfikatu urzędu certyfikacji musi być zainstalowany w magazynie prawidłowego certyfikatu.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Aby zainstalować łańcuch certyfikatów urzędu certyfikacji  
  
-   Dla każdego urzędu certyfikacji, które odbiorca wiadomości SOAP zamierza zaufania certyfikatów X.509 wystawionych przez, zainstaluj łańcucha certyfikatu urzędu certyfikacji do magazynu certyfikatów, czy WCF jest skonfigurowany do pobierania certyfikatów X.509 z.  
  
     Na przykład adresat wiadomości SOAP zamierza zaufania certyfikatów X.509 wystawionych przez firmę Microsoft, musi być zainstalowany w magazynie certyfikatów ustawionej WCF do wyszukania certyfikatów X.509 z łańcucha certyfikatu urzędu certyfikacji firmy Microsoft. W konfiguracji lub kodu można określić magazyn certyfikatów, w którym WCF wyszukuje certyfikatów X.509. Na przykład można wybrać opcję za pomocą kodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody lub w konfiguracji na kilka sposobów, łącznie z [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Ponieważ system Windows jest dostarczany z zestawem domyślne łańcuchów certyfikatów dla zaufanych urzędów certyfikacji, nie można niezbędne do zainstalowania łańcucha certyfikatów dla wszystkich urzędów certyfikacji.  
  
    1.  Wyeksportuj łańcucha certyfikatu urzędu certyfikacji.  
  
         Dokładnie tak jak to jest wykonywane jest zależna od urzędu certyfikacji. Jeśli urząd certyfikacji działa usług certyfikatów firmy Microsoft, wybierz **Pobierz certyfikat urzędu certyfikacji, łańcuch certyfikatów lub listę CRL**, a następnie wybierz pozycję **Pobierz certyfikat urzędu certyfikacji**.  
  
    2.  Importuj łańcucha certyfikatu urzędu certyfikacji.  
  
         W programie Microsoft Management Console (MMC), otwórz przystawkę Certyfikaty. Do magazynu certyfikatów tego WCF jest skonfigurowany do pobierania certyfikatów X.509 z wybierz opcję **zaufanym głównym** **urzędów certyfikacji**folderu. W obszarze **zaufane główne urzędy certyfikacji** folderu, kliknij prawym przyciskiem myszy **certyfikaty**folderu, wskaż **wszystkie zadania**, a następnie kliknij przycisk **importu** . Określ plik wyeksportowany w kroku.  
  
         Aby uzyskać więcej informacji o korzystaniu z przystawki Certyfikaty w programie MMC, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
