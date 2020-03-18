---
title: 'Jak: Wyłącz funkcję pomijania silnej nazwy'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141105"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="f2d07-102">Jak: Wyłącz funkcję pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="f2d07-102">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="f2d07-103">Począwszy od .NET Framework w wersji 3.5 z dodatkiem Service Pack 1 (SP1), podpisy <xref:System.AppDomain> o silnej nazwie <xref:System.AppDomain> nie `MyComputer` są weryfikowane po załadowaniu zestawu do obiektu pełnego zaufania, takiego jak domyślna dla strefy.</span><span class="sxs-lookup"><span data-stu-id="f2d07-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="f2d07-104">Jest to określane jako funkcja pomijania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="f2d07-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="f2d07-105">W środowisku pełnego zaufania wymagania <xref:System.Security.Permissions.StrongNameIdentityPermission> dotyczące zawsze odnoszą sukcesy dla podpisanych zestawów o pełnym zaufaniu, niezależnie od ich podpisu.</span><span class="sxs-lookup"><span data-stu-id="f2d07-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="f2d07-106">Jedynym ograniczeniem jest to, że zestaw musi być w pełni zaufany, ponieważ jego strefa jest w pełni zaufana.</span><span class="sxs-lookup"><span data-stu-id="f2d07-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="f2d07-107">Ponieważ silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie ma powodu, aby zostać zweryfikowane.</span><span class="sxs-lookup"><span data-stu-id="f2d07-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="f2d07-108">Pomijanie sprawdzania poprawności podpisów o silnej nazwie zapewnia znaczną poprawę wydajności.</span><span class="sxs-lookup"><span data-stu-id="f2d07-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="f2d07-109">Funkcja pomijania ma zastosowanie do każdego zestawu pełnego zaufania, który nie jest podpisany <xref:System.AppDomain> z opóźnieniem i <xref:System.AppDomainSetup.ApplicationBase%2A> który jest ładowany do dowolnego pełnego zaufania z katalogu określonego przez jego właściwość.</span><span class="sxs-lookup"><span data-stu-id="f2d07-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="f2d07-110">Funkcję pomijania dla wszystkich aplikacji na komputerze można zastąpić, ustawiając wartość klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="f2d07-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="f2d07-111">Można zastąpić ustawienie dla pojedynczej aplikacji przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2d07-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="f2d07-112">Nie można przywrócić funkcji pomijania dla pojedynczej aplikacji, jeśli została ona wyłączona przez klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="f2d07-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="f2d07-113">Po zastąpieniu funkcji pomijania silna nazwa jest sprawdzana tylko pod kątem poprawności; nie jest sprawdzany <xref:System.Security.Permissions.StrongNameIdentityPermission>pod kątem .</span><span class="sxs-lookup"><span data-stu-id="f2d07-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="f2d07-114">Jeśli chcesz potwierdzić określoną silną nazwę, musisz wykonać tę kontrolę oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="f2d07-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f2d07-115">Możliwość wymuszenia sprawdzania poprawności silnej nazwy zależy od klucza rejestru, zgodnie z opisem w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="f2d07-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="f2d07-116">Jeśli aplikacja jest uruchomiona na koncie, które nie ma uprawnień listy kontroli dostępu (ACL) do dostępu do tego klucza rejestru, ustawienie jest nieskuteczne.</span><span class="sxs-lookup"><span data-stu-id="f2d07-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="f2d07-117">Należy upewnić się, że prawa acl są skonfigurowane dla tego klucza, dzięki czemu mogą być odczytywane dla wszystkich zestawów.</span><span class="sxs-lookup"><span data-stu-id="f2d07-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="f2d07-118">Wyłącz funkcję pomijania silnej nazwy dla wszystkich aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2d07-118">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="f2d07-119">Na komputerach 32-bitowych w rejestrze systemowym utwórz wpis `AllowStrongNameBypass` DWORD o wartości\\0 o nazwie pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework.</span><span class="sxs-lookup"><span data-stu-id="f2d07-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="f2d07-120">Na komputerach 64-bitowych w rejestrze systemowym utwórz wpis `AllowStrongNameBypass` DWORD o wartości\\0 o nazwie pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Węzeł\Microsoft\\. NETFramework.</span><span class="sxs-lookup"><span data-stu-id="f2d07-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="f2d07-121">Wyłączanie funkcji pomijania silnej nazwy dla pojedynczej aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2d07-121">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="f2d07-122">Otwórz lub utwórz plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2d07-122">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="f2d07-123">Aby uzyskać więcej informacji na temat tego pliku, zobacz sekcję Pliki konfiguracji aplikacji w [polu Konfigurowanie aplikacji](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2d07-123">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="f2d07-124">Dodaj następujący wpis:</span><span class="sxs-lookup"><span data-stu-id="f2d07-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="f2d07-125">Funkcję pomijania aplikacji można przywrócić, usuwając ustawienie pliku konfiguracyjnego `true`lub ustawiając atrybut na .</span><span class="sxs-lookup"><span data-stu-id="f2d07-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2d07-126">Sprawdzanie poprawności silnej nazwy można włączać i wyłączać dla aplikacji tylko wtedy, gdy funkcja pomijania jest włączona dla komputera.</span><span class="sxs-lookup"><span data-stu-id="f2d07-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="f2d07-127">Jeśli funkcja pomijania została wyłączona dla komputera, silne nazwy są sprawdzane dla wszystkich aplikacji i nie można obejść sprawdzania poprawności dla pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2d07-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d07-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2d07-128">See also</span></span>

- [<span data-ttu-id="f2d07-129">Sn.exe (Narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="f2d07-129">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="f2d07-130">\<obejśćTrustedAppStrongNames> element</span><span class="sxs-lookup"><span data-stu-id="f2d07-130">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="f2d07-131">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="f2d07-131">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
