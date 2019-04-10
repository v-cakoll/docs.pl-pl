---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203512"
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
  
 Typ dostępu: tylko do odczytu  
  
 Lokalizacja dziennika inspekcji.  
  
### <a name="messageauthenticationauditlevel"></a>MessageAuthenticationAuditLevel  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Typ poziom uwierzytelniania wiadomości, która jest używana do rejestrowania zdarzeń inspekcji.  
  
### <a name="serviceauthorizationauditlevel"></a>ServiceAuthorizationAuditLevel  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.  
  
### <a name="suppressauditfailure"></a>suppressAuditFailure  
 Typ danych: wartość logiczna  
  
 Typ dostępu: tylko do odczytu  
  
 Wartość logiczna określająca zachowanie w sytuacji pominięcia błędów zapisu do dziennika inspekcji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
