---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 759ab099066e300484860cf3f91d6d084ba1d339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527084"
---
# <a name="operating-system-resources-required-by-wcf"></a>Zasoby systemu operacyjnego wymagane przez architekturę WCF
Windows Communication Foundation (WCF) jest zależna od kilka zasobów, które są dostarczane przez system operacyjny do funkcji. W poniższej tabeli wymieniono te zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|Microsoft Distributed Transaction Coordinator (MSDTC)|Wymagany do obsługi transakcji OleTx.|  
|Internet Information Services (IIS)|Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.|  
|Usługa aktywacji procesów systemu Windows (WAS)|Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.|  
  
## <a name="see-also"></a>Zobacz także
- [Wymagania systemowe](../../../docs/framework/wcf/wcf-system-requirements.md)
