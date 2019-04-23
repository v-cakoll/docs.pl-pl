---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 572e458f08c4717207667db9940296c4a957199a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59771778"
---
# <a name="servicethrottlingbehavior"></a>ServiceThrottlingBehavior
ServiceThrottlingBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa elementu ServiceThrottlingBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa elementu ServiceThrottlingBehavior ma następujące właściwości:  
  
### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba komunikatów aktywnie przetwarzania dla wszystkich obiektów dyspozytora w elemencie ServiceHost.  
  
### <a name="maxconcurrentinstances"></a>MaxConcurrentInstances  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba obiektów usługi, które mogą być wykonywane w tym samym czasie.  
  
### <a name="maxconcurrentsessions"></a>MaxConcurrentSessions  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Maksymalna liczba sesji na hoście może akceptować w tym samym czasie.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
