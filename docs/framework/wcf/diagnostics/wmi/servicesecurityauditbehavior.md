---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: e8b24877c2d76a3f2f90c27ae83374c7bca1328b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181163"
---
# <a name="servicesecurityauditbehavior"></a>ServiceSecurityAuditBehavior
ServiceSecurityAuditBehavior  
  
## <a name="syntax"></a>Składnia  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceSecurityAuditBehavior nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceSecurityAuditBehavior ma następujące właściwości:  
  
### <a name="auditloglocation"></a>auditLogLocation  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Lokalizacja dziennika inspekcji.  
  
### <a name="messageauthenticationauditlevel"></a>messageAuthenticationAuditLevel  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Typ poziom uwierzytelniania wiadomości, która jest używana do rejestrowania zdarzeń inspekcji.  
  
### <a name="serviceauthorizationauditlevel"></a>serviceAuthorizationAuditLevel  
 Typ danych: ciąg  
  
 Dostęp do typu: tylko do odczytu  
  
 Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.  
  
### <a name="suppressauditfailure"></a>suppressAuditFailure  
 Typ danych: wartość logiczna  
  
 Dostęp do typu: tylko do odczytu  
  
 Wartość logiczna określająca zachowanie w sytuacji pominięcia błędów zapisu do dziennika inspekcji.  
  
## <a name="requirements"></a>Wymagania  
  
|PLIK MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
