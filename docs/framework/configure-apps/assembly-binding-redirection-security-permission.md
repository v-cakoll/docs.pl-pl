---
title: Uprawnienie zabezpieczeń przekierowania powiązania zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b9b9ac5c4e8ce08b9f926b0cdf7149dbdd9ac2da
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501436"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="bf34a-102">Uprawnienie zabezpieczeń przekierowania powiązania zestawu</span><span class="sxs-lookup"><span data-stu-id="bf34a-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="bf34a-103">Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bf34a-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="bf34a-104">Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich.</span><span class="sxs-lookup"><span data-stu-id="bf34a-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="bf34a-105">To uprawnienie jest przydzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagą <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="bf34a-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="bf34a-106">Zestawy zarządzane nie mają uprawnień domyślnie.</span><span class="sxs-lookup"><span data-stu-id="bf34a-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="bf34a-107">Do aplikacji działających w strefie intranetu i zaufane (maszyna lokalna) jest udzielane uprawnienie zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="bf34a-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="bf34a-108">Aplikacje działające w strefie Internet jest bezwzględnie zabronione wykonywaniu przekierowanie powiązań zestawów.</span><span class="sxs-lookup"><span data-stu-id="bf34a-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="bf34a-109">Uprawnienie nie jest wymagane, jeśli przekierowanie zestawów jest wykonywana w plik zasad wydawcy, który jest kontrolowany przez wydawcę składnika lub w pliku konfiguracji komputera, który jest kontrolowany przez administratora.</span><span class="sxs-lookup"><span data-stu-id="bf34a-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="bf34a-110">Jednak uprawnienia są wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "no" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bf34a-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="bf34a-111">W poniższej tabeli przedstawiono domyślne ustawienia zabezpieczeń dla **BindingRedirects** flagi.</span><span class="sxs-lookup"><span data-stu-id="bf34a-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="bf34a-112">Strefy</span><span class="sxs-lookup"><span data-stu-id="bf34a-112">Zone</span></span>|<span data-ttu-id="bf34a-113">Ustawienia flagi BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="bf34a-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="bf34a-114">Zaufanej strefy (komputer lokalny)</span><span class="sxs-lookup"><span data-stu-id="bf34a-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="bf34a-115">**DALEJ**</span><span class="sxs-lookup"><span data-stu-id="bf34a-115">**ON**</span></span>|  
|<span data-ttu-id="bf34a-116">Strefy intranet</span><span class="sxs-lookup"><span data-stu-id="bf34a-116">Intranet Zone</span></span>|<span data-ttu-id="bf34a-117">**DALEJ**</span><span class="sxs-lookup"><span data-stu-id="bf34a-117">**ON**</span></span>|  
|<span data-ttu-id="bf34a-118">Strefa Internet</span><span class="sxs-lookup"><span data-stu-id="bf34a-118">Internet Zone</span></span>|<span data-ttu-id="bf34a-119">**OFF**</span><span class="sxs-lookup"><span data-stu-id="bf34a-119">**OFF**</span></span>|  
|<span data-ttu-id="bf34a-120">Niezaufane stref</span><span class="sxs-lookup"><span data-stu-id="bf34a-120">Untrusted zones</span></span>|<span data-ttu-id="bf34a-121">**OFF**</span><span class="sxs-lookup"><span data-stu-id="bf34a-121">**OFF**</span></span>|  
  
 <span data-ttu-id="bf34a-122">Administrator może zmienić te ustawienia zabezpieczeń do obsługi lub ograniczyć konkretnych scenariuszy na danym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bf34a-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="bf34a-123">Są dostępne żadne narzędzia wielokanałowej **BindingRedirects** ustawienia domyślnego; flagi administrator musi ręcznie edytować plik Security.config — na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf34a-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf34a-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf34a-124">See Also</span></span>  
 [<span data-ttu-id="bf34a-125">Pliki zasad wydawcy i wykonywanie Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="bf34a-125">Publisher Policy Files and Side-by-Side Execution</span></span>](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="bf34a-126">Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="bf34a-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="bf34a-127">Wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="bf34a-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
