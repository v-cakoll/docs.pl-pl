---
title: 'Instrukcje: Stale odwołanie certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: 2468faabfbca57e7d905a592b6743c43cb2ccd56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731975"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Instrukcje: Stale odwołanie certyfikatu X.509
Można zidentyfikować certyfikatu na kilka sposobów: przez skrót certyfikatu, przez wystawcę i numer seryjny lub przez identyfikator klucza podmiotu (NARCIARSKIE). NARCIARSKIE zawiera unikatowy identyfikator dla klucz publiczny podmiotu certyfikatu i jest często używana podczas pracy z XML cyfrowego podpisywania. Wartość NARCIARSKIE jest zazwyczaj część certyfikatu X.509 jako *rozszerzenia certyfikatów X.509*. Windows Communication Foundation (WCF) ma wartość domyślną *odwołanie do stylu* , jeżeli wystawcy i numer seryjny rozszerzenia NARCIARSKIE brakuje certyfikatu. Jeśli certyfikat zawiera rozszerzenie NARCIARSKIE, domyślne odwołanie do stylu używa NARCIARSKIE wskaż certyfikat. Środku sposób przez proces tworzenia aplikacji, możesz przejść z korzystania z certyfikatów, które nie korzystają z rozszerzenia NARCIARSKIE certyfikaty, które mają rozszerzenie NARCIARSKIE, zmienia także odwołujący się styl używany w wiadomościach generowanych przez usługi WCF.  
  
 Jeśli jednolitego stylu odwołujący się jest wymagany niezależnie od obecności rozszerzenia NARCIARSKIE, jest możliwość skonfigurowania żądany styl odwołujący się, jak pokazano w poniższym kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy niestandardowe zabezpieczeń element powiązania, który używa pojedynczego jednolitego stylu odwołujący się, nazwy wystawcy i numer seryjny.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Następujące przestrzenie nazw są wymagane, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Zobacz także
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
