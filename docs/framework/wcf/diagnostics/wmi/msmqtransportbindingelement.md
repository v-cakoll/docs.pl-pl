---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 572a19723583a6bc717a71b3b46040148f29e1cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementem MsmqTransportBindingElement ma następujące właściwości:  
  
### <a name="maxpoolsize"></a>maxPoolSize  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny rozmiar puli zawierającej wewnętrzne obiekty komunikatów MSMQ.  
  
### <a name="queuetransferprotocol"></a>Właściwość queueTransferProtocol  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość wyliczenia wskazująca kolejkowany kanał komunikacyjny transportu przez to wiązanie.  
  
### <a name="useactivedirectory"></a>Właściwość UseActiveDirectory  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Zwraca wartość logiczną, wskazującą, czy adresy kolejek powinny być konwertowane przy użyciu usługi Active Directory.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
