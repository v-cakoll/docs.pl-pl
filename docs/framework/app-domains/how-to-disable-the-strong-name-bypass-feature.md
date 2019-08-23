---
title: 'Instrukcje: Wyłączanie funkcji pomijania silnej nazwy'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7484e67202c430df6ec2d4bea9cff5a850720ff5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921560"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="540e7-102">Instrukcje: Wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="540e7-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="540e7-103">Począwszy od wersji 3,5 .NET Framework programu Service Pack 1 (SP1), sygnatury silnej nazwy nie są sprawdzane, gdy zestaw jest ładowany do obiektu pełnego <xref:System.AppDomain> zaufania, takiego jak domyślny <xref:System.AppDomain> dla `MyComputer` strefy.</span><span class="sxs-lookup"><span data-stu-id="540e7-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="540e7-104">Jest to nazywane funkcją pomijania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="540e7-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="540e7-105">W środowisku z pełnym zaufaniem wymagania dotyczące <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodło się w przypadku podpisanych, pełnego zaufania zestawów niezależnie od ich sygnatury.</span><span class="sxs-lookup"><span data-stu-id="540e7-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="540e7-106">Jedynym ograniczeniem jest to, że zestaw musi być w pełni zaufany, ponieważ jego strefa jest w pełni zaufana.</span><span class="sxs-lookup"><span data-stu-id="540e7-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="540e7-107">Ponieważ silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie ma powodów, dla których nie można jej zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="540e7-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="540e7-108">Pomijanie sprawdzania poprawności sygnatur silnych nazw zapewnia znaczną poprawę wydajności.</span><span class="sxs-lookup"><span data-stu-id="540e7-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="540e7-109">Funkcja Bypass ma zastosowanie do dowolnego zestawu pełnego zaufania, który nie jest podpisany z opóźnieniem i który jest ładowany do dowolnego pełnego zaufania <xref:System.AppDomain> z katalogu określonego przez jego <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="540e7-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="540e7-110">Można zastąpić funkcję pomijania dla wszystkich aplikacji na komputerze przez ustawienie wartości klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="540e7-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="540e7-111">Można zastąpić ustawienie pojedynczej aplikacji przy użyciu pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="540e7-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="540e7-112">Nie można przywrócić funkcji pomijania dla pojedynczej aplikacji, jeśli została ona wyłączona przez klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="540e7-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="540e7-113">Gdy zastąpisz funkcję pomijania, silna nazwa jest weryfikowana tylko pod kątem poprawności; nie jest ona sprawdzana dla <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="540e7-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="540e7-114">Jeśli chcesz potwierdzić konkretną silną nazwę, musisz wykonać to sprawdzenie oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="540e7-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="540e7-115">Możliwość wymuszenia weryfikacji silnej nazwy zależy od klucza rejestru, zgodnie z opisem w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="540e7-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="540e7-116">Jeśli aplikacja jest uruchomiona w ramach konta, które nie ma uprawnień do uzyskiwania dostępu do tego klucza rejestru na liście kontroli dostępu (ACL), to ustawienie jest nieskuteczne.</span><span class="sxs-lookup"><span data-stu-id="540e7-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="540e7-117">Musisz się upewnić, że dla tego klucza są skonfigurowane uprawnienia ACL, aby można było je odczytać dla wszystkich zestawów.</span><span class="sxs-lookup"><span data-stu-id="540e7-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="540e7-118">Aby wyłączyć funkcję pomijania silnej nazwy dla wszystkich aplikacji</span><span class="sxs-lookup"><span data-stu-id="540e7-118">To disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="540e7-119">Na komputerach 32-bitowych w rejestrze systemowym Utwórz wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\Software\Microsoft.\\ Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="540e7-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="540e7-120">Na komputerach 64-bitowych w rejestrze systemowym Utwórz wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` HKEY_LOCAL_MACHINE\Software\Microsoft.\\ NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucze NETFramework.</span><span class="sxs-lookup"><span data-stu-id="540e7-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="540e7-121">Aby wyłączyć funkcję pomijania silnej nazwy dla pojedynczej aplikacji</span><span class="sxs-lookup"><span data-stu-id="540e7-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="540e7-122">Otwórz lub Utwórz plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="540e7-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="540e7-123">Aby uzyskać więcej informacji na temat tego pliku, zapoznaj się z sekcją pliki konfiguracyjne aplikacji w artykule [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="540e7-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="540e7-124">Dodaj następujący wpis:</span><span class="sxs-lookup"><span data-stu-id="540e7-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="540e7-125">Można przywrócić funkcję pomijania dla aplikacji przez usunięcie ustawienia pliku konfiguracji lub przez ustawienie atrybutu na wartość "true".</span><span class="sxs-lookup"><span data-stu-id="540e7-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="540e7-126">Można włączać i wyłączać sprawdzanie silnej nazwy dla aplikacji tylko wtedy, gdy Funkcja pomijania jest włączona dla komputera.</span><span class="sxs-lookup"><span data-stu-id="540e7-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="540e7-127">Jeśli funkcja pomijania została wyłączona dla komputera, silne nazwy są weryfikowane dla wszystkich aplikacji i nie można pominąć walidacji dla pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="540e7-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540e7-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="540e7-128">See also</span></span>

- [<span data-ttu-id="540e7-129">Sn.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="540e7-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="540e7-130">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="540e7-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="540e7-131">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="540e7-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
