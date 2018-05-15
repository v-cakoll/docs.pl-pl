---
title: 'Porady: wyłączanie funkcji pomijania silnej nazwy'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9604969ea073b07af0eca8d481f5459ee15d099
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="08996-102">Porady: wyłączanie funkcji pomijania silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="08996-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="08996-103">Począwszy od wersji programu .NET Framework 3.5 z dodatkiem Service Pack 1 (SP1), podpisów silnej nazwy nie są weryfikowane podczas zestaw jest ładowany do pełnego zaufania <xref:System.AppDomain> obiektu, takie jak domyślny <xref:System.AppDomain> dla `MyComputer` strefy.</span><span class="sxs-lookup"><span data-stu-id="08996-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="08996-104">Jest to określane jako silnej nazwy pomijania funkcji.</span><span class="sxs-lookup"><span data-stu-id="08996-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="08996-105">W pełni zaufanym środowisku, wymaga dla <xref:System.Security.Permissions.StrongNameIdentityPermission> zawsze powiodła się dla podpisanej zestawy pełnego zaufania, niezależnie od ich podpisu.</span><span class="sxs-lookup"><span data-stu-id="08996-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="08996-106">Tylko ograniczenie jest, że zestaw muszą być całkowicie zaufane, ponieważ jej strefy jest w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="08996-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="08996-107">Silna nazwa nie jest czynnikiem decydującym w tych warunkach, nie istnieje przyczyna jej do sprawdzenia poprawności.</span><span class="sxs-lookup"><span data-stu-id="08996-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="08996-108">Pomijanie sprawdzania poprawności podpisów silnej nazwy zapewnia znaczną poprawę wydajności.</span><span class="sxs-lookup"><span data-stu-id="08996-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="08996-109">Funkcja pomijania dotyczy dowolnego zestawu pełnego zaufania, który jest nie podpisywany z opóźnieniem i który jest ładowany do dowolnego pełnego zaufania <xref:System.AppDomain> z katalogu określonego przez jego <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="08996-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="08996-110">Funkcja pomijania dla wszystkich aplikacji na komputerze można zmienić, ustawiając wartość klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="08996-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="08996-111">Można zastąpić to ustawienie dla jednej aplikacji przy użyciu pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08996-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="08996-112">Nie można przywrócić funkcja pomijania dla jednej aplikacji, jeśli wyłączono go przy użyciu klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="08996-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="08996-113">Gdy przesłonięcia funkcji pomijania silnej nazwy jest weryfikowane tylko pod kątem poprawności; nie jest zaznaczone dla <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="08996-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="08996-114">Aby potwierdzić określonych silnej nazwy, należy wykonać sprawdzanie oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="08996-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="08996-115">Możliwość wymuszenia Walidacja silnej nazwy jest zależna od klucz rejestru zgodnie z opisem w poniższej procedurze.</span><span class="sxs-lookup"><span data-stu-id="08996-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="08996-116">Jeśli aplikacja działa w ramach konta, które nie ma dostępu do kontroli listę kontroli dostępu (ACL) uprawnienia dostępu do tego klucza rejestru, to ustawienie jest nieskuteczne.</span><span class="sxs-lookup"><span data-stu-id="08996-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="08996-117">Upewnij się czy praw listy ACL są skonfigurowane dla tego klucza, dzięki czemu mogą być odczytywane dla wszystkich zestawów.</span><span class="sxs-lookup"><span data-stu-id="08996-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="08996-118">Aby wyłączyć silnej nazwy pomijania funkcji dla wszystkich aplikacji</span><span class="sxs-lookup"><span data-stu-id="08996-118">To disable the strong-name bypass feature for all applications</span></span>  
  
-   <span data-ttu-id="08996-119">Na komputerach z 32-bitowe w rejestrze systemu utworzyć wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Klucz NETFramework.</span><span class="sxs-lookup"><span data-stu-id="08996-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
-   <span data-ttu-id="08996-120">Na komputerach 64-bitowych w rejestrze systemu, Utwórz wpis DWORD o wartości 0 o nazwie `AllowStrongNameBypass` w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework i HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Klucze NETFramework.</span><span class="sxs-lookup"><span data-stu-id="08996-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="08996-121">Aby wyłączyć silnej nazwy pomijania funkcji dla jednej aplikacji</span><span class="sxs-lookup"><span data-stu-id="08996-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1.  <span data-ttu-id="08996-122">Otwarcia lub utworzenia pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08996-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="08996-123">Aby uzyskać więcej informacji na temat tego pliku, zobacz sekcję pliki konfiguracji aplikacji w [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="08996-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2.  <span data-ttu-id="08996-124">Dodaj następujący wpis:</span><span class="sxs-lookup"><span data-stu-id="08996-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="08996-125">Funkcja pomijania dla aplikacji można przywrócić przez usunięcie ustawienie pliku konfiguracji lub ustawienie atrybutu na wartość "true".</span><span class="sxs-lookup"><span data-stu-id="08996-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08996-126">Walidacja silnej nazwy włączać i wyłączać dla aplikacji można włączyć tylko wtedy, gdy funkcja pomijania jest włączona na komputerze.</span><span class="sxs-lookup"><span data-stu-id="08996-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="08996-127">Jeśli funkcja pomijania zostało wyłączone dla komputera, silnych nazw są weryfikowane dla wszystkich aplikacji i nie można pominąć weryfikacji dla pojedynczej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="08996-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08996-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08996-128">See Also</span></span>  
 [<span data-ttu-id="08996-129">Sn.exe (narzędzie silnych nazw)</span><span class="sxs-lookup"><span data-stu-id="08996-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="08996-130">\<bypasstrustedappstrongnames — > — Element</span><span class="sxs-lookup"><span data-stu-id="08996-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [<span data-ttu-id="08996-131">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="08996-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
