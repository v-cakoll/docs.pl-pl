---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: bfe6dcfe6850ee17a7bbb59f3a6ccad6c3c3e7d7
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964240"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Instrukcje: Uzyskiwanie certyfikatu (WCF)
Aby używać dowolnych funkcji programu Windows Communication Foundation (WCF), które używają certyfikatów X. 509, wystarczy najpierw uzyskać certyfikaty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Aby uzyskać certyfikat X. 509  
  
1. Wybierz jedną z następujących opcji:  
  
    - Kup certyfikat od urzędu certyfikacji, na przykład VeriSign, Inc.  
  
    - Skonfiguruj własną usługę certyfikatów i przygotuj certyfikaty przy użyciu urzędu certyfikacji. Wszystkie systemy Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter i Windows 2000 Datacenter Server obejmują usługi certyfikatów obsługujące infrastrukturę kluczy publicznych (PKI). W systemie Windows Server 2008 Użyj roli [usługi certyfikatów Active Directory](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) do zarządzania urzędem certyfikacji.  
  
    - Skonfiguruj własną usługę certyfikatów i nie masz podpisanych certyfikatów.  
  
    > [!NOTE]
    > Niezależnie od tego, jakie podejście zostanie wykonane, odbiorca żądania protokołu SOAP, który zawiera certyfikat X. 509, musi ufać certyfikatowi X. 509. Oznacza to, że certyfikat X. 509 lub wystawca w łańcuchu certyfikatów znajduje się w magazynie certyfikatów osoby zaufane i certyfikat X. 509 nie znajduje się w magazynie certyfikatów niezaufanych.  
  
## <a name="see-also"></a>Zobacz także

- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Instrukcje: tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
