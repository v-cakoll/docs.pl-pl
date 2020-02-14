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
ms.openlocfilehash: 026697feec7afe950628639c5e595ba0a0220b97
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217143"
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
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
