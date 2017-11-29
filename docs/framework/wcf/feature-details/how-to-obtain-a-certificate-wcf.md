---
title: 'Instrukcje: Uzyskiwanie certyfikatu (WCF)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 468298c7a0ea673a90e0cde9d481333fad60e4a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Instrukcje: Uzyskiwanie certyfikatu (WCF)
Aby użyć dowolnego z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcje, które korzystają z certyfikatów X.509, po prostu najpierw uzyskać certyfikaty.  
  
### <a name="to-obtain-an-x509-certificate"></a>Aby uzyskać certyfikat X.509  
  
1.  Wybierz jedną z następujących opcji:  
  
    -   Kup certyfikat od urzędu certyfikacji, takich jak VeriSign, Inc.  
  
    -   Skonfiguruj usługi certyfikatów i mieć podpisywania certyfikatów urzędu certyfikacji. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Systemu Windows Server 2000, Windows 2000 Server Datacenter i systemu Windows 2000 Server Datacenter uwzględnienia usług certyfikatów, które obsługują infrastruktury kluczy publicznych (PKI). W systemie Windows Server 2008, należy użyć [usługi certyfikatów Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) roli do zarządzania urzędem certyfikacji.  
  
    -   Skonfiguruj usługi certyfikatów i czy nie ma certyfikatów podpisany.  
  
    > [!NOTE]
    >  Sposób należy wykonać, odbiorca żądania SOAP, który zawiera certyfikat X.509 musi traktować jako zaufany certyfikat X.509. Oznacza to, że certyfikat X.509 lub wystawców w łańcuchu certyfikatów jest w magazynie certyfikatów zaufanych osób i że certyfikatu X.509 nie jest w magazynie certyfikatów niezaufanych.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Porady: Tworzenie certyfikatów tymczasowych do użytku w czasie projektowania](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
