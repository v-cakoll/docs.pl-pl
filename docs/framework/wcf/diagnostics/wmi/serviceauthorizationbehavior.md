---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 58eb2a9fd9017aaf9966644180936f5871e086d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613899"
---
# <a name="serviceauthorizationbehavior"></a>ServiceAuthorizationBehavior
ServiceAuthorizationBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Typ dostępu: tylko do odczytu  
  
 Wartość, która kontroluje, czy usługa próbuje personifikować przy użyciu poświadczeń dostarczonych przez wiadomości przychodzącej.  
  
### <a name="principalpermissionmode"></a>PrincipalPermissionMode  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.  
  
### <a name="roleprovider"></a>RoleProvider  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa dostawcy ról ASP.NET.  
  
### <a name="serviceauthorizationmanager"></a>ServiceAuthorizationManager  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Menedżer autoryzacji używanych na potrzeby autoryzacji niestandardowej.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
