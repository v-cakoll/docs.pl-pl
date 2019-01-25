---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 303e5523befb68c65bc50ee3933af58897929363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668460"
---
# <a name="transportbindingelement"></a>TransportBindingElement
TransportBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementu TransportBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementu TransportBindingElement ma następujące właściwości:  
  
### <a name="manualaddressing"></a>opcję manualAddressing  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca, czy użytkownik chce, aby przejąć kontrolę nad adresowaniem komunikatów.  
  
### <a name="maxbufferpoolsize"></a>MaxBufferPoolSize  
 Typ danych: sint64  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny rozmiar puli buforów dla wiązania.  
  
### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize  
 Typ danych: sint64  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalny rozmiar komunikatu, który jest przetwarzany przez to wiązanie.  
  
### <a name="scheme"></a>Schemat  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Schemat identyfikatora URI dla transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Channels.TransportBindingElement>
