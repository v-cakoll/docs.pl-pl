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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645757"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Niebezpieczne uprawnienia i administrowanie zasadami
Kilka chronionych operacji, dla których .NET Framework zapewnia uprawnienia może potencjalnie umożliwić obejście systemu zabezpieczeń. Te niebezpieczne uprawnienia powinny być podane tylko do kodu godnego zaufania, a następnie tylko w razie potrzeby. Zazwyczaj nie ma żadnej ochrony przed złośliwym kodem, jeśli zostanie on przyznany te uprawnienia.  
  
> [!NOTE]
> W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń i terminologii programu .NET Framework. Aby uzyskać więcej informacji na temat tych zmian, zobacz [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Niebezpieczne uprawnienia są wyjaśnione w poniższej tabeli.  
  
|Uprawnienie|Potencjalne ryzyko|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umożliwia kod zarządzany do wywołania do kodu niezarządzanego, co jest często niebezpieczne.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez weryfikacji kod może zrobić wszystko.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Unieważnione dowody mogą oszukać zasady bezpieczeństwa.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Możliwość modyfikowania zasad zabezpieczeń może wyłączyć zabezpieczenia.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Użycie serializacji można obejść mechanizmy ułatwień dostępu. Aby uzyskać szczegółowe informacje, zobacz [Zabezpieczenia i serializacja](security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Możliwość ustawienia bieżącego podmiotu zabezpieczeń może oszukać zabezpieczenia oparte na rolach.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulowanie wątkami jest niebezpieczne ze względu na stan zabezpieczeń skojarzony z wątkami.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Można użyć prywatnych członków, aby pokonać mechanizmy ułatwień dostępu.|  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
