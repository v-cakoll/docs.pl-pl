---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: 4522f1c59c8f74281a0e197338c6206ab29c229b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498647"
---
# <a name="operating-system-resources-required-by-wcf"></a>Zasoby systemu operacyjnego wymagane przez architekturę WCF
Windows Communication Foundation (WCF) zależy od wielu zasobów, które są dostarczane przez system operacyjny do funkcji. W poniższej tabeli wymieniono te zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|Microsoft Distributed Transaction Coordinator (MSDTC)|Wymagany do obsługi transakcji OleTx.|  
|Internet Information Services (IIS)|Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.|  
|Usługa aktywacji procesów systemu Windows (WAS)|Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania systemowe](../../../docs/framework/wcf/wcf-system-requirements.md)
