---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 062b45eb5d627903142ca1a5fd4db6df0855384b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasy TransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasy TransportBindingElement ma następujące właściwości:  
  
### <a name="manualaddressing"></a>Opcję ManualAddressing  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy użytkownik chce przejąć kontrolę nad adresowaniem komunikatów.  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  
 Typ danych: sint64  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny rozmiar puli buforów powiązania.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Typ danych: sint64  
  
 Dostęp typu: tylko do odczytu  
  
 Maksymalny rozmiar komunikatu przetwarzanego przez to powiązanie.  
  
### <a name="scheme"></a>Schemat  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Schemat identyfikatora URI dla transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
