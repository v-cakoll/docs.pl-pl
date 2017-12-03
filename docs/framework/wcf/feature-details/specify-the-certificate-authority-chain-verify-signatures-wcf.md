---
title: "Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6cba37a82174ab255cb6814e296154485fbdd54c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Instrukcje: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów (WCF)
Gdy [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] odbiera wiadomości SOAP podpisany za pomocą certyfikatu X.509, domyślnie sprawdza, czy certyfikat X.509 został wystawiony przez zaufany urząd certyfikacji. Jest to realizowane przez wyszukiwanie w magazynie certyfikatów i określenia, czy certyfikat dla tego urzędu certyfikacji został wyznaczony jako zaufany. Aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Aby określić to łańcucha certyfikatu urzędu certyfikacji musi być zainstalowany w magazynie prawidłowego certyfikatu.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Aby zainstalować łańcuch certyfikatów urzędu certyfikacji  
  
-   Dla każdego urzędu certyfikacji, który zamierza zaufania X.509 certyfikaty wystawiane przez adresata wiadomości SOAP, zainstaluj łańcucha certyfikatu urzędu certyfikacji do certyfikatu magazyn [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest skonfigurowany do pobierania certyfikatów X.509 z.  
  
     Na przykład, jeśli adresat wiadomości SOAP zamierza zaufania certyfikatów X.509 wystawionych przez firmę Microsoft, łańcucha certyfikatu urzędu certyfikacji dla firmy Microsoft musi być zainstalowany w certyfikacie magazyn [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest skonfigurowany do wyszukania certyfikatów X.509 z. Magazyn certyfikatów, w którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] szuka certyfikatów X.509 można określić w konfiguracji lub kodu. Na przykład można wybrać opcję za pomocą kodu <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody lub w konfiguracji na kilka sposobów, łącznie z [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Ponieważ system Windows jest dostarczany z zestawem domyślne łańcuchów certyfikatów dla zaufanych urzędów certyfikacji, nie można niezbędne do zainstalowania łańcucha certyfikatów dla wszystkich urzędów certyfikacji.  
  
    1.  Wyeksportuj łańcucha certyfikatu urzędu certyfikacji.  
  
         Dokładnie tak jak to jest wykonywane jest zależna od urzędu certyfikacji. Jeśli urząd certyfikacji działa usług certyfikatów firmy Microsoft, wybierz **Pobierz certyfikat urzędu certyfikacji, łańcuch certyfikatów lub listę CRL**, a następnie wybierz pozycję **Pobierz certyfikat urzędu certyfikacji**.  
  
    2.  Importuj łańcucha certyfikatu urzędu certyfikacji.  
  
         W programie Microsoft Management Console (MMC), otwórz przystawkę Certyfikaty. Certyfikatu przechowywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest skonfigurowany do pobierania certyfikatów X.509 z wybierz opcję **zaufanym głównym** **urzędów certyfikacji**folderu. W obszarze **zaufane główne urzędy certyfikacji** folderu, kliknij prawym przyciskiem myszy **certyfikaty**folderu, wskaż **wszystkie zadania**, a następnie kliknij przycisk **importu** . Określ plik wyeksportowany w kroku.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]za pomocą przystawki Certyfikaty w programie MMC, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
