---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 828d656370efd7638fa4cf367b84ee7b316b89bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61955223"
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
