---
title: "Zasoby systemu operacyjnego wymagane przez architekturę WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6cfe114e5e044a6aaa1e356194a46b4a46011aa0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operating-system-resources-required-by-wcf"></a>Zasoby systemu operacyjnego wymagane przez architekturę WCF
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]zależy od wielu zasobów, które są dostarczane przez system operacyjny do funkcji. W poniższej tabeli wymieniono te zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|Microsoft Distributed Transaction Coordinator (MSDTC)|Wymagany do obsługi transakcji OleTx.|  
|Internet Information Services (IIS)|Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.|  
|Usługa aktywacji procesów systemu Windows (WAS)|Wymagane, jeśli chcesz użyć WAS do hostowania aplikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wymagania systemowe](../../../docs/framework/wcf/wcf-system-requirements.md)
