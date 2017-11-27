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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb02a02557a88bf53ca1a8e5b30fe66d6995e545
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
