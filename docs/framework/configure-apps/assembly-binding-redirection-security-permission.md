---
title: Uprawnienie zabezpieczeń przekierowania powiązania zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921372"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="672f7-102">Uprawnienie zabezpieczeń przekierowania powiązania zestawu</span><span class="sxs-lookup"><span data-stu-id="672f7-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="672f7-103">Jawne przekierowanie powiązań zestawu w pliku konfiguracji aplikacji wymaga uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="672f7-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="672f7-104">Dotyczy to przekierowań zestawów programu .NET Framework i zestawów firm trzecich.</span><span class="sxs-lookup"><span data-stu-id="672f7-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="672f7-105">Uprawnienie jest udzielane przez ustawienie <xref:System.Security.Permissions.SecurityPermissionFlag> flagi na <xref:System.Security.Permissions.SecurityPermission> .</span><span class="sxs-lookup"><span data-stu-id="672f7-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="672f7-106">Zarządzane zestawy nie mają domyślnie żadnych uprawnień.</span><span class="sxs-lookup"><span data-stu-id="672f7-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="672f7-107">Uprawnienia zabezpieczeń są udzielane aplikacjom działającym w strefie zaufanej (komputer lokalny) i intranet.</span><span class="sxs-lookup"><span data-stu-id="672f7-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="672f7-108">Aplikacje działające w strefie Internetu są ściśle zabronione przed przekierowaniem powiązań zestawu.</span><span class="sxs-lookup"><span data-stu-id="672f7-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="672f7-109">Uprawnienie nie jest wymagane, jeśli przekierowanie zestawu jest wykonywane w pliku zasad wydawcy, który jest kontrolowany przez wydawcę składnika lub w pliku konfiguracyjnym komputera kontrolowanym przez administratora.</span><span class="sxs-lookup"><span data-stu-id="672f7-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="672f7-110">Jednak uprawnienie jest wymagane, aby aplikacja jawnie ignorował zasady wydawcy przy użyciu [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) elementu w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="672f7-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="672f7-111">W poniższej tabeli przedstawiono domyślne ustawienia zabezpieczeń flagi **BindingRedirects** .</span><span class="sxs-lookup"><span data-stu-id="672f7-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="672f7-112">Strefa</span><span class="sxs-lookup"><span data-stu-id="672f7-112">Zone</span></span>|<span data-ttu-id="672f7-113">Ustawienie flagi BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="672f7-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="672f7-114">Strefa zaufana (maszyna lokalna)</span><span class="sxs-lookup"><span data-stu-id="672f7-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="672f7-115">**Z**</span><span class="sxs-lookup"><span data-stu-id="672f7-115">**ON**</span></span>|  
|<span data-ttu-id="672f7-116">Strefa intranetowa</span><span class="sxs-lookup"><span data-stu-id="672f7-116">Intranet Zone</span></span>|<span data-ttu-id="672f7-117">**Z**</span><span class="sxs-lookup"><span data-stu-id="672f7-117">**ON**</span></span>|  
|<span data-ttu-id="672f7-118">Strefa Internet</span><span class="sxs-lookup"><span data-stu-id="672f7-118">Internet Zone</span></span>|<span data-ttu-id="672f7-119">**Logowanie**</span><span class="sxs-lookup"><span data-stu-id="672f7-119">**OFF**</span></span>|  
|<span data-ttu-id="672f7-120">Niezaufane strefy</span><span class="sxs-lookup"><span data-stu-id="672f7-120">Untrusted zones</span></span>|<span data-ttu-id="672f7-121">**Logowanie**</span><span class="sxs-lookup"><span data-stu-id="672f7-121">**OFF**</span></span>|  
  
 <span data-ttu-id="672f7-122">Administrator może zmienić te ustawienia zabezpieczeń, aby obsługiwać lub ograniczać określone scenariusze na danym komputerze.</span><span class="sxs-lookup"><span data-stu-id="672f7-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="672f7-123">Nie ma narzędzi do zmiany ustawienia flagi **BindingRedirects** z domyślnego. Administrator musi ręcznie edytować plik Security. config na komputerze użytkownika.</span><span class="sxs-lookup"><span data-stu-id="672f7-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672f7-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="672f7-124">See also</span></span>

- <span data-ttu-id="672f7-125">[Pliki zasad wydawcy i wykonywanie równoczesne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="672f7-125">[Publisher Policy Files and Side-by-Side Execution](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))</span></span>
- [<span data-ttu-id="672f7-126">Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań</span><span class="sxs-lookup"><span data-stu-id="672f7-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="672f7-127">Wykonywanie równoczesne</span><span class="sxs-lookup"><span data-stu-id="672f7-127">Side-by-Side Execution</span></span>](../deployment/side-by-side-execution.md)
