---
title: Niebezpieczne uprawnienia i administrowanie zasadami
description: Zobacz linki do różnych niebezpiecznych uprawnień w programie .NET. Te uprawnienia powinny mieć tylko kod godny zaufania i tylko wtedy, gdy jest to konieczne.
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
ms.openlocfilehash: ba3d47dc445e4b368f57d59d735fc331f5d6de81
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281618"
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="f53e4-104">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="f53e4-104">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="f53e4-105">Kilka operacji chronionych, dla których .NET Framework zapewnia uprawnienia, mogą potencjalnie pozwolić na obejście systemu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f53e4-105">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="f53e4-106">Te niebezpieczne uprawnienia powinny być przyznawane tylko do wiarygodnego kodu, a następnie tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="f53e4-106">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="f53e4-107">W przypadku przyznania tych uprawnień zwykle nie ma obrony przed złośliwym kodem.</span><span class="sxs-lookup"><span data-stu-id="f53e4-107">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f53e4-108">W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń .NET Framework i terminologii.</span><span class="sxs-lookup"><span data-stu-id="f53e4-108">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="f53e4-109">Aby uzyskać więcej informacji o tych zmianach, zobacz [zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="f53e4-109">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="f53e4-110">W poniższej tabeli objaśniono niebezpieczne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="f53e4-110">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="f53e4-111">Uprawnienie</span><span class="sxs-lookup"><span data-stu-id="f53e4-111">Permission</span></span>|<span data-ttu-id="f53e4-112">Potencjalne ryzyko</span><span class="sxs-lookup"><span data-stu-id="f53e4-112">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="f53e4-113">Umożliwia kodowi zarządzanemu Wywoływanie kodu niezarządzanego, który jest często niebezpieczny.</span><span class="sxs-lookup"><span data-stu-id="f53e4-113">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="f53e4-114">Bez weryfikacji kod może wykonać dowolne czynności.</span><span class="sxs-lookup"><span data-stu-id="f53e4-114">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="f53e4-115">Unieważnione dowody mogą mieć oszustwa zasady zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f53e4-115">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="f53e4-116">Możliwość modyfikowania zasad zabezpieczeń może wyłączyć zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="f53e4-116">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="f53e4-117">Użycie serializacji może obejść mechanizmy ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="f53e4-117">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="f53e4-118">Aby uzyskać szczegółowe informacje, zobacz [zabezpieczenia i Serializacja](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f53e4-118">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="f53e4-119">Możliwość ustawienia bieżącego podmiotu zabezpieczeń może wypróbować zabezpieczenia oparte na rolach.</span><span class="sxs-lookup"><span data-stu-id="f53e4-119">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="f53e4-120">Manipulowanie wątkami jest niebezpieczne ze względu na stan zabezpieczeń skojarzony z wątkami.</span><span class="sxs-lookup"><span data-stu-id="f53e4-120">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="f53e4-121">Może używać prywatnych elementów członkowskich do pokonania mechanizmów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="f53e4-121">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f53e4-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f53e4-122">See also</span></span>

- [<span data-ttu-id="f53e4-123">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="f53e4-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
