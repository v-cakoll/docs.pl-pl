---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 485741f98c4a120669eafe85d3a3810374f61378
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347143"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Instrukcje: Uzyskiwanie certyfikatu (WCF)
Aby używać dowolnych funkcji programu Windows Communication Foundation (WCF), które używają certyfikatów X. 509, wystarczy najpierw uzyskać certyfikaty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Aby uzyskać certyfikat X. 509  
  
1. Wybierz jedną z następujących opcji:  
  
    - Kup certyfikat od urzędu certyfikacji, na przykład VeriSign, Inc.  
  
    - Skonfiguruj własną usługę certyfikatów i przygotuj certyfikaty przy użyciu urzędu certyfikacji. Wszystkie systemy Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter i Windows 2000 Datacenter Server obejmują usługi certyfikatów obsługujące infrastrukturę kluczy publicznych (PKI). W systemie Windows Server 2008 Użyj roli [usługi certyfikatów Active Directory](https://go.microsoft.com/fwlink/?LinkID=153483) do zarządzania urzędem certyfikacji.  
  
    - Skonfiguruj własną usługę certyfikatów i nie masz podpisanych certyfikatów.  
  
    > [!NOTE]
    > Niezależnie od tego, jakie podejście zostanie wykonane, odbiorca żądania protokołu SOAP, który zawiera certyfikat X. 509, musi ufać certyfikatowi X. 509. Oznacza to, że certyfikat X. 509 lub wystawca w łańcuchu certyfikatów znajduje się w magazynie certyfikatów osoby zaufane i certyfikat X. 509 nie znajduje się w magazynie certyfikatów niezaufanych.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
