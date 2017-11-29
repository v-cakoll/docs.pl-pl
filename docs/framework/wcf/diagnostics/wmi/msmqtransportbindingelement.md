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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c0c2c5d54050216c91a318a407341c4ffb9cb687
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
