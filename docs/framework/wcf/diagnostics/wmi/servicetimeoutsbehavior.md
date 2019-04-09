---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 58e872f2b15776d65bccdcc47c353ce566cd9d2f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116015"
---
# <a name="servicetimeoutsbehavior"></a>ServiceTimeoutsBehavior
ServiceTimeoutsBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceTimeoutsBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceTimeoutsBehavior ma następującą właściwość:  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Typ danych: Data i godzina  
  
 Typ dostępu: tylko do odczytu  
  
 Okres, w którym należy wykonać transakcję.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
