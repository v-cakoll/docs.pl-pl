---
title: 'Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caa9afcb1ab2ca53bba849c39651ca4cba3a9c77
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316534"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="1bfb5-102">Instrukcje: Uruchamianie częściowo zaufanego kodu w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="1bfb5-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="1bfb5-103">Tryb piaskownicy jest rozwiązaniem polegającym na uruchamianie kodu w środowisku ograniczonych zabezpieczeń ogranicza uprawnienia udzielone do kodu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="1bfb5-104">Na przykład jeśli masz zarządzanej biblioteki ze źródła, którym ufasz całkowicie, nie należy uruchamiać go jako w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="1bfb5-105">Zamiast tego należy umieszczać kodu w piaskownicy, która ogranicza uprawnienia do tych, które mogą potrzebować (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień).</span><span class="sxs-lookup"><span data-stu-id="1bfb5-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="1bfb5-106">Aby przetestować kod, który można będzie wydawać uruchamianego tylko w środowiskach częściowo zaufanym umożliwia także tryb piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="1bfb5-107"><xref:System.AppDomain> Jest skutecznym sposobem zapewnienia piaskownicy dla zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="1bfb5-108">Domeny aplikacji, które są używane do uruchamiania częściowo zaufanego kodu mają uprawnienia, które definiują chronionych zasobów, które są dostępne podczas uruchamiania w ramach którego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="1bfb5-109">Kod, który działa wewnątrz <xref:System.AppDomain> jest ograniczone przez uprawnienia związane z <xref:System.AppDomain> i będzie mógł uzyskać dostęp tylko określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="1bfb5-110"><xref:System.AppDomain> Obejmuje również <xref:System.Security.Policy.StrongName> tablica, która służy do identyfikowania zestawów, które mają być załadowany jako w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="1bfb5-111">Dzięki temu twórca <xref:System.AppDomain> można uruchomić nowej domeny piaskownicy, umożliwiająca pomocnika określonych zestawów jako w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="1bfb5-112">Innym rozwiązaniem do ładowania zestawów jako w pełni zaufane jest umieszczenie ich w globalnej pamięci podręcznej; Jednakże, zostaną załadowane zestawy jako w pełni zaufany we wszystkich domenach aplikacji, utworzony na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="1bfb5-113">Lista silnej nazwy obsługuje na-<xref:System.AppDomain> decyzji, który zapewnia bardziej restrykcyjne określenie.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="1bfb5-114">Możesz użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenia metody, aby określić uprawnienia ustawione dla aplikacji działających w piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="1bfb5-115">Tego przeciążenia można określić dokładny poziom zabezpieczeń dostępu kodu, który ma.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="1bfb5-116">Zestawy, które są ładowane do <xref:System.AppDomain> przy użyciu tego przeciążenia można albo mieć określony tylko zestaw uprawnień lub może być w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="1bfb5-117">Zestaw jest udzielone pełne zaufanie, jeśli znajduje się w globalnej pamięci podręcznej lub na liście `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr tablicy.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="1bfb5-118">Tylko zestawy znane jako w pełni zaufany, powinny zostać dodane do `fullTrustAssemblies` listy.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="1bfb5-119">Przeciążenie ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="1bfb5-120">Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody umożliwia określenie nazwy <xref:System.AppDomain>, dowód <xref:System.AppDomain>, <xref:System.AppDomainSetup> obiektu, który identyfikuje podstawa aplikacji piaskownicy, zestaw uprawnień, aby użyć i silne nazwy dla całkowicie zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="1bfb5-121">Ze względów bezpieczeństwa podstawy aplikacji określony w `info` parametrów nie powinny być podstawowy dla aplikacji macierzystej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="1bfb5-122">Dla `grantSet` parametru, można określić zestaw uprawnień, utworzono jawnie lub standardowe uprawnienie zestaw utworzony przez <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="1bfb5-123">W przeciwieństwie do większości <xref:System.AppDomain> ładuje dowodów dla <xref:System.AppDomain> (inaczej niż w `securityInfo` parametr) nie jest używana do określenia przyznanego zestawu dla częściowo zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="1bfb5-124">Zamiast tego niezależnie jest określona przez `grantSet` parametru.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="1bfb5-125">Jednak dowód może służyć do innych celów, takich jak określanie zakresu wydzielonej pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="1bfb5-126">Aby uruchomić aplikację w bibliotece</span><span class="sxs-lookup"><span data-stu-id="1bfb5-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="1bfb5-127">Utwórz zestaw uprawnień, aby można mu było przydzielić niezaufanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="1bfb5-128">Jest co najmniej uprawnienie można przyznać <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="1bfb5-129">Możesz też przyznawać dodatkowe uprawnienia, które Twoim zdaniem mogą być bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="1bfb5-130">Poniższy kod tworzy nowy zestaw uprawnień o tylko <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="1bfb5-131">Alternatywnie można użyć istniejącego nazwany zestaw uprawnień, takich jak Internet.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="1bfb5-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda zwraca albo `Internet` zestaw uprawnień lub `LocalIntranet` uprawnienia w zależności od strefy w dowodów.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <xref:System.Security.SecurityManager.GetStandardSandbox%2A> <span data-ttu-id="1bfb5-133">tworzy również uprawnienia tożsamości dla niektórych obiektów dowód przekazywane jako odwołania.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-133">also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="1bfb5-134">Podpisz zestaw, który zawiera klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), wywołuje niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="1bfb5-135">Dodaj <xref:System.Security.Policy.StrongName> używany do podpisywania zestawu do <xref:System.Security.Policy.StrongName> tablicę `fullTrustAssemblies` parametru <xref:System.AppDomain.CreateDomain%2A> wywołania.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="1bfb5-136">Klasa hostingu musi działać jako w pełni zaufany, aby włączyć wykonywanie częściowo zaufanemu kodowi lub oferty usług do aplikacji częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="1bfb5-137">Jest to, jak odczytać <xref:System.Security.Policy.StrongName> zestawu:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="1bfb5-138">Nie masz zestawów .NET framework, takich jak mscorlib i System.dll ma zostać dodany do listy pełnego zaufania, ponieważ są one załadowane jako w pełni zaufany z globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="1bfb5-139">Inicjowanie <xref:System.AppDomainSetup> parametru <xref:System.AppDomain.CreateDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="1bfb5-140">Z tego parametru można kontrolować wiele ustawień nowej <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="1bfb5-141"><xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość jest ważne ustawienia i powinna być inna niż <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość <xref:System.AppDomain> hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="1bfb5-142">Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> ustawień są takie same, aplikacja częściowego zaufania może uzyskać ładowanie (jako w pełni zaufany) wyjątek, który definiuje, w związku z tym pełniejsze wykorzystanie hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="1bfb5-143">Jest to kolejny powód, dlaczego catch (exception) nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="1bfb5-144">Ustawienie aplikacji base hosta różni się od podstawy aplikacji dla aplikacji w trybie piaskownicy zmniejsza ryzyko luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="1bfb5-145">Wywołaj <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody tworzenia domeny aplikacji przy użyciu parametrów została określona.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="1bfb5-146">Podpis dla tej metody jest:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="1bfb5-147">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-147">Additional information:</span></span>  
  
    -   <span data-ttu-id="1bfb5-148">Jest to jedyna przeciążenia <xref:System.AppDomain.CreateDomain%2A> metody, która przyjmuje <xref:System.Security.PermissionSet> jako parametr, a zatem jedynym przeciążenia, które umożliwia ładowanie aplikacji w środowisku częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    -   <span data-ttu-id="1bfb5-149">`evidence` Parametr nie jest używany do obliczania zestawu uprawnień; jest używany do identyfikacji przez inne funkcje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="1bfb5-150">Ustawienie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość `info` parametr jest obowiązkowy w przypadku tego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    -   <span data-ttu-id="1bfb5-151">`fullTrustAssemblies` Parametr ma `params` — słowo kluczowe, co oznacza, że nie jest niezbędne do utworzenia <xref:System.Security.Policy.StrongName> tablicy.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="1bfb5-152">Przekazywanie jako parametrów 0, 1 lub więcej silnych nazw jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    -   <span data-ttu-id="1bfb5-153">Kod, aby utworzyć domenę aplikacji to:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="1bfb5-154">Ładowanie kodu do piaskownicy <xref:System.AppDomain> utworzony.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="1bfb5-155">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-155">This can be done in two ways:</span></span>  
  
    -   <span data-ttu-id="1bfb5-156">Wywołaj <xref:System.AppDomain.ExecuteAssembly%2A> metody dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    -   <span data-ttu-id="1bfb5-157">Użyj <xref:System.Activator.CreateInstanceFrom%2A> metodę, aby utworzyć wystąpienie klasy pochodne <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="1bfb5-158">Druga metoda jest preferowana, ponieważ ułatwia do przekazania parametrów do nowego <xref:System.AppDomain> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="1bfb5-159"><xref:System.Activator.CreateInstanceFrom%2A> Metoda zapewnia dwie ważne funkcje:</span><span class="sxs-lookup"><span data-stu-id="1bfb5-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    -   <span data-ttu-id="1bfb5-160">Możesz użyć bazy kodu, który wskazuje na lokalizację, która nie zawiera zestawu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    -   <span data-ttu-id="1bfb5-161">Masz możliwości tworzenia w obszarze <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), która pozwala na tworzenie wystąpienia klasy krytycznych.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="1bfb5-162">(Jest to wykonywane zawsze, gdy zestaw ma oznaczenia nie przezroczystości, a także jest ładowany jako w pełni zaufany.) W związku z tym musisz być ostrożnym, aby utworzyć kod, którym ufasz, że za pomocą tej funkcji i zaleca się utworzenie tylko wystąpienia klasy w pełni zaufany w nowej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="1bfb5-163">Należy pamiętać, aby można było utworzyć wystąpienia klasy w nowej domenie, klasa ma rozszerzenie <xref:System.MarshalByRefObject> klasy</span><span class="sxs-lookup"><span data-stu-id="1bfb5-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="1bfb5-164">Dekodowanie nowe wystąpienie domeny do odwołania w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="1bfb5-165">Ta dokumentacja jest używany do wykonania niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="1bfb5-166">Wywołaj `ExecuteUntrustedCode` metody w wystąpieniu `Sandboxer` klasy właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="1bfb5-167">To wywołanie jest wykonywane w domenie aplikacji w trybie piaskownicy ma ograniczone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```csharp
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the entry point in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            // Invoke the method.  
            target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
        //When information is obtained from a SecurityException extra information is provided if it is   
        //accessed in full-trust.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
    ```  
  
     <xref:System.Reflection> <span data-ttu-id="1bfb5-168">Służy do uzyskać dojścia do metody w częściowo zaufanym zestawem.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-168">is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="1bfb5-169">Uchwyt może służyć do wykonywania kodu w bezpieczny sposób za pomocą minimalny poziom uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="1bfb5-170">W poprzednim kodzie, należy pamiętać, <xref:System.Security.PermissionSet.Assert%2A> uprawnienia pełnego zaufania, przed rozpoczęciem drukowania <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="1bfb5-171">Asercja pełnego zaufania jest używany do uzyskiwania rozszerzonych informacji z <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="1bfb5-172">Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metody <xref:System.Security.SecurityException> wykryje, że jest częściowo zaufany kod w stosie i ograniczyć zwracane informacje dotyczą.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="1bfb5-173">Może to spowodować problemy z zabezpieczeniami, jeśli częściowo zaufanemu kodowi można odczytać te informacje, ale ryzyko skuteczność została osłabiona przez nieprzyznanie <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="1bfb5-174">Asercja pełnego zaufania należy używać oszczędnie i tylko wtedy, gdy masz pewność, że nie umożliwi częściowo zaufanemu kodowi do podniesienia uprawnień na w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="1bfb5-175">Zgodnie z zasadą nie wymagają kodu, której nie ufasz w tej samej funkcji i asercja wywołuje się, aby uzyskać pełne zaufanie.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="1bfb5-176">Jest dobrą praktyką, aby zawsze wracają assert, po zakończeniu korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bfb5-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bfb5-177">Example</span></span>  
 <span data-ttu-id="1bfb5-178">Poniższy przykład wykonuje procedurę w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="1bfb5-179">W tym przykładzie projekt o nazwie `Sandboxer` w programie Visual Studio rozwiązanie zawiera także projekt o nazwie `UntrustedCode`, który implementuje klasa `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="1bfb5-180">W tym scenariuszu przyjmuje się, czy zostały pobrane zestawu biblioteki, zawierający metodę, która powinna zwrócić `true` lub `false` do wskazania, czy liczba podane jest liczbą Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="1bfb5-181">Zamiast tego metoda próbuje odczytać plik z komputera.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="1bfb5-182">Poniższy przykład pokazuje niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-182">The following example shows the untrusted code.</span></span>  
  
```csharp
using System;  
using System.IO;  
namespace UntrustedCode  
{  
    public class UntrustedClass  
    {  
        // Pretend to be a method checking if a number is a Fibonacci  
        // but which actually attempts to read a file.  
        public static bool IsFibonacci(int number)  
        {  
           File.ReadAllText("C:\\Temp\\file.txt");  
           return false;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="1bfb5-183">W poniższym przykładzie przedstawiono `Sandboxer` kod aplikacji, która wykonuje niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="1bfb5-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Security;  
using System.Security.Policy;  
using System.Security.Permissions;  
using System.Reflection;  
using System.Runtime.Remoting;  
  
//The Sandboxer class needs to derive from MarshalByRefObject so that we can create it in another   
// AppDomain and refer to it from the default AppDomain.  
class Sandboxer : MarshalByRefObject  
{  
    const string pathToUntrusted = @"..\..\..\UntrustedCode\bin\Debug";  
    const string untrustedAssembly = "UntrustedCode";  
    const string untrustedClass = "UntrustedCode.UntrustedClass";  
    const string entryPoint = "IsFibonacci";  
    private static Object[] parameters = { 45 };  
    static void Main()  
    {  
        //Setting the AppDomainSetup. It is very important to set the ApplicationBase to a folder   
        //other than the one in which the sandboxer resides.  
        AppDomainSetup adSetup = new AppDomainSetup();  
        adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
  
        //Setting the permissions for the AppDomain. We give the permission to execute and to   
        //read/discover the location where the untrusted code is loaded.  
        PermissionSet permSet = new PermissionSet(PermissionState.None);  
        permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
  
        //We want the sandboxer assembly's strong name, so that we can add it to the full trust list.  
        StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
  
        //Now we have everything we need to create the AppDomain, so let's create it.  
        AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
  
        //Use CreateInstanceFrom to load an instance of the Sandboxer class into the  
        //new AppDomain.   
        ObjectHandle handle = Activator.CreateInstanceFrom(  
            newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
            typeof(Sandboxer).FullName  
            );  
        //Unwrap the new domain instance into a reference in this domain and use it to execute the   
        //untrusted code.  
        Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
        newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    }  
    public void ExecuteUntrustedCode(string assemblyName, string typeName, string entryPoint, Object[] parameters)  
    {  
        //Load the MethodInfo for a method in the new Assembly. This might be a method you know, or   
        //you can use Assembly.EntryPoint to get to the main function in an executable.  
        MethodInfo target = Assembly.Load(assemblyName).GetType(typeName).GetMethod(entryPoint);  
        try  
        {  
            //Now invoke the method.  
            bool retVal = (bool)target.Invoke(null, parameters);  
        }  
        catch (Exception ex)  
        {  
            // When we print informations from a SecurityException extra information can be printed if we are   
            //calling it with a full-trust stack.  
            new PermissionSet(PermissionState.Unrestricted).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1bfb5-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bfb5-184">See also</span></span>

- [<span data-ttu-id="1bfb5-185">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="1bfb5-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
