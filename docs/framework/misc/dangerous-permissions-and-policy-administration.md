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
ms.openlocfilehash: ae24cdcb97e30da0bd4aec6569ef3dcda11488c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775768"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Niebezpieczne uprawnienia i administrowanie zasadami
Niektóre operacje chronionych, dla których program .NET Framework oferuje uprawnienia jest potencjalnie pozwolić system zabezpieczeń obejść. Niebezpieczne uprawnienia należy podać tylko zaufanego kodu, a następnie tylko gdy jest to konieczne. Istnieje zazwyczaj nie chroniącej przed złośliwym kodem, w przypadku przyznania uprawnienia.  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], miały miejsce istotne zmiany w modelu zabezpieczeń .NET Framework i terminologię. Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Niebezpieczne uprawnienia są opisane w poniższej tabeli.  
  
|Uprawnienie|Potencjalne ryzyko|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umożliwia kodowi zarządzanemu wywoływania kod niezarządzany, który często jest niebezpieczne.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez weryfikacji kod można zrobić wszystko.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Dowód unieważniany można oszukania zasady zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Możliwość modyfikowania zasad zabezpieczeń, można wyłączyć zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Korzystanie z serializacji mogą omijać mechanizmów ułatwień dostępu. Aby uzyskać więcej informacji, zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Możliwość ustawiania bieżący podmiot zabezpieczeń może wymuszać opartej na rolach zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulowanie wątków jest niebezpieczne ze względu na stan zabezpieczeń skojarzone z wątków.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Można użyć prywatnych elementów członkowskich do pokonania mechanizmów ułatwień dostępu.|  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
