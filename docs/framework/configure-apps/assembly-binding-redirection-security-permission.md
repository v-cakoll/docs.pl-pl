---
title: "Uprawnienie zabezpieczeń przekierowania powiązania zestawu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ddaf9965a3b3b5d6171a643b198db93309afad48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="e1a74-102">Uprawnienie zabezpieczeń przekierowania powiązania zestawu</span><span class="sxs-lookup"><span data-stu-id="e1a74-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="e1a74-103">Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="e1a74-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="e1a74-104">Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich.</span><span class="sxs-lookup"><span data-stu-id="e1a74-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="e1a74-105">Uprawnienie zostanie udzielone przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> Flaga na <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="e1a74-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="e1a74-106">Zarządzanych zestawów nie mają uprawnień domyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1a74-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="e1a74-107">Uprawnienie zabezpieczeń otrzymuje do aplikacji działających w strefie intranetu i zaufane (komputer lokalny).</span><span class="sxs-lookup"><span data-stu-id="e1a74-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="e1a74-108">Aplikacje uruchomione w strefie Internet są zabronione wykonywanie przekierowanie powiązań zestawów.</span><span class="sxs-lookup"><span data-stu-id="e1a74-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="e1a74-109">Uprawnienie nie jest wymagane, jeśli przekierowanie zestawów odbywa się w pliku zasad wydawcy, który jest kontrolowany przez wydawcę składnika lub w pliku konfiguracji komputera, które są kontrolowane przez administratora.</span><span class="sxs-lookup"><span data-stu-id="e1a74-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="e1a74-110">Jednak uprawnienia są wymagane dla aplikacji, aby jawnie Ignoruj przy użyciu zasad wydawcy [ \<zastosować publisherPolicy = "nie" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1a74-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="e1a74-111">W poniższej tabeli przedstawiono domyślne ustawienia zabezpieczeń dla **BindingRedirects** flagi.</span><span class="sxs-lookup"><span data-stu-id="e1a74-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="e1a74-112">strefy</span><span class="sxs-lookup"><span data-stu-id="e1a74-112">Zone</span></span>|<span data-ttu-id="e1a74-113">Ustawienia flagi BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="e1a74-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="e1a74-114">Strefa Zaufane (komputer lokalny)</span><span class="sxs-lookup"><span data-stu-id="e1a74-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="e1a74-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="e1a74-115">**ON**</span></span>|  
|<span data-ttu-id="e1a74-116">Strefy intranet</span><span class="sxs-lookup"><span data-stu-id="e1a74-116">Intranet Zone</span></span>|<span data-ttu-id="e1a74-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="e1a74-117">**ON**</span></span>|  
|<span data-ttu-id="e1a74-118">Strefa Internet</span><span class="sxs-lookup"><span data-stu-id="e1a74-118">Internet Zone</span></span>|<span data-ttu-id="e1a74-119">**WYŁĄCZANIE**</span><span class="sxs-lookup"><span data-stu-id="e1a74-119">**OFF**</span></span>|  
|<span data-ttu-id="e1a74-120">Niezaufane stref</span><span class="sxs-lookup"><span data-stu-id="e1a74-120">Untrusted zones</span></span>|<span data-ttu-id="e1a74-121">**WYŁĄCZANIE**</span><span class="sxs-lookup"><span data-stu-id="e1a74-121">**OFF**</span></span>|  
  
 <span data-ttu-id="e1a74-122">Administrator może zmienić te ustawienia zabezpieczeń do obsługi lub ograniczyć określonych scenariuszy na danym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e1a74-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="e1a74-123">Nie ma żadnych narzędzi do zmiany **BindingRedirects** ustawienia domyślnego; flagi administrator musi ręcznie zmodyfikować plik Security.config — na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1a74-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a74-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1a74-124">See Also</span></span>  
 [<span data-ttu-id="e1a74-125">Pliki zasad wydawcy i wykonywanie Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="e1a74-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="e1a74-126">Porady: Włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="e1a74-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="e1a74-127">Wykonanie Side-by-Side</span><span class="sxs-lookup"><span data-stu-id="e1a74-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
