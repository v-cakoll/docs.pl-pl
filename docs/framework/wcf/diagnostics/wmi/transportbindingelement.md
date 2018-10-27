---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182661"
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
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca, czy użytkownik chce, aby przejąć kontrolę nad adresowaniem komunikatów.  
  
### <a name="maxbufferpoolsize"></a>maxBufferPoolSize  
 Typ danych: sint64  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalny rozmiar puli buforów dla wiązania.  
  
### <a name="maxreceivedmessagesize"></a>maxReceivedMessageSize  
 Typ danych: sint64  
  
 Dostęp do typu: tylko do odczytu  
  
 Maksymalny rozmiar komunikatu, który jest przetwarzany przez to wiązanie.  
  
### <a name="scheme"></a>Schemat  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Schemat identyfikatora URI dla transportu.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.TransportBindingElement>
