---
title: "Instrukcje: Spójne odwoływanie się do certyfikatów X.509"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d42af919b9792fc5a5303737187be7ffef6405d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Instrukcje: Spójne odwoływanie się do certyfikatów X.509
Można zidentyfikować certyfikatu na kilka sposobów: przez skrót certyfikatu, wystawcy i numer seryjny lub identyfikator klucza podmiotu (SKI). SKI zawiera unikatowy identyfikator dla klucz publiczny podmiotu certyfikatu i jest często używany podczas pracy z XML podpisu cyfrowego. Wartość SKI zwykle jest częścią certyfikatu X.509 jako *rozszerzenia certyfikatów X.509*. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]ma wartość domyślną *odwołuje się do stylu* które używa wystawcy i numer seryjny, jeśli rozszerzenie SKI brakuje certyfikatu. Jeśli certyfikat zawiera rozszerzenia SKI, domyślne odwołanie do stylu używa SKI do punktu z certyfikatem. Jeśli pośredniej sposób tworzenia aplikacji, można zmienić za pomocą certyfikatów, które nie korzystają z rozszerzenia SKI certyfikaty, które było używane rozszerzenie SKI, odwołujący się styl używany w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-wygenerowane wiadomości również zmiany.  
  
 Jeśli stylu odwołujący się spójne jest wymagany niezależnie od obecności rozszerzenia SKI, jest możliwe do skonfigurowania żądany styl odwołujący się, jak pokazano w poniższym kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy niestandardowe zabezpieczeń element powiązania, który używa pojedynczy styl odwołujący się zgodne, nazwa wystawcy i numer seryjny.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Następujących przestrzeni nazw są wymagane, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
