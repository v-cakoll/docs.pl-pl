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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078945"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="0da31-102">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="0da31-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="0da31-103">Niektóre operacje chronionych, dla których program .NET Framework oferuje uprawnienia jest potencjalnie pozwolić system zabezpieczeń obejść.</span><span class="sxs-lookup"><span data-stu-id="0da31-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="0da31-104">Niebezpieczne uprawnienia należy podać tylko zaufanego kodu, a następnie tylko gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="0da31-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="0da31-105">Istnieje zazwyczaj nie chroniącej przed złośliwym kodem, w przypadku przyznania uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="0da31-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0da31-106">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], miały miejsce istotne zmiany w modelu zabezpieczeń .NET Framework i terminologię.</span><span class="sxs-lookup"><span data-stu-id="0da31-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="0da31-107">Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="0da31-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="0da31-108">Niebezpieczne uprawnienia są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0da31-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="0da31-109">Uprawnienie</span><span class="sxs-lookup"><span data-stu-id="0da31-109">Permission</span></span>|<span data-ttu-id="0da31-110">Potencjalne ryzyko</span><span class="sxs-lookup"><span data-stu-id="0da31-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="0da31-111">Umożliwia kodowi zarządzanemu wywoływania kod niezarządzany, który często jest niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="0da31-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="0da31-112">Bez weryfikacji kod można zrobić wszystko.</span><span class="sxs-lookup"><span data-stu-id="0da31-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="0da31-113">Dowód unieważniany można oszukania zasady zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0da31-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="0da31-114">Możliwość modyfikowania zasad zabezpieczeń, można wyłączyć zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0da31-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="0da31-115">Korzystanie z serializacji mogą omijać mechanizmów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0da31-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="0da31-116">Aby uzyskać więcej informacji, zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="0da31-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="0da31-117">Możliwość ustawiania bieżący podmiot zabezpieczeń może wymuszać opartej na rolach zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0da31-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="0da31-118">Manipulowanie wątków jest niebezpieczne ze względu na stan zabezpieczeń skojarzone z wątków.</span><span class="sxs-lookup"><span data-stu-id="0da31-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="0da31-119">Można użyć prywatnych elementów członkowskich do pokonania mechanizmów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="0da31-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0da31-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0da31-120">See also</span></span>

- [<span data-ttu-id="0da31-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="0da31-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
