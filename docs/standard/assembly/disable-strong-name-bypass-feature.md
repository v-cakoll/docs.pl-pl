---
title: 'Instrukcje: wyłączanie funkcji pomijania silnej nazwy'
description: Obejście silnej nazwy pomija sprawdzanie poprawności podpisu w w pełni zaufanych domenach w programie .NET. Tę funkcję można zastąpić dla jednej aplikacji lub wszystkich aplikacji.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: 1914997b322591d8deda13d00192bc5f60d81ca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378492"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="694f7-104">Instrukcje: wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="694f7-104">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="694f7-105">Począwszy od wersji 3,5 .NET Framework programu Service Pack 1 (SP1), sygnatury silnej nazwy nie są sprawdzane, gdy zestaw jest ładowany do obiektu pełnego zaufania <xref:System.AppDomain> , takiego jak domyślny <xref:System.AppDomain> dla `MyComputer` strefy.</span><span class="sxs-lookup"><span data-stu-id="694f7-105">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="694f7-106">Jest to nazywane funkcją pomijania silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="694f7-106">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="694f7-107">W środowisku z pełnym zaufaniem wymagania dotyczące <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodło się w przypadku podpisanych, pełnego zaufania zestawów niezależnie od ich sygnatury.</span><span class="sxs-lookup"><span data-stu-id="694f7-107">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="694f7-108">Jedynym ograniczeniem jest to, że zestaw musi być w pełni zaufany, ponieważ jego strefa jest w pełni zaufana.</span><span class="sxs-lookup"><span data-stu-id="694f7-108">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="694f7-109">Ponieważ silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie ma powodów, dla których nie można jej zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="694f7-109">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="694f7-110">Pomijanie sprawdzania poprawności sygnatur silnych nazw zapewnia znaczną poprawę wydajności.</span><span class="sxs-lookup"><span data-stu-id="694f7-110">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="694f7-111">Funkcja Bypass ma zastosowanie do dowolnego zestawu pełnego zaufania, który nie jest podpisany z opóźnieniem i który jest ładowany do dowolnego pełnego zaufania <xref:System.AppDomain> z katalogu określonego przez jego <xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="694f7-111">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="694f7-112">Można zastąpić funkcję pomijania dla wszystkich aplikacji na komputerze przez ustawienie wartości klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="694f7-112">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="694f7-113">Można zastąpić ustawienie pojedynczej aplikacji przy użyciu pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="694f7-113">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="694f7-114">Nie można przywrócić funkcji pomijania dla pojedynczej aplikacji, jeśli została ona wyłączona przez klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="694f7-114">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="694f7-115">Gdy zastąpisz funkcję pomijania, silna nazwa jest weryfikowana tylko pod kątem poprawności; nie jest ona sprawdzana dla <xref:System.Security.Permissions.StrongNameIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="694f7-115">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="694f7-116">Jeśli chcesz potwierdzić konkretną silną nazwę, musisz wykonać to sprawdzenie oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="694f7-116">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="694f7-117">Możliwość wymuszenia weryfikacji silnej nazwy zależy od klucza rejestru, zgodnie z opisem w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="694f7-117">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="694f7-118">Jeśli aplikacja jest uruchomiona w ramach konta, które nie ma uprawnień do uzyskiwania dostępu do tego klucza rejestru na liście kontroli dostępu (ACL), to ustawienie jest nieskuteczne.</span><span class="sxs-lookup"><span data-stu-id="694f7-118">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="694f7-119">Musisz się upewnić, że dla tego klucza są skonfigurowane uprawnienia ACL, aby można było je odczytać dla wszystkich zestawów.</span><span class="sxs-lookup"><span data-stu-id="694f7-119">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="694f7-120">Wyłącz funkcję pomijania silnej nazwy dla wszystkich aplikacji</span><span class="sxs-lookup"><span data-stu-id="694f7-120">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="694f7-121">Na komputerach 32-bitowych w rejestrze systemowym Utwórz wpis DWORD z wartością 0 o nazwie `AllowStrongNameBypass` w HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="694f7-121">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="694f7-122">Na komputerach 64-bitowych w rejestrze systemowym Utwórz wpis DWORD z wartością 0 o nazwie `AllowStrongNameBypass` w HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework i HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . Klucze NETFramework.</span><span class="sxs-lookup"><span data-stu-id="694f7-122">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="694f7-123">Wyłączenie funkcji pomijania silnej nazwy dla pojedynczej aplikacji</span><span class="sxs-lookup"><span data-stu-id="694f7-123">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="694f7-124">Otwórz lub Utwórz plik konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="694f7-124">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="694f7-125">Aby uzyskać więcej informacji na temat tego pliku, zapoznaj się z sekcją pliki konfiguracyjne aplikacji w artykule [Konfigurowanie aplikacji](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="694f7-125">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="694f7-126">Dodaj następujący wpis:</span><span class="sxs-lookup"><span data-stu-id="694f7-126">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="694f7-127">Można przywrócić funkcję pomijania dla aplikacji, usuwając ustawienia pliku konfiguracji lub ustawiając atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="694f7-127">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="694f7-128">Można włączać i wyłączać sprawdzanie silnej nazwy dla aplikacji tylko wtedy, gdy Funkcja pomijania jest włączona dla komputera.</span><span class="sxs-lookup"><span data-stu-id="694f7-128">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="694f7-129">Jeśli funkcja pomijania została wyłączona dla komputera, silne nazwy są weryfikowane dla wszystkich aplikacji i nie można pominąć walidacji dla pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="694f7-129">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="694f7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="694f7-130">See also</span></span>

- [<span data-ttu-id="694f7-131">SN. exe (Narzędzie silnej nazwy)</span><span class="sxs-lookup"><span data-stu-id="694f7-131">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="694f7-132">\<bypassTrustedAppStrongNames, element></span><span class="sxs-lookup"><span data-stu-id="694f7-132">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="694f7-133">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="694f7-133">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
