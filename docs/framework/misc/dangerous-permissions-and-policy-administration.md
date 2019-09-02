---
title: Niebezpieczne uprawnienia i administrowanie zasadami
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffe4f3e000c80610d5a105dddef90f9cfd51f0dc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205586"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Niebezpieczne uprawnienia i administrowanie zasadami
Kilka operacji chronionych, dla których .NET Framework zapewnia uprawnienia, mogą potencjalnie pozwolić na obejście systemu zabezpieczeń. Te niebezpieczne uprawnienia powinny być przyznawane tylko do wiarygodnego kodu, a następnie tylko w razie potrzeby. W przypadku przyznania tych uprawnień zwykle nie ma obrony przed złośliwym kodem.  
  
> [!NOTE]
> W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń .NET Framework i terminologii. Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](../security/security-changes.md).  
  
 W poniższej tabeli objaśniono niebezpieczne uprawnienia.  
  
|Uprawnienie|Potencjalne ryzyko|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umożliwia kodowi zarządzanemu Wywoływanie kodu niezarządzanego, który jest często niebezpieczny.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez weryfikacji kod może wykonać dowolne czynności.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Unieważnione dowody mogą mieć oszustwa zasady zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Możliwość modyfikowania zasad zabezpieczeń może wyłączyć zabezpieczenia.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Użycie serializacji może obejść mechanizmy ułatwień dostępu. Aby uzyskać szczegółowe informacje, zobacz [zabezpieczenia i Serializacja](security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Możliwość ustawienia bieżącego podmiotu zabezpieczeń może wypróbować zabezpieczenia oparte na rolach.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulowanie wątkami jest niebezpieczne ze względu na stan zabezpieczeń skojarzony z wątkami.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Może używać prywatnych elementów członkowskich do pokonania mechanizmów ułatwień dostępu.|  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
