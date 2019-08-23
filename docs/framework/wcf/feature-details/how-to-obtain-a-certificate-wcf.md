---
title: 'Instrukcje: Uzyskaj certyfikat (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929189"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Instrukcje: Uzyskaj certyfikat (WCF)
Aby używać dowolnych funkcji programu Windows Communication Foundation (WCF), które używają certyfikatów X. 509, wystarczy najpierw uzyskać certyfikaty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Aby uzyskać certyfikat X. 509  
  
1. Wybierz jedną z następujących opcji:  
  
    - Kup certyfikat od urzędu certyfikacji, na przykład VeriSign, Inc.  
  
    - Skonfiguruj własną usługę certyfikatów i przygotuj certyfikaty przy użyciu urzędu certyfikacji. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter i Windows 2000 Datacenter Server wszystkie obejmują usługi certyfikatów, które obsługują infrastrukturę kluczy publicznych (PKI). W systemie Windows Server 2008 Użyj roli [usługi certyfikatów Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) do zarządzania urzędem certyfikacji.  
  
    - Skonfiguruj własną usługę certyfikatów i nie masz podpisanych certyfikatów.  
  
    > [!NOTE]
    > Niezależnie od tego, jakie podejście zostanie wykonane, odbiorca żądania protokołu SOAP, który zawiera certyfikat X. 509, musi ufać certyfikatowi X. 509. Oznacza to, że certyfikat X. 509 lub wystawca w łańcuchu certyfikatów znajduje się w magazynie certyfikatów osoby zaufane i certyfikat X. 509 nie znajduje się w magazynie certyfikatów niezaufanych.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: Tworzenie certyfikatów tymczasowych do użycia podczas opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
