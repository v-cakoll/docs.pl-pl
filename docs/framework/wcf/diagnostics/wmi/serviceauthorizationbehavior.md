---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972839"
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
