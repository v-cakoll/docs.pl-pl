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
ms.openlocfilehash: 0c8a01cbae2077838a8eef3f2f673e7d9d646717
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="9b927-102">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="9b927-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="9b927-103">Kilka działań chronionych, dla których programu .NET Framework zapewnia uprawnienia potencjalnie pozwolić na obejść przez system zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9b927-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="9b927-104">Należy podać te niebezpieczne uprawnienia tylko do zaufanego kodu, a następnie tylko niezbędne.</span><span class="sxs-lookup"><span data-stu-id="9b927-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="9b927-105">Brak zwykle nie funkcji chroniącej przed złośliwym kodem, w przypadku przyznania uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9b927-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b927-106">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], zostały ważne zmiany modelu zabezpieczeń .NET Framework i terminologię.</span><span class="sxs-lookup"><span data-stu-id="9b927-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="9b927-107">Aby uzyskać więcej informacji na temat tych zmian, zobacz [zmiany zabezpieczeń](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="9b927-107">For more information about these changes, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="9b927-108">Niebezpieczne uprawnienia opisano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9b927-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="9b927-109">Uprawnienie</span><span class="sxs-lookup"><span data-stu-id="9b927-109">Permission</span></span>|<span data-ttu-id="9b927-110">Potencjalne zagrożenie</span><span class="sxs-lookup"><span data-stu-id="9b927-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="9b927-111">Umożliwia kodu zarządzanego do wywołania do kodu niezarządzanego, który często jest niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="9b927-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="9b927-112">Bez weryfikacji kod można wykonać żadnych czynności.</span><span class="sxs-lookup"><span data-stu-id="9b927-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="9b927-113">Nieważne dowód można oszukiwania zasady zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9b927-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="9b927-114">Uprawnienia do modyfikowania zasad zabezpieczeń można wyłączyć zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9b927-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="9b927-115">Użycie serializacji mogą omijać mechanizmów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="9b927-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="9b927-116">Aby uzyskać więcej informacji, zobacz [zabezpieczenia i serializacja](../../../docs/framework/misc/security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="9b927-116">For details, see [Security and Serialization](../../../docs/framework/misc/security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="9b927-117">Możliwość określenia bieżący podmiot zabezpieczeń można wymuszać na podstawie ról zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="9b927-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="9b927-118">Manipulowanie wątków jest niebezpieczne ze względu na stan zabezpieczeń skojarzone z wątków.</span><span class="sxs-lookup"><span data-stu-id="9b927-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="9b927-119">Można użyć prywatnych elementów członkowskich pokonanie mechanizmów ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="9b927-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b927-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b927-120">See Also</span></span>  
 [<span data-ttu-id="9b927-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="9b927-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
