---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045991"
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
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalny rozmiar puli, która zawiera obiekty wewnętrzne wiadomości usługi MSMQ.  
  
### <a name="queuetransferprotocol"></a>Właściwość queueTransferProtocol  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość wyliczenia, która wskazuje kanał transportowy komunikacji z obsługą kolejek, który używa tego powiązania.  
  
### <a name="useactivedirectory"></a>UseActiveDirectory  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Zwraca wartość logiczną wskazującą, czy adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>
