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
# <a name="dangerous-permissions-and-policy-administration"></a><span data-ttu-id="373d1-102">Niebezpieczne uprawnienia i administrowanie zasadami</span><span class="sxs-lookup"><span data-stu-id="373d1-102">Dangerous Permissions and Policy Administration</span></span>
<span data-ttu-id="373d1-103">Kilka chronionych operacji, dla których .NET Framework zapewnia uprawnienia może potencjalnie umożliwić obejście systemu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="373d1-103">Several of the protected operations for which the .NET Framework provides permissions can potentially allow the security system to be circumvented.</span></span> <span data-ttu-id="373d1-104">Te niebezpieczne uprawnienia powinny być podane tylko do kodu godnego zaufania, a następnie tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="373d1-104">These dangerous permissions should be given only to trustworthy code, and then only as necessary.</span></span> <span data-ttu-id="373d1-105">Zazwyczaj nie ma żadnej ochrony przed złośliwym kodem, jeśli zostanie on przyznany te uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="373d1-105">There is usually no defense against malicious code if it is granted these permissions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="373d1-106">W .NET Framework 4 wprowadzono ważne zmiany w modelu zabezpieczeń i terminologii programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="373d1-106">In the .NET Framework 4, there have been important changes to the .NET Framework security model and terminology.</span></span> <span data-ttu-id="373d1-107">Aby uzyskać więcej informacji na temat tych zmian, zobacz [Zmiany zabezpieczeń](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span><span class="sxs-lookup"><span data-stu-id="373d1-107">For more information about these changes, see [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="373d1-108">Niebezpieczne uprawnienia są wyjaśnione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="373d1-108">The dangerous permissions are explained in the following table.</span></span>  
  
|<span data-ttu-id="373d1-109">Uprawnienie</span><span class="sxs-lookup"><span data-stu-id="373d1-109">Permission</span></span>|<span data-ttu-id="373d1-110">Potencjalne ryzyko</span><span class="sxs-lookup"><span data-stu-id="373d1-110">Potential risk</span></span>|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|<span data-ttu-id="373d1-111">Umożliwia kod zarządzany do wywołania do kodu niezarządzanego, co jest często niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="373d1-111">Allows managed code to call into unmanaged code, which is often dangerous.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|<span data-ttu-id="373d1-112">Bez weryfikacji kod może zrobić wszystko.</span><span class="sxs-lookup"><span data-stu-id="373d1-112">Without verification, the code can do anything.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|<span data-ttu-id="373d1-113">Unieważnione dowody mogą oszukać zasady bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="373d1-113">Invalidated evidence can fool security policy.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|<span data-ttu-id="373d1-114">Możliwość modyfikowania zasad zabezpieczeń może wyłączyć zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="373d1-114">The ability to modify security policy can disable security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|<span data-ttu-id="373d1-115">Użycie serializacji można obejść mechanizmy ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="373d1-115">The use of serialization can circumvent accessibility mechanisms.</span></span> <span data-ttu-id="373d1-116">Aby uzyskać szczegółowe informacje, zobacz [Zabezpieczenia i serializacja](security-and-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="373d1-116">For details, see [Security and Serialization](security-and-serialization.md).</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|<span data-ttu-id="373d1-117">Możliwość ustawienia bieżącego podmiotu zabezpieczeń może oszukać zabezpieczenia oparte na rolach.</span><span class="sxs-lookup"><span data-stu-id="373d1-117">The ability to set the current principal can trick role-based security.</span></span>|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|<span data-ttu-id="373d1-118">Manipulowanie wątkami jest niebezpieczne ze względu na stan zabezpieczeń skojarzony z wątkami.</span><span class="sxs-lookup"><span data-stu-id="373d1-118">Manipulation of threads is dangerous because of the security state associated with threads.</span></span>|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|<span data-ttu-id="373d1-119">Można użyć prywatnych członków, aby pokonać mechanizmy ułatwień dostępu.</span><span class="sxs-lookup"><span data-stu-id="373d1-119">Can use private members to defeat accessibility mechanisms.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="373d1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="373d1-120">See also</span></span>

- [<span data-ttu-id="373d1-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="373d1-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
