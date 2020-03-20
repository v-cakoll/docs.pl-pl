---
title: 'Porady: uruchamianie częściowo zaufanego kodu w bibliotece'
ms.date: 03/30/2017
helpviewer_keywords:
- partially trusted code
- sandboxing
- partial trust
- restricted security environment
- code security, sandboxing
ms.assetid: d1ad722b-5b49-4040-bff3-431b94bb8095
ms.openlocfilehash: b2f5a72e747f6c71743a7b22fe9f1962ac2f6b53
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181178"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="9d71f-102">Porady: uruchamianie częściowo zaufanego kodu w bibliotece</span><span class="sxs-lookup"><span data-stu-id="9d71f-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="9d71f-103">Piaskownica jest praktyką uruchamiania kodu w ograniczonym środowisku zabezpieczeń, co ogranicza uprawnienia dostępu przyznane do kodu.</span><span class="sxs-lookup"><span data-stu-id="9d71f-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="9d71f-104">Na przykład jeśli masz bibliotekę zarządzaną ze źródła, któremu nie ufasz całkowicie, nie należy jej uruchamiać jako w pełni zaufanej.</span><span class="sxs-lookup"><span data-stu-id="9d71f-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="9d71f-105">Zamiast tego należy umieścić kod w obszarze izolowanym, który ogranicza jego uprawnienia do <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> tych, które oczekują, że będzie potrzebne (na przykład uprawnienia).</span><span class="sxs-lookup"><span data-stu-id="9d71f-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="9d71f-106">Można również użyć piaskownicy do testowania kodu, który będzie dystrybuowany, który będzie uruchamiany w częściowo zaufanych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="9d71f-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="9d71f-107">An <xref:System.AppDomain> jest skutecznym sposobem zapewnienia piaskownicy dla aplikacji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9d71f-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="9d71f-108">Domeny aplikacji, które są używane do uruchamiania częściowo zaufanego kodu mają uprawnienia, <xref:System.AppDomain>które definiują chronione zasoby, które są dostępne podczas uruchamiania w tym .</span><span class="sxs-lookup"><span data-stu-id="9d71f-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="9d71f-109">Kod, który <xref:System.AppDomain> działa wewnątrz jest związany uprawnieniami <xref:System.AppDomain> skojarzonymi z i może uzyskać dostęp tylko do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="9d71f-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="9d71f-110">Zawiera <xref:System.AppDomain> również <xref:System.Security.Policy.StrongName> tablicę, która jest używana do identyfikowania zestawów, które mają być ładowane jako w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="9d71f-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="9d71f-111">Dzięki temu twórca, <xref:System.AppDomain> aby rozpocząć nową domenę w trybie piaskownicy, która umożliwia określone zestawy pomocnika być w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="9d71f-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="9d71f-112">Inną opcją ładowania zestawów jako w pełni zaufanych jest umieszczenie ich w globalnej pamięci podręcznej zestawów; jednak, że będzie załadować zestawy jako w pełni zaufane we wszystkich domenach aplikacji utworzonych na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9d71f-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="9d71f-113">Lista silnych nazwisk popiera<xref:System.AppDomain> decyzję per- która zapewnia bardziej restrykcyjną determinację.</span><span class="sxs-lookup"><span data-stu-id="9d71f-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="9d71f-114">Przeciążenie <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> metody służy do określenia zestawu uprawnień dla aplikacji, które są uruchamiane w obszarze izolowanym.</span><span class="sxs-lookup"><span data-stu-id="9d71f-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="9d71f-115">To przeciążenie umożliwia określenie dokładnego poziomu zabezpieczeń dostępu do kodu, które chcesz.</span><span class="sxs-lookup"><span data-stu-id="9d71f-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="9d71f-116">Zestawy, które są <xref:System.AppDomain> ładowane do za pomocą tego przeciążenia może mieć tylko określony zestaw dotacji lub mogą być w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="9d71f-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="9d71f-117">Zestaw otrzymuje pełne zaufanie, jeśli znajduje się w globalnej `fullTrustAssemblies` pamięci <xref:System.Security.Policy.StrongName>podręcznej zestawów lub jest wymieniony w () parametr tablicy.</span><span class="sxs-lookup"><span data-stu-id="9d71f-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="9d71f-118">Do listy należy dodać tylko zestawy, `fullTrustAssemblies` o których wiadomo, że są w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="9d71f-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="9d71f-119">Przeciążenie ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="9d71f-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="9d71f-120"><xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> Parametry przeciążenia metody określają nazwę <xref:System.AppDomain>, dowód dla <xref:System.AppDomain>obiektu, który identyfikuje bazę <xref:System.AppDomainSetup> aplikacji dla piaskownicy, ustawione uprawnienia do użycia i silne nazwy w pełni zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="9d71f-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="9d71f-121">Ze względów bezpieczeństwa baza `info` aplikacji określona w parametrze nie powinna być podstawą aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="9d71f-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="9d71f-122">Dla `grantSet` parametru można określić zestaw uprawnień, który został jawnie utworzony, <xref:System.Security.SecurityManager.GetStandardSandbox%2A> lub standardowy zestaw uprawnień utworzony przez metodę.</span><span class="sxs-lookup"><span data-stu-id="9d71f-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="9d71f-123">W <xref:System.AppDomain> przeciwieństwie do większości obciążeń <xref:System.AppDomain> dowody dla (który jest dostarczany przez `securityInfo` parametr) nie jest używany do określenia zestawu dotacji dla częściowo zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="9d71f-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="9d71f-124">Zamiast tego jest niezależnie określony `grantSet` przez parametr.</span><span class="sxs-lookup"><span data-stu-id="9d71f-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="9d71f-125">Jednak dowody mogą być używane do innych celów, takich jak określenie zakresu izolowanego magazynu.</span><span class="sxs-lookup"><span data-stu-id="9d71f-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="9d71f-126">Aby uruchomić aplikację w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="9d71f-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="9d71f-127">Utwórz zestaw uprawnień, które mają zostać przyznane niezaufanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d71f-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="9d71f-128">Minimalne uprawnienie, które <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> można udzielić, to uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="9d71f-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="9d71f-129">Można również udzielić dodatkowych uprawnień, które uważasz za bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="9d71f-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="9d71f-130">Poniższy kod tworzy nowy zestaw <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnień tylko z uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="9d71f-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="9d71f-131">Alternatywnie można użyć istniejącego nazwanego zestawu uprawnień, takiego jak Internet.</span><span class="sxs-lookup"><span data-stu-id="9d71f-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="9d71f-132">Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> zwraca zestaw `Internet` uprawnień lub `LocalIntranet` zestaw uprawnień w zależności od strefy w dowodach.</span><span class="sxs-lookup"><span data-stu-id="9d71f-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="9d71f-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A>również konstruuje uprawnienia tożsamości dla niektórych obiektów dowodów przekazanych jako odwołania.</span><span class="sxs-lookup"><span data-stu-id="9d71f-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="9d71f-134">Podpisz zestaw, który zawiera `Sandboxer` klasę hostingu (o nazwie w tym przykładzie), która wywołuje niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="9d71f-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="9d71f-135">Dodaj <xref:System.Security.Policy.StrongName> używane do podpisania zestawu <xref:System.Security.Policy.StrongName> do `fullTrustAssemblies` tablicy <xref:System.AppDomain.CreateDomain%2A> parametru wywołania.</span><span class="sxs-lookup"><span data-stu-id="9d71f-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="9d71f-136">Klasa hostingu musi działać jako w pełni zaufany, aby umożliwić wykonanie kodu częściowego zaufania lub oferować usługi aplikacji częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="9d71f-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="9d71f-137">W ten sposób <xref:System.Security.Policy.StrongName> można odczytać zestawu:</span><span class="sxs-lookup"><span data-stu-id="9d71f-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="9d71f-138">Zestawy .NET Framework, takie jak mscorlib i System.dll, nie muszą być dodawane do listy pełnego zaufania, ponieważ są ładowane jako w pełni zaufane z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9d71f-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="9d71f-139">Zainicjować <xref:System.AppDomainSetup> parametr <xref:System.AppDomain.CreateDomain%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9d71f-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="9d71f-140">Za pomocą tego parametru można kontrolować wiele <xref:System.AppDomain>ustawień nowego .</span><span class="sxs-lookup"><span data-stu-id="9d71f-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="9d71f-141">Właściwość <xref:System.AppDomainSetup.ApplicationBase%2A> jest ważnym ustawieniem i powinna <xref:System.AppDomainSetup.ApplicationBase%2A> się <xref:System.AppDomain> różnić od właściwości aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="9d71f-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="9d71f-142">Jeśli <xref:System.AppDomainSetup.ApplicationBase%2A> ustawienia są takie same, aplikacja częściowego zaufania można uzyskać aplikacji hostingu, aby załadować (jako w pełni zaufany) wyjątek, który definiuje, wykorzystując go.</span><span class="sxs-lookup"><span data-stu-id="9d71f-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="9d71f-143">Jest to kolejny powód, dla którego catch (wyjątek) nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="9d71f-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="9d71f-144">Ustawienie bazy aplikacji hosta inaczej niż baza aplikacji w trybie piaskownicy zmniejsza ryzyko exploitów.</span><span class="sxs-lookup"><span data-stu-id="9d71f-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="9d71f-145">Wywołanie <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> przeciążenia metody, aby utworzyć domenę aplikacji przy użyciu parametrów, które określiliśmy.</span><span class="sxs-lookup"><span data-stu-id="9d71f-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="9d71f-146">Podpis dla tej metody jest:</span><span class="sxs-lookup"><span data-stu-id="9d71f-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="9d71f-147">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="9d71f-147">Additional information:</span></span>  
  
    - <span data-ttu-id="9d71f-148">Jest to tylko przeciążenie <xref:System.AppDomain.CreateDomain%2A> metody, <xref:System.Security.PermissionSet> która przyjmuje jako parametr, a tym samym tylko przeciążenie, które pozwala załadować aplikację w ustawieniach częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="9d71f-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="9d71f-149">Parametr `evidence` nie jest używany do obliczania zestawu uprawnień; służy do identyfikacji przez inne funkcje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d71f-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="9d71f-150">Ustawienie <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości parametru `info` jest obowiązkowe dla tego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="9d71f-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="9d71f-151">Parametr `fullTrustAssemblies` zawiera `params` słowo kluczowe, co oznacza, że <xref:System.Security.Policy.StrongName> nie jest konieczne tworzenie tablicy.</span><span class="sxs-lookup"><span data-stu-id="9d71f-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="9d71f-152">Przekazywanie 0, 1 lub więcej silnych nazw jako parametry jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9d71f-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="9d71f-153">Kod do utworzenia domeny aplikacji jest:</span><span class="sxs-lookup"><span data-stu-id="9d71f-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="9d71f-154">Załaduj kod <xref:System.AppDomain> do utworzonego piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="9d71f-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="9d71f-155">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="9d71f-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="9d71f-156">Wywołanie <xref:System.AppDomain.ExecuteAssembly%2A> metody dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="9d71f-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="9d71f-157">Użyj <xref:System.Activator.CreateInstanceFrom%2A> metody, aby utworzyć wystąpienie klasy <xref:System.MarshalByRefObject> pochodnej <xref:System.AppDomain>w nowym .</span><span class="sxs-lookup"><span data-stu-id="9d71f-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="9d71f-158">Druga metoda jest preferowana, ponieważ ułatwia przekazywanie parametrów <xref:System.AppDomain> do nowego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9d71f-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="9d71f-159">Metoda <xref:System.Activator.CreateInstanceFrom%2A> ta zapewnia dwie ważne cechy:</span><span class="sxs-lookup"><span data-stu-id="9d71f-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="9d71f-160">Można użyć bazy kodu, który wskazuje lokalizację, która nie zawiera zestawu.</span><span class="sxs-lookup"><span data-stu-id="9d71f-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="9d71f-161">Tworzenie można wykonać w <xref:System.Security.CodeAccessPermission.Assert%2A> ramach for<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>full-trust ( ), który umożliwia utworzenie wystąpienia klasy krytycznej.</span><span class="sxs-lookup"><span data-stu-id="9d71f-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="9d71f-162">(Dzieje się tak, gdy zespół nie ma oznaczeń przezroczystości i jest ładowany jako w pełni zaufany). W związku z tym należy uważać, aby utworzyć tylko kod, który można ufać z tej funkcji i zaleca się tworzenie tylko wystąpienia w pełni zaufanych klas w nowej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d71f-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="9d71f-163">Należy zauważyć, że aby utworzyć wystąpienie klasy w nowej domenie, klasa musi rozszerzyć <xref:System.MarshalByRefObject> klasę</span><span class="sxs-lookup"><span data-stu-id="9d71f-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="9d71f-164">Odrapuj nowe wystąpienie domeny na odwołanie w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="9d71f-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="9d71f-165">To odwołanie jest używane do wykonywania niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="9d71f-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="9d71f-166">Wywołanie `ExecuteUntrustedCode` metody w wystąpieniu klasy, `Sandboxer` która właśnie została utworzona.</span><span class="sxs-lookup"><span data-stu-id="9d71f-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="9d71f-167">To wywołanie jest wykonywane w domenie aplikacji w trybie piaskownicy, która ma ograniczone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9d71f-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="9d71f-168"><xref:System.Reflection>służy do uzyskania dojścia metody w zestawie częściowo zaufanych.</span><span class="sxs-lookup"><span data-stu-id="9d71f-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="9d71f-169">Dojście może służyć do wykonywania kodu w bezpieczny sposób z minimalnymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="9d71f-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="9d71f-170">W poprzednim kodzie <xref:System.Security.PermissionSet.Assert%2A> zanotuj uprawnienie pełnego <xref:System.Security.SecurityException>zaufania przed wydrukowaniem pliku .</span><span class="sxs-lookup"><span data-stu-id="9d71f-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="9d71f-171">Potwierdzenie pełnego zaufania służy do uzyskiwania rozszerzonych informacji z pliku <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="9d71f-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="9d71f-172">Bez <xref:System.Security.PermissionSet.Assert%2A>, <xref:System.Security.SecurityException.ToString%2A> metoda <xref:System.Security.SecurityException> odkryje, że istnieje częściowo zaufany kod na stosie i ograniczy zwracane informacje.</span><span class="sxs-lookup"><span data-stu-id="9d71f-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="9d71f-173">Może to spowodować problemy z zabezpieczeniami, jeśli kod częściowego zaufania może odczytać <xref:System.Security.Permissions.UIPermission>te informacje, ale ryzyko jest ograniczone przez nieudzielenie .</span><span class="sxs-lookup"><span data-stu-id="9d71f-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="9d71f-174">Potwierdzenie pełnego zaufania powinny być używane oszczędnie i tylko wtedy, gdy masz pewność, że nie zezwalasz na częściowe zaufanie kodu podnieść do pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="9d71f-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="9d71f-175">Z reguły nie należy wywoływać kodu, którego nie ufasz w tej samej funkcji i po wywołaniu potwierdzenia dla pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="9d71f-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="9d71f-176">Jest dobrą praktyką, aby zawsze przywrócić potwierdzenia po zakończeniu korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="9d71f-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d71f-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d71f-177">Example</span></span>  
 <span data-ttu-id="9d71f-178">Poniższy przykład implementuje procedurę w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9d71f-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="9d71f-179">W przykładzie projekt `Sandboxer` o nazwie w rozwiązaniu programu `UntrustedCode`Visual Studio zawiera `UntrustedClass`również projekt o nazwie , który implementuje klasę .</span><span class="sxs-lookup"><span data-stu-id="9d71f-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="9d71f-180">W tym scenariuszu założono, że pobrano zestaw biblioteki `true` zawierający metodę, która ma zwrócić lub `false` wskazać, czy podana liczba jest numerem Fibonacciego.</span><span class="sxs-lookup"><span data-stu-id="9d71f-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="9d71f-181">Zamiast tego metoda próbuje odczytać plik z komputera.</span><span class="sxs-lookup"><span data-stu-id="9d71f-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="9d71f-182">W poniższym przykładzie pokazano niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="9d71f-182">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="9d71f-183">W poniższym `Sandboxer` przykładzie pokazano kod aplikacji, który wykonuje niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="9d71f-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d71f-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d71f-184">See also</span></span>

- [<span data-ttu-id="9d71f-185">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="9d71f-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
