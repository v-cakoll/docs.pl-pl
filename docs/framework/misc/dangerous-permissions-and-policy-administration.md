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
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="4c089-102">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="4c089-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="4c089-103">Kilka operacji chronionych, dla których .NET Framework zapewnia uprawnienia, mogą potencjalnie pozwolić na obejście systemu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4c089-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="4c089-104">Te niebezpieczne uprawnienia powinny być przyznawane tylko do wiarygodnego kodu, a następnie tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="4c089-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="4c089-105">W przypadku przyznania tych uprawnień zwykle nie ma obrony przed złośliwym kodem.</span><span class="sxs-lookup"><span data-stu-id="4c089-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c089-106">W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń .NET Framework i terminologii.</span><span class="sxs-lookup"><span data-stu-id="4c089-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="4c089-107">Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](../security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="4c089-107">For more information about these changes, see [Security Changes](../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="4c089-108">W poniższej tabeli objaśniono niebezpieczne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4c089-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="4c089-109">Uprawnienie</span><span class="sxs-lookup"><span data-stu-id="4c089-109">Permission</span></span>|<span data-ttu-id="4c089-110">Potencjalne ryzyko</span><span class="sxs-lookup"><span data-stu-id="4c089-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="4c089-111">Umożliwia kodowi zarządzanemu Wywoływanie kodu niezarządzanego, który jest często niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="4c089-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="4c089-112">Bez weryfikacji kod może wykonać dowolne czynności.</span><span class="sxs-lookup"><span data-stu-id="4c089-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="4c089-113">Unieważnione dowody mogą mieć oszustwa zasady zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="4c089-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="4c089-114">Możliwość modyfikowania zasad zabezpieczeń może wyłączyć zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="4c089-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="4c089-115">Użycie serializacji może obejść mechanizmy ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c089-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="4c089-116">Aby uzyskać szczegółowe informacje, zobacz [zabezpieczenia i Serializacja](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="4c089-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="4c089-117">Możliwość ustawienia bieżącego podmiotu zabezpieczeń może wypróbować zabezpieczenia oparte na rolach.</span><span class="sxs-lookup"><span data-stu-id="4c089-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="4c089-118">Manipulowanie wątkami jest niebezpieczne ze względu na stan zabezpieczeń skojarzony z wątkami.</span><span class="sxs-lookup"><span data-stu-id="4c089-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="4c089-119">Może używać prywatnych elementów członkowskich do pokonania mechanizmów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="4c089-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c089-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c089-120">See also</span></span>

- [<span data-ttu-id="4c089-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="4c089-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
