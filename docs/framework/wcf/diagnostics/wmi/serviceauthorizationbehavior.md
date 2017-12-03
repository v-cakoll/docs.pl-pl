---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fd22cd7e7783a67e7ad10371533eee680bd3af16
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Składnia  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceAuthorizationBehavior ma następujące właściwości:  
  
### <a name="impersonatecallerforalloperations"></a>ImpersonateCallerForAllOperations  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Wartość, która kontroluje, czy usługa próbuje dokonać personifikacji, używając poświadczeń dostarczonych w komunikacie przychodzącym.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.  
  
### <a name="roleprovider"></a>Element RoleProvider  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa dostawcy ról ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>Obiekt ServiceAuthorizationManager  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Menedżer autoryzacji używany do przeprowadzania niestandardowej autoryzacji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
