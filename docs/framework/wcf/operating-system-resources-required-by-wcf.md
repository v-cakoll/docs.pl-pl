---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: ac9bd5ed7c2092720c6521d0f78185c3fbf9f94b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318946"
---
# <a name="operating-system-resources-required-by-wcf"></a>Zasoby systemu operacyjnego wymagane przez architekturę WCF
Windows Communication Foundation (WCF) zależy od kilku zasobów dostarczonych przez system operacyjny do działania. W poniższej tabeli wymieniono te zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|Microsoft Distributed Transaction Coordinator (MSDTC)|Wymagane do obsługi transakcji OleTx.|  
|Internet Information Services (IIS)|Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.|  
|Usługa aktywacji procesów systemu Windows (WAS)|Wymagane, jeśli chcesz używać aplikacji.|  
  
## <a name="see-also"></a>Zobacz także

- [Wymagania systemowe](wcf-system-requirements.md)
