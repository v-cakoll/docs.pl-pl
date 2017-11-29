---
title: "Porady: uruchamianie częściowo zaufanego kodu w bibliotece"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
caps.latest.revision: "27"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5dab15c2c43c17b5f83954719ba99a0e5fb73527
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="4aed7-102">Porady: uruchamianie częściowo zaufanego kodu w bibliotece</span><span class="sxs-lookup"><span data-stu-id="4aed7-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="4aed7-103">Sandboxing polega na uruchamianie kodu w środowisku ograniczonych zabezpieczeń, co ogranicza uprawnienia dostępu do kodu.</span><span class="sxs-lookup"><span data-stu-id="4aed7-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="4aed7-104">Na przykład jeśli masz zarządzanej biblioteki ze źródła, który całkowicie nie ufasz, nie należy uruchamiać go jako w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="4aed7-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="4aed7-105">Zamiast tego należy umieszczać kod w izolowanym, która ogranicza uprawnienia do tych, które można spodziewać się muszą (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień).</span><span class="sxs-lookup"><span data-stu-id="4aed7-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="4aed7-106">Sandboxing można również używać do testowania kodu, który będzie rozpowszechniania uruchamianego w środowiskach częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="4aed7-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="4aed7-107"><xref:System.AppDomain> Jest efektywnym sposobem zapewnienia piaskownicy zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aed7-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="4aed7-108">Domeny aplikacji, które są używane do uruchamiania częściowo zaufany kod uprawnień, które definiują chronionych zasobów, które są dostępne podczas uruchamiania w tym <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="4aed7-109">Kod uruchamiany w <xref:System.AppDomain> jest powiązany uprawnienia skojarzone z <xref:System.AppDomain> i będzie mógł uzyskać dostępu do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="4aed7-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="4aed7-110"><xref:System.AppDomain> Obejmuje również <xref:System.Security.Policy.StrongName> tablica, która służy do identyfikowania zestawów, które mają być załadowany jako w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="4aed7-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="4aed7-111">Dzięki temu twórca <xref:System.AppDomain> można uruchomić nowej domeny piaskownicy, umożliwiający zestawy określonego pomocnika być w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="4aed7-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="4aed7-112">Inną opcją w przypadku ładowania zestawów jako w pełni zaufany jest umieszczenie ich w pamięci podręcznej GAC; Jednakże, który będzie ładowanie zestawów jako w pełni zaufany we wszystkich domenach aplikacji utworzone na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4aed7-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="4aed7-113">Lista silnych nazw obsługiwanych na-<xref:System.AppDomain> decyzja, który zapewnia bardziej restrykcyjne określenie.</span><span class="sxs-lookup"><span data-stu-id="4aed7-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="4aed7-114">Można użyć <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> przeciążenie metody, aby określić uprawnienia ustawione dla aplikacji działających w piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="4aed7-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="4aed7-115">To przeciążenie umożliwia określenie dokładnej poziom zabezpieczeń dostępu kodu, który ma.</span><span class="sxs-lookup"><span data-stu-id="4aed7-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="4aed7-116">Zestawy, które są ładowane do <xref:System.AppDomain> przy użyciu tego przeciążenia może albo mieć określony tylko zestaw uprawnień lub może być w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="4aed7-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="4aed7-117">Zestaw otrzymuje pełne zaufanie, gdy jest on w globalnej pamięci podręcznej zestawów lub na liście `fullTrustAssemblies` ( <xref:System.Security.Policy.StrongName>) parametr tablicy.</span><span class="sxs-lookup"><span data-stu-id="4aed7-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="4aed7-118">Tylko zestawy wiadomo, że są w pełni zaufany, należy dodać do `fullTrustAssemblies` listy.</span><span class="sxs-lookup"><span data-stu-id="4aed7-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="4aed7-119">Przeciążenie ma następującą sygnaturą:</span><span class="sxs-lookup"><span data-stu-id="4aed7-119">The overload has the following signature:</span></span>  
  
```  
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="4aed7-120">Parametry <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenie metody Określ nazwę <xref:System.AppDomain>, dowód <xref:System.AppDomain>, <xref:System.AppDomainSetup> obiekt, który identyfikuje baza aplikacji piaskownicy, uprawnienia do użycia i silnej nazwy całkowicie zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="4aed7-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="4aed7-121">Ze względów bezpieczeństwa baza aplikacji określonego w `info` parametr nie może być podstawowy dla hostingu aplikacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aed7-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="4aed7-122">Dla `grantSet` parametru, możesz określić zestaw uprawnień, jawnie utworzono lub standardowe uprawnienie zestaw utworzony przez <xref:System.Security.SecurityManager.GetStandardSandbox%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4aed7-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="4aed7-123">W przeciwieństwie do większości <xref:System.AppDomain> ładuje dowód <xref:System.AppDomain> (przekazywane przez `securityInfo` parametru) nie jest używane do określania zestaw częściowo zaufanych zestawów uprawnień.</span><span class="sxs-lookup"><span data-stu-id="4aed7-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="4aed7-124">Zamiast tego niezależnie jest określona przez `grantSet` parametru.</span><span class="sxs-lookup"><span data-stu-id="4aed7-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="4aed7-125">Jednak dowody może służyć do innych celów, takich jak określanie zakres magazynu izolowanego.</span><span class="sxs-lookup"><span data-stu-id="4aed7-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="4aed7-126">Aby uruchomić aplikację w bibliotece</span><span class="sxs-lookup"><span data-stu-id="4aed7-126">To run an application in a sandbox</span></span>  
  
1.  <span data-ttu-id="4aed7-127">Utwórz zestaw mieć uprawnienia do niezaufanych aplikacji uprawnień.</span><span class="sxs-lookup"><span data-stu-id="4aed7-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="4aed7-128">To minimalne uprawnienia można przyznać <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4aed7-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="4aed7-129">Można również przyznać dodatkowe uprawnienia, które zdaniem użytkownika mogą być bezpieczne dla kodzie niezaufanym; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="4aed7-130">Poniższy kod tworzy nowy zestaw uprawnień o tylko <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4aed7-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```  
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="4aed7-131">Alternatywnie można użyć istniejącego nazwany zestaw uprawnień, takich jak Internet.</span><span class="sxs-lookup"><span data-stu-id="4aed7-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```  
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="4aed7-132"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> Metoda zwraca albo `Internet` zestaw uprawnień lub `LocalIntranet` zestaw uprawnień w zależności od strefy na dowód.</span><span class="sxs-lookup"><span data-stu-id="4aed7-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="4aed7-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>Tworzy uprawnienia dotyczące tożsamości dla niektórych obiektów dowód przekazany jako odwołania.</span><span class="sxs-lookup"><span data-stu-id="4aed7-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2.  <span data-ttu-id="4aed7-134">Podpisz zestaw zawierający klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), który odwołuje się kodzie niezaufanym.</span><span class="sxs-lookup"><span data-stu-id="4aed7-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="4aed7-135">Dodaj <xref:System.Security.Policy.StrongName> używany do podpisywania zestawu do <xref:System.Security.Policy.StrongName> tablicę `fullTrustAssemblies` parametr <xref:System.AppDomain.CreateDomain%2A> wywołania.</span><span class="sxs-lookup"><span data-stu-id="4aed7-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="4aed7-136">Klasa hostująca musi działać jako w pełni zaufany, aby umożliwić wykonywanie kodu częściowego zaufania lub aktualnych aplikacji częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="4aed7-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="4aed7-137">Jest to, jak przeczytać <xref:System.Security.Policy.StrongName> zestawu:</span><span class="sxs-lookup"><span data-stu-id="4aed7-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```  
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="4aed7-138">Nie masz zestawy .NET framework, takich jak mscorlib i System.dll mają zostać dodane do listy pełnego zaufania, ponieważ są one załadowany jako w pełni zaufany z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="4aed7-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3.  <span data-ttu-id="4aed7-139">Inicjowanie <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="4aed7-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="4aed7-140">Z tym parametrem można kontrolować wiele ustawień nowej <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="4aed7-141"><xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość jest ustawienie ważne i powinien być inny niż <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość <xref:System.AppDomain> hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aed7-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="4aed7-142">Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> ustawienia są takie same, aplikacja częściowego zaufania może uzyskać ładowanie (jako w pełni zaufany) wystąpił wyjątek definiuje, w związku z tym wykorzystuje je hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aed7-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="4aed7-143">Jest to kolejny powód, dlaczego catch (wyjątek) nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="4aed7-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="4aed7-144">Ustawienie aplikacji base hosta inaczej niż baza aplikacji w trybie piaskownicy aplikacji zmniejsza ryzyko luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="4aed7-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```  
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4.  <span data-ttu-id="4aed7-145">Wywołanie <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenie metody, aby utworzyć domenę aplikacji przy użyciu parametrów została określona.</span><span class="sxs-lookup"><span data-stu-id="4aed7-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="4aed7-146">Podpis dla tej metody jest:</span><span class="sxs-lookup"><span data-stu-id="4aed7-146">The signature for this method is:</span></span>  
  
    ```  
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="4aed7-147">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="4aed7-147">Additional information:</span></span>  
  
    -   <span data-ttu-id="4aed7-148">Jest to tylko przeciążenia <xref:System.AppDomain.CreateDomain%2A> metody pobierającej <xref:System.Security.PermissionSet> jako parametr, a zatem tylko przeciążenia, które pozwala załadować aplikacji w ustawieniu częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="4aed7-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    -   <span data-ttu-id="4aed7-149">`evidence` Parametr nie jest używany do obliczania zestawu uprawnień; jest używany do identyfikacji przez inne funkcje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4aed7-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    -   <span data-ttu-id="4aed7-150">Ustawienie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwość `info` parametr jest wymagany dla tego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="4aed7-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    -   <span data-ttu-id="4aed7-151">`fullTrustAssemblies` Parametr ma `params` — słowo kluczowe, co oznacza, że nie jest konieczne tworzenie <xref:System.Security.Policy.StrongName> tablicy.</span><span class="sxs-lookup"><span data-stu-id="4aed7-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="4aed7-152">Dozwolone jest przekazywanie 0, 1 lub więcej silnych nazw jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="4aed7-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    -   <span data-ttu-id="4aed7-153">Kod, aby utworzyć domenę aplikacji jest:</span><span class="sxs-lookup"><span data-stu-id="4aed7-153">The code to create the application domain is:</span></span>  
  
    ```  
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5.  <span data-ttu-id="4aed7-154">Ładowanie kod do sandboxing <xref:System.AppDomain> utworzony.</span><span class="sxs-lookup"><span data-stu-id="4aed7-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="4aed7-155">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="4aed7-155">This can be done in two ways:</span></span>  
  
    -   <span data-ttu-id="4aed7-156">Wywołanie <xref:System.AppDomain.ExecuteAssembly%2A> metody dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="4aed7-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    -   <span data-ttu-id="4aed7-157">Użyj <xref:System.Activator.CreateInstanceFrom%2A> metodę w celu utworzenia wystąpienia klasy pochodzące z <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="4aed7-158">Druga metoda jest preferowana, ponieważ ułatwi do przekazania parametrów do nowego <xref:System.AppDomain> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4aed7-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="4aed7-159"><xref:System.Activator.CreateInstanceFrom%2A> Metoda zapewnia dwie ważne funkcje:</span><span class="sxs-lookup"><span data-stu-id="4aed7-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    -   <span data-ttu-id="4aed7-160">Można użyć bazy kodu, który wskazuje lokalizację, która nie zawiera używanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4aed7-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    -   <span data-ttu-id="4aed7-161">Możliwość tworzenia w obszarze <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), która umożliwia utworzenie wystąpienia klasy krytyczne.</span><span class="sxs-lookup"><span data-stu-id="4aed7-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="4aed7-162">(Dzieje się to za każdym razem z zestawu ma nie oznaczenia przezroczystość i jest załadowany jako w pełni zaufany.) Dlatego należy należy zachować ostrożność utworzyć tylko kod, którym ufasz, że za pomocą tej funkcji i zaleca się utworzenie tylko wystąpienia klas w pełni zaufany w nowej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aed7-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```  
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="4aed7-163">Należy pamiętać, aby można było utworzyć wystąpienia klasy w nowej domenie, klasa ma rozszerzenie <xref:System.MarshalByRefObject> — klasa</span><span class="sxs-lookup"><span data-stu-id="4aed7-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```  
    class Sandboxer:MarshalByRefObject  
    ```  
  
6.  <span data-ttu-id="4aed7-164">Dekodowanie nowe wystąpienie domeny do odwołania w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="4aed7-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="4aed7-165">To odwołanie jest używane do wykonywania kodu niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="4aed7-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```  
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7.  <span data-ttu-id="4aed7-166">Wywołanie `ExecuteUntrustedCode` metody w wystąpieniu `Sandboxer` klasy właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="4aed7-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```  
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="4aed7-167">To wywołanie jest wykonywany w domenie aplikacji piaskownicy, która ma ograniczone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4aed7-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
    ```  
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
                (new PermissionSet(PermissionState.Unrestricted)).Assert();  
                Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
    CodeAccessPermission.RevertAssert();  
                Console.ReadLine();  
            }  
        }  
    ```  
  
     <span data-ttu-id="4aed7-168"><xref:System.Reflection>Służy do uzyskania dojścia metody w częściowo zaufanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="4aed7-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="4aed7-169">Dojście może służyć do wykonywania kodu w bezpieczny sposób z minimalne uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4aed7-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="4aed7-170">W poprzednim kodzie <xref:System.Security.PermissionSet.Assert%2A> uprawnienia pełnego zaufania przed wydrukowaniem <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```  
    new PermissionSet(PermissionState.Unrestricted)).Assert()  
    ```  
  
     <span data-ttu-id="4aed7-171">Assert pełnego zaufania jest używany do uzyskania rozszerzonych informacji z <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="4aed7-172">Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metody <xref:System.Security.SecurityException> wykryje, że jest częściowo zaufany kod na stosie i ograniczy zwrócone informacje.</span><span class="sxs-lookup"><span data-stu-id="4aed7-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="4aed7-173">Może to spowodować problemy z zabezpieczeniami, jeśli kod częściowego zaufania można odczytać informacji, ale ryzyko skuteczność została osłabiona przez nieprzyznanie <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="4aed7-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="4aed7-174">Assert pełnego zaufania, które powinny być używane rzadko i tylko wtedy, gdy masz pewność, że użytkownik nie zezwalają na kod częściowego zaufania, aby podnieść poziom do pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="4aed7-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="4aed7-175">Jako zasada nie należy wywoływać kodu, w którym nie ufasz w tej samej funkcji i po wywołaniu assert dla pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="4aed7-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="4aed7-176">Należy dobrze przywrócić assert po zakończeniu korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="4aed7-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4aed7-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="4aed7-177">Example</span></span>  
 <span data-ttu-id="4aed7-178">Poniższy przykład zawiera procedura w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4aed7-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="4aed7-179">W tym przykładzie projektu o nazwie `Sandboxer` w programie Visual Studio rozwiązanie zawiera również projektu o nazwie `UntrustedCode`, która implementuje klasy `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="4aed7-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="4aed7-180">W tym scenariuszu przyjęto został pobrany w zestawie biblioteki zawierający metodę, która powinna zwrócić `true` lub `false` wskazująca, czy liczba podane jest liczbą Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="4aed7-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="4aed7-181">Zamiast tego metodę podejmuje próbę odczytania pliku z komputera.</span><span class="sxs-lookup"><span data-stu-id="4aed7-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="4aed7-182">Poniższy przykład przedstawia kod niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="4aed7-182">The following example shows the untrusted code.</span></span>  
  
```  
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
  
 <span data-ttu-id="4aed7-183">W poniższym przykładzie przedstawiono `Sandboxer` kodu aplikacji, która wykonuje kodzie niezaufanym.</span><span class="sxs-lookup"><span data-stu-id="4aed7-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
```  
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
            (new PermissionSet(PermissionState.Unrestricted)).Assert();  
            Console.WriteLine("SecurityException caught:\n{0}", ex.ToString());  
            CodeAccessPermission.RevertAssert();  
            Console.ReadLine();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aed7-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4aed7-184">See Also</span></span>  
 [<span data-ttu-id="4aed7-185">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="4aed7-185">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
