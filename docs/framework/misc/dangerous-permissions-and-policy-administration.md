---
title: Niebezpieczne uprawnienia i administrowanie zasadami
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 471570aec43398b05b8678bdcf74a3ef2494e289
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a>Niebezpieczne uprawnienia i administrowanie zasadami
Kilka działań chronionych, dla których programu .NET Framework zapewnia uprawnienia potencjalnie pozwolić na obejść przez system zabezpieczeń. Należy podać te niebezpieczne uprawnienia tylko do zaufanego kodu, a następnie tylko niezbędne. Brak zwykle nie funkcji chroniącej przed złośliwym kodem, w przypadku przyznania uprawnienia.  
  
> [!NOTE]
>  W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zostały ważne zmiany modelu zabezpieczeń .NET Framework i terminologię. Aby uzyskać więcej informacji na temat tych zmian, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).  
  
 Niebezpieczne uprawnienia opisano w poniższej tabeli.  
  
|Uprawnienie|Potencjalne zagrożenie|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umożliwia kodu zarządzanego do wywołania do kodu niezarządzanego, który często jest niebezpieczne.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez weryfikacji kod można wykonać żadnych czynności.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Nieważne dowód można oszukiwania zasady zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Uprawnienia do modyfikowania zasad zabezpieczeń można wyłączyć zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Użycie serializacji mogą omijać mechanizmów ułatwień dostępu. Aby uzyskać więcej informacji, zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Możliwość określenia bieżący podmiot zabezpieczeń można wymuszać na podstawie ról zabezpieczeń.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulowanie wątków jest niebezpieczne ze względu na stan zabezpieczeń skojarzone z wątków.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Można użyć prywatnych elementów członkowskich pokonanie mechanizmów ułatwień dostępu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
