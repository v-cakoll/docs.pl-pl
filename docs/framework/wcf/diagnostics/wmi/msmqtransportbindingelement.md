---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963309"
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny rozmiar puli, która zawiera obiekty wewnętrzne wiadomości usługi MSMQ.  
  
### <a name="queuetransferprotocol"></a>QueueTransferProtocol  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość wyliczenia, która wskazuje kanał transportowy komunikacji z obsługą kolejek, który używa tego powiązania.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Zwraca wartość logiczną wskazującą, czy adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
