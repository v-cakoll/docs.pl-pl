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
ms.openlocfilehash: 0191846f5589b0162ba342161fb5919ff20099d4
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215862"
---
# <a name="how-to-run-partially-trusted-code-in-a-sandbox"></a><span data-ttu-id="111ce-102">Porady: uruchamianie częściowo zaufanego kodu w bibliotece</span><span class="sxs-lookup"><span data-stu-id="111ce-102">How to: Run Partially Trusted Code in a Sandbox</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="111ce-103">Tryb piaskownicy jest praktycznym sposobem uruchamiania kodu w ograniczonym środowisku zabezpieczeń, który ogranicza uprawnienia dostępu przyznane do kodu.</span><span class="sxs-lookup"><span data-stu-id="111ce-103">Sandboxing is the practice of running code in a restricted security environment, which limits the access permissions granted to the code.</span></span> <span data-ttu-id="111ce-104">Na przykład, jeśli masz bibliotekę zarządzaną z źródła, które nie jest całkowicie zaufane, nie należy uruchamiać go jako w pełni zaufany.</span><span class="sxs-lookup"><span data-stu-id="111ce-104">For example, if you have a managed library from a source you do not completely trust, you should not run it as fully trusted.</span></span> <span data-ttu-id="111ce-105">Zamiast tego należy umieścić kod w piaskownicy, który ogranicza jego uprawnienia do tych, których oczekuje potrzeba (na przykład <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> uprawnienia).</span><span class="sxs-lookup"><span data-stu-id="111ce-105">Instead, you should place the code in a sandbox that limits its permissions to those that you expect it to need (for example, <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission).</span></span>  
  
 <span data-ttu-id="111ce-106">Możesz również użyć piaskownicy do testowania kodu, który będzie wykonywany w środowiskach częściowo zaufanych.</span><span class="sxs-lookup"><span data-stu-id="111ce-106">You can also use sandboxing to test code you will be distributing that will run in partially trusted environments.</span></span>  
  
 <span data-ttu-id="111ce-107"><xref:System.AppDomain> jest skutecznym sposobem udostępniania piaskownicy dla aplikacji zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="111ce-107">An <xref:System.AppDomain> is an effective way of providing a sandbox for managed applications.</span></span> <span data-ttu-id="111ce-108">Domeny aplikacji używane do uruchamiania częściowo zaufanego kodu mają uprawnienia definiujące chronione zasoby, które są dostępne podczas uruchamiania w ramach tego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="111ce-108">Application domains that are used for running partially trusted code have permissions that define the protected resources that are available when running within that <xref:System.AppDomain>.</span></span> <span data-ttu-id="111ce-109">Kod, który jest uruchamiany w <xref:System.AppDomain> jest powiązany z uprawnieniami skojarzonymi z <xref:System.AppDomain> i może uzyskiwać dostęp tylko do określonych zasobów.</span><span class="sxs-lookup"><span data-stu-id="111ce-109">Code that runs inside the <xref:System.AppDomain> is bound by the permissions associated with the <xref:System.AppDomain> and is allowed to access only the specified resources.</span></span> <span data-ttu-id="111ce-110"><xref:System.AppDomain> zawiera również tablicę <xref:System.Security.Policy.StrongName>, która jest używana do identyfikowania zestawów, które mają zostać załadowane jako w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="111ce-110">The <xref:System.AppDomain> also includes a <xref:System.Security.Policy.StrongName> array that is used to identify assemblies that are to be loaded as fully trusted.</span></span> <span data-ttu-id="111ce-111">Umożliwia to twórcy <xref:System.AppDomain> uruchamiania nowej domeny w trybie piaskownicy, która umożliwia pełne zaufane zestawy pomocnika.</span><span class="sxs-lookup"><span data-stu-id="111ce-111">This enables the creator of an <xref:System.AppDomain> to start a new sandboxed domain that allows specific helper assemblies to be fully trusted.</span></span> <span data-ttu-id="111ce-112">Kolejną opcją ładowania zestawów jako w pełni zaufanej jest umieszczenie ich w globalnej pamięci podręcznej zestawów; Jednak program będzie ładować zestawy jako w pełni zaufane we wszystkich domenach aplikacji utworzonych na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="111ce-112">Another option for loading assemblies as fully trusted is to place them in the global assembly cache; however, that will load assemblies as fully trusted in all application domains created on that computer.</span></span> <span data-ttu-id="111ce-113">Lista silnych nazw obsługuje decyzję dla<xref:System.AppDomain>, która zapewnia bardziej restrykcyjne Określanie.</span><span class="sxs-lookup"><span data-stu-id="111ce-113">The list of strong names supports a per-<xref:System.AppDomain> decision that provides more restrictive determination.</span></span>  
  
 <span data-ttu-id="111ce-114">Można użyć przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType>, aby określić zestaw uprawnień dla aplikacji, które działają w piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="111ce-114">You can use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> method overload to specify the permission set for applications that run in a sandbox.</span></span> <span data-ttu-id="111ce-115">To przeciążenie umożliwia określenie dokładnego poziomu zabezpieczeń dostępu kodu.</span><span class="sxs-lookup"><span data-stu-id="111ce-115">This overload enables you to specify the exact level of code access security you want.</span></span> <span data-ttu-id="111ce-116">Zestawy, które są ładowane do <xref:System.AppDomain> przy użyciu tego przeciążenia, mogą mieć określony zestaw dotacji lub mogą być w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="111ce-116">Assemblies that are loaded into an <xref:System.AppDomain> by using this overload can either have the specified grant set only, or can be fully trusted.</span></span> <span data-ttu-id="111ce-117">Zestaw uzyskuje pełne zaufanie, jeśli znajduje się w globalnej pamięci podręcznej zestawów lub znajduje się w `fullTrustAssemblies` (<xref:System.Security.Policy.StrongName>) parametr tablicy.</span><span class="sxs-lookup"><span data-stu-id="111ce-117">The assembly is granted full trust if it is in the global assembly cache or listed in the `fullTrustAssemblies` (the <xref:System.Security.Policy.StrongName>) array parameter.</span></span> <span data-ttu-id="111ce-118">Do listy `fullTrustAssemblies` należy dodać tylko zestawy znane jako w pełni zaufane.</span><span class="sxs-lookup"><span data-stu-id="111ce-118">Only assemblies known to be fully trusted should be added to the `fullTrustAssemblies` list.</span></span>  
  
 <span data-ttu-id="111ce-119">Przeciążenie ma następujący podpis:</span><span class="sxs-lookup"><span data-stu-id="111ce-119">The overload has the following signature:</span></span>  
  
```csharp
AppDomain.CreateDomain( string friendlyName,  
                        Evidence securityInfo,  
                        AppDomainSetup info,  
                        PermissionSet grantSet,  
                        params StrongName[] fullTrustAssemblies);  
```  
  
 <span data-ttu-id="111ce-120">Parametry przeciążenia metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> określają nazwę <xref:System.AppDomain>, dowody dla <xref:System.AppDomain>, obiekt <xref:System.AppDomainSetup>, który identyfikuje bazę aplikacji dla piaskownicy, zestaw uprawnień, który ma być używany, oraz silne nazwy dla w pełni zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="111ce-120">The parameters for the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload specify the name of the <xref:System.AppDomain>, the evidence for the <xref:System.AppDomain>, the <xref:System.AppDomainSetup> object that identifies the application base for the sandbox, the permission set to use, and the strong names for fully trusted assemblies.</span></span>  
  
 <span data-ttu-id="111ce-121">Ze względów bezpieczeństwa baza aplikacji określona w parametrze `info` nie powinna być bazą aplikacji dla aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="111ce-121">For security reasons, the application base specified in the `info` parameter should not be the application base for the hosting application.</span></span>  
  
 <span data-ttu-id="111ce-122">Dla parametru `grantSet` można określić zestaw uprawnień, który został utworzony jawnie, lub standardowy zestaw uprawnień utworzony przez metodę <xref:System.Security.SecurityManager.GetStandardSandbox%2A>.</span><span class="sxs-lookup"><span data-stu-id="111ce-122">For the `grantSet` parameter, you can specify either a permission set you have explicitly created, or a standard permission set created by the <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method.</span></span>  
  
 <span data-ttu-id="111ce-123">W przeciwieństwie do większości obciążeń <xref:System.AppDomain>, dowody dla <xref:System.AppDomain> (które są dostarczane przez parametr `securityInfo`) nie są używane do określenia zestawu dotacji dla częściowo zaufanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="111ce-123">Unlike most <xref:System.AppDomain> loads, the evidence for the <xref:System.AppDomain> (which is provided by the `securityInfo` parameter) is not used to determine the grant set for the partially trusted assemblies.</span></span> <span data-ttu-id="111ce-124">Zamiast tego jest on niezależnie określony przez parametr `grantSet`.</span><span class="sxs-lookup"><span data-stu-id="111ce-124">Instead, it is independently specified by the `grantSet` parameter.</span></span> <span data-ttu-id="111ce-125">Jednakże dowody mogą być używane do innych celów, takich jak określenie zakresu izolowanego magazynu.</span><span class="sxs-lookup"><span data-stu-id="111ce-125">However, the evidence can be used for other purposes such as determining the isolated storage scope.</span></span>  
  
### <a name="to-run-an-application-in-a-sandbox"></a><span data-ttu-id="111ce-126">Aby uruchomić aplikację w piaskownicy</span><span class="sxs-lookup"><span data-stu-id="111ce-126">To run an application in a sandbox</span></span>  
  
1. <span data-ttu-id="111ce-127">Utwórz zestaw uprawnień, który ma zostać udzielony dla niezaufanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="111ce-127">Create the permission set to be granted to the untrusted application.</span></span> <span data-ttu-id="111ce-128">Minimalnym uprawnieniem, które można udzielić, jest uprawnienie <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.</span><span class="sxs-lookup"><span data-stu-id="111ce-128">The minimum permission you can grant is <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span> <span data-ttu-id="111ce-129">Możesz również udzielić dodatkowych uprawnień, które mogą być bezpieczne dla niezaufanego kodu; na przykład <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span><span class="sxs-lookup"><span data-stu-id="111ce-129">You can also grant additional permissions you think might be safe for untrusted code; for example, <xref:System.Security.Permissions.IsolatedStorageFilePermission>.</span></span> <span data-ttu-id="111ce-130">Poniższy kod tworzy nowy zestaw uprawnień z uprawnieniami tylko <xref:System.Security.Permissions.SecurityPermissionFlag.Execution>.</span><span class="sxs-lookup"><span data-stu-id="111ce-130">The following code creates a new permission set with only <xref:System.Security.Permissions.SecurityPermissionFlag.Execution> permission.</span></span>  
  
    ```csharp
    PermissionSet permSet = new PermissionSet(PermissionState.None);  
    permSet.AddPermission(new SecurityPermission(SecurityPermissionFlag.Execution));  
    ```  
  
     <span data-ttu-id="111ce-131">Alternatywnie możesz użyć istniejącego zestawu uprawnień o nazwie, takiego jak Internet.</span><span class="sxs-lookup"><span data-stu-id="111ce-131">Alternatively, you can use an existing named permission set, such as Internet.</span></span>  
  
    ```csharp
    Evidence ev = new Evidence();  
    ev.AddHostEvidence(new Zone(SecurityZone.Internet));  
    PermissionSet internetPS = SecurityManager.GetStandardSandbox(ev);  
    ```  
  
     <span data-ttu-id="111ce-132">Metoda <xref:System.Security.SecurityManager.GetStandardSandbox%2A> zwraca zestaw uprawnień `Internet` lub zestaw uprawnień `LocalIntranet` w zależności od strefy w zeznaniach.</span><span class="sxs-lookup"><span data-stu-id="111ce-132">The <xref:System.Security.SecurityManager.GetStandardSandbox%2A> method returns either an `Internet` permission set or a `LocalIntranet` permission set depending on the zone in the evidence.</span></span> <span data-ttu-id="111ce-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> również konstruuje uprawnienia tożsamości dla niektórych obiektów dowodu przesłanych jako odwołania.</span><span class="sxs-lookup"><span data-stu-id="111ce-133"><xref:System.Security.SecurityManager.GetStandardSandbox%2A> also constructs identity permissions for some of the evidence objects passed as references.</span></span>  
  
2. <span data-ttu-id="111ce-134">Podpisz zestaw zawierający klasę hostingu (o nazwie `Sandboxer` w tym przykładzie), która wywołuje niezaufany kod.</span><span class="sxs-lookup"><span data-stu-id="111ce-134">Sign the assembly that contains the hosting class (named `Sandboxer` in this example) that calls the untrusted code.</span></span> <span data-ttu-id="111ce-135">Dodaj <xref:System.Security.Policy.StrongName> używany do podpisywania zestawu do tablicy <xref:System.Security.Policy.StrongName> `fullTrustAssemblies` parametru wywołania <xref:System.AppDomain.CreateDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="111ce-135">Add the <xref:System.Security.Policy.StrongName> used to sign the assembly to the <xref:System.Security.Policy.StrongName> array of the `fullTrustAssemblies` parameter of the <xref:System.AppDomain.CreateDomain%2A> call.</span></span> <span data-ttu-id="111ce-136">Klasa hostingu musi działać jako w pełni zaufana, aby umożliwić wykonywanie kodu częściowego zaufania lub oferowanie usług dla aplikacji częściowo zaufanej.</span><span class="sxs-lookup"><span data-stu-id="111ce-136">The hosting class must run as fully trusted to enable the execution of the partial-trust code or to offer services to the partial-trust application.</span></span> <span data-ttu-id="111ce-137">Jest to sposób odczytywania <xref:System.Security.Policy.StrongName> zestawu:</span><span class="sxs-lookup"><span data-stu-id="111ce-137">This is how you read the <xref:System.Security.Policy.StrongName> of an assembly:</span></span>  
  
    ```csharp
    StrongName fullTrustAssembly = typeof(Sandboxer).Assembly.Evidence.GetHostEvidence<StrongName>();  
    ```  
  
     <span data-ttu-id="111ce-138">Zestawy .NET Framework, takie jak mscorlib i system. dll, nie muszą być dodawane do listy całkowicie zaufanych, ponieważ są załadowane jako w pełni zaufane z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="111ce-138">.NET Framework assemblies such as mscorlib and System.dll do not have to be added to the full-trust list because they are loaded as fully trusted from the global assembly cache.</span></span>  
  
3. <span data-ttu-id="111ce-139">Zainicjuj <xref:System.AppDomainSetup> parametr metody <xref:System.AppDomain.CreateDomain%2A>.</span><span class="sxs-lookup"><span data-stu-id="111ce-139">Initialize the <xref:System.AppDomainSetup> parameter of the <xref:System.AppDomain.CreateDomain%2A> method.</span></span> <span data-ttu-id="111ce-140">Za pomocą tego parametru można kontrolować wiele ustawień nowego <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="111ce-140">With this parameter, you can control many of the settings of the new <xref:System.AppDomain>.</span></span> <span data-ttu-id="111ce-141">Właściwość <xref:System.AppDomainSetup.ApplicationBase%2A> jest ważnym ustawieniem i powinna być inna niż Właściwość <xref:System.AppDomainSetup.ApplicationBase%2A> dla <xref:System.AppDomain> aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="111ce-141">The <xref:System.AppDomainSetup.ApplicationBase%2A> property is an important setting, and should be different from the <xref:System.AppDomainSetup.ApplicationBase%2A> property for the <xref:System.AppDomain> of the hosting application.</span></span> <span data-ttu-id="111ce-142">Jeśli ustawienia <xref:System.AppDomainSetup.ApplicationBase%2A> są takie same, aplikacja częściowej relacji zaufania może pobrać aplikację hostingu (jako w pełni zaufana), którą definiuje wyjątek, a tym samym ją wykorzystać.</span><span class="sxs-lookup"><span data-stu-id="111ce-142">If the <xref:System.AppDomainSetup.ApplicationBase%2A> settings are the same, the partial-trust application can get the hosting application to load (as fully trusted) an exception it defines, thus exploiting it.</span></span> <span data-ttu-id="111ce-143">Jest to kolejny powód, dla którego nie zaleca się przechwytywania (wyjątek).</span><span class="sxs-lookup"><span data-stu-id="111ce-143">This is another reason why a catch (exception) is not recommended.</span></span> <span data-ttu-id="111ce-144">Ustawienie bazy aplikacji hosta różni się od bazy aplikacji w aplikacji w trybie piaskownicy, co zmniejsza ryzyko ataków wykorzystujących luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="111ce-144">Setting the application base of the host differently from the application base of the sandboxed application mitigates the risk of exploits.</span></span>  
  
    ```csharp
    AppDomainSetup adSetup = new AppDomainSetup();  
    adSetup.ApplicationBase = Path.GetFullPath(pathToUntrusted);  
    ```  
  
4. <span data-ttu-id="111ce-145">Wywołaj Przeciążenie metody <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29>, aby utworzyć domenę aplikacji przy użyciu określonych parametrów.</span><span class="sxs-lookup"><span data-stu-id="111ce-145">Call the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29> method overload to create the application domain using the parameters we have specified.</span></span>  
  
     <span data-ttu-id="111ce-146">Sygnaturą tej metody jest:</span><span class="sxs-lookup"><span data-stu-id="111ce-146">The signature for this method is:</span></span>  
  
    ```csharp
    public static AppDomain CreateDomain(string friendlyName,   
        Evidence securityInfo, AppDomainSetup info, PermissionSet grantSet,   
        params StrongName[] fullTrustAssemblies)  
    ```  
  
     <span data-ttu-id="111ce-147">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="111ce-147">Additional information:</span></span>  
  
    - <span data-ttu-id="111ce-148">Jest to jedyne Przeciążenie metody <xref:System.AppDomain.CreateDomain%2A>, która przyjmuje <xref:System.Security.PermissionSet> jako parametr, i w ten sposób jedynym przeciążeniem umożliwiającym załadowanie aplikacji w ustawieniu częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="111ce-148">This is the only overload of the <xref:System.AppDomain.CreateDomain%2A> method that takes a <xref:System.Security.PermissionSet> as a parameter, and thus the only overload that lets you load an application in a partial-trust setting.</span></span>  
  
    - <span data-ttu-id="111ce-149">Parametr `evidence` nie jest używany do obliczania zestawu uprawnień; służy do identyfikacji przez inne funkcje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="111ce-149">The `evidence` parameter is not used to calculate a permission set; it is used for identification by other features of the .NET Framework.</span></span>  
  
    - <span data-ttu-id="111ce-150">Ustawienie właściwości <xref:System.AppDomainSetup.ApplicationBase%2A> parametru `info` jest obowiązkowe dla tego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="111ce-150">Setting the <xref:System.AppDomainSetup.ApplicationBase%2A> property of the `info` parameter is mandatory for this overload.</span></span>  
  
    - <span data-ttu-id="111ce-151">`fullTrustAssemblies` parametr zawiera słowo kluczowe `params`, co oznacza, że nie jest konieczne tworzenie tablicy <xref:System.Security.Policy.StrongName>.</span><span class="sxs-lookup"><span data-stu-id="111ce-151">The `fullTrustAssemblies` parameter has the `params` keyword, which means that it is not necessary to create a <xref:System.Security.Policy.StrongName> array.</span></span> <span data-ttu-id="111ce-152">Przekazanie wartości 0, 1 lub większej liczby silnych nazw jako parametrów jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="111ce-152">Passing 0, 1, or more strong names as parameters is allowed.</span></span>  
  
    - <span data-ttu-id="111ce-153">Kod do utworzenia domeny aplikacji:</span><span class="sxs-lookup"><span data-stu-id="111ce-153">The code to create the application domain is:</span></span>  
  
    ```csharp
    AppDomain newDomain = AppDomain.CreateDomain("Sandbox", null, adSetup, permSet, fullTrustAssembly);  
    ```  
  
5. <span data-ttu-id="111ce-154">Załaduj kod do utworzonego <xref:System.AppDomain> piaskownicy.</span><span class="sxs-lookup"><span data-stu-id="111ce-154">Load the code into the sandboxing <xref:System.AppDomain> that you created.</span></span> <span data-ttu-id="111ce-155">Można to zrobić na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="111ce-155">This can be done in two ways:</span></span>  
  
    - <span data-ttu-id="111ce-156">Wywołaj metodę <xref:System.AppDomain.ExecuteAssembly%2A> zestawu.</span><span class="sxs-lookup"><span data-stu-id="111ce-156">Call the <xref:System.AppDomain.ExecuteAssembly%2A> method for the assembly.</span></span>  
  
    - <span data-ttu-id="111ce-157">Użyj metody <xref:System.Activator.CreateInstanceFrom%2A>, aby utworzyć wystąpienie klasy pochodzącej od <xref:System.MarshalByRefObject> w nowym <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="111ce-157">Use the <xref:System.Activator.CreateInstanceFrom%2A> method to create an instance of a class derived from <xref:System.MarshalByRefObject> in the new <xref:System.AppDomain>.</span></span>  
  
     <span data-ttu-id="111ce-158">Druga metoda jest preferowana, ponieważ ułatwia przekazywanie parametrów do nowego wystąpienia <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="111ce-158">The second method is preferable, because it makes it easier to pass parameters to the new <xref:System.AppDomain> instance.</span></span> <span data-ttu-id="111ce-159">Metoda <xref:System.Activator.CreateInstanceFrom%2A> zapewnia dwie ważne funkcje:</span><span class="sxs-lookup"><span data-stu-id="111ce-159">The <xref:System.Activator.CreateInstanceFrom%2A> method provides two important features:</span></span>  
  
    - <span data-ttu-id="111ce-160">Możesz użyć bazy kodu, która wskazuje lokalizację, która nie zawiera Twojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="111ce-160">You can use a code base that points to a location that does not contain your assembly.</span></span>  
  
    - <span data-ttu-id="111ce-161">Tworzenie można wykonać w ramach <xref:System.Security.CodeAccessPermission.Assert%2A> dla pełnego zaufania (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), co umożliwia utworzenie wystąpienia klasy krytycznej.</span><span class="sxs-lookup"><span data-stu-id="111ce-161">You can do the creation under an <xref:System.Security.CodeAccessPermission.Assert%2A> for full-trust (<xref:System.Security.Permissions.PermissionState.Unrestricted?displayProperty=nameWithType>), which enables you to create an instance of a critical class.</span></span> <span data-ttu-id="111ce-162">(Dzieje się tak, gdy zestaw nie ma znaczników przezroczystości i jest ładowany jako w pełni zaufany). W związku z tym należy zachować ostrożność, aby utworzyć tylko kod, który ufasz tej funkcji, i zalecamy utworzenie tylko wystąpień w pełni zaufanych klas w nowej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="111ce-162">(This happens whenever your assembly has no transparency markings and is loaded as fully trusted.) Therefore, you have to be careful to create only code that you trust with this function, and we recommend that you create only instances of fully trusted classes in the new application domain.</span></span>  
  
    ```csharp
    ObjectHandle handle = Activator.CreateInstanceFrom(  
    newDomain, typeof(Sandboxer).Assembly.ManifestModule.FullyQualifiedName,  
           typeof(Sandboxer).FullName );  
    ```  
  
     <span data-ttu-id="111ce-163">Należy pamiętać, że w celu utworzenia wystąpienia klasy w nowej domenie Klasa musi zwiększyć klasę <xref:System.MarshalByRefObject></span><span class="sxs-lookup"><span data-stu-id="111ce-163">Note that in order to create an instance of a class in a new domain, the class has to extend the <xref:System.MarshalByRefObject> class</span></span>  
  
    ```csharp
    class Sandboxer:MarshalByRefObject  
    ```  
  
6. <span data-ttu-id="111ce-164">Odpakuj nowe wystąpienie domeny do odwołania w tej domenie.</span><span class="sxs-lookup"><span data-stu-id="111ce-164">Unwrap the new domain instance into a reference in this domain.</span></span> <span data-ttu-id="111ce-165">To odwołanie służy do wykonywania niezaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="111ce-165">This reference is used to execute the untrusted code.</span></span>  
  
    ```csharp
    Sandboxer newDomainInstance = (Sandboxer) handle.Unwrap();  
    ```  
  
7. <span data-ttu-id="111ce-166">Wywołaj metodę `ExecuteUntrustedCode` w wystąpieniu klasy `Sandboxer`, która została właśnie utworzona.</span><span class="sxs-lookup"><span data-stu-id="111ce-166">Call the `ExecuteUntrustedCode` method in the instance of the `Sandboxer` class you just created.</span></span>  
  
    ```csharp
    newDomainInstance.ExecuteUntrustedCode(untrustedAssembly, untrustedClass, entryPoint, parameters);  
    ```  
  
     <span data-ttu-id="111ce-167">To wywołanie jest wykonywane w domenie aplikacji w trybie piaskownicy, która ma ograniczone uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="111ce-167">This call is executed in the sandboxed application domain, which has restricted permissions.</span></span>  
  
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
  
     <span data-ttu-id="111ce-168"><xref:System.Reflection> służy do uzyskania dojścia metody w częściowo zaufanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="111ce-168"><xref:System.Reflection> is used to get a handle of a method in the partially trusted assembly.</span></span> <span data-ttu-id="111ce-169">Uchwyt może służyć do wykonywania kodu w bezpieczny sposób z minimalnymi uprawnieniami.</span><span class="sxs-lookup"><span data-stu-id="111ce-169">The handle can be used to execute code in a safe way with minimum permissions.</span></span>  
  
     <span data-ttu-id="111ce-170">Przed przystąpieniem do drukowania <xref:System.Security.SecurityException>w poprzednim kodzie Zwróć uwagę na <xref:System.Security.PermissionSet.Assert%2A> uprawnienia pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="111ce-170">In the previous code, note the <xref:System.Security.PermissionSet.Assert%2A> for the full-trust permission before printing the <xref:System.Security.SecurityException>.</span></span>  
  
    ```csharp
    new PermissionSet(PermissionState.Unrestricted).Assert()  
    ```  
  
     <span data-ttu-id="111ce-171">Potwierdzenie pełnego zaufania służy do uzyskiwania rozszerzonych informacji z <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="111ce-171">The full-trust assert is used to obtain extended information from the <xref:System.Security.SecurityException>.</span></span> <span data-ttu-id="111ce-172">Bez <xref:System.Security.PermissionSet.Assert%2A>Metoda <xref:System.Security.SecurityException.ToString%2A> <xref:System.Security.SecurityException> wykrywa, że na stosie znajduje się częściowo zaufany kod i ograniczy zwrócone informacje.</span><span class="sxs-lookup"><span data-stu-id="111ce-172">Without the <xref:System.Security.PermissionSet.Assert%2A>, the <xref:System.Security.SecurityException.ToString%2A> method of <xref:System.Security.SecurityException> will discover that there is partially trusted code on the stack and will restrict the information returned.</span></span> <span data-ttu-id="111ce-173">Może to spowodować problemy z bezpieczeństwem, jeśli kod częściowego zaufania może odczytać te informacje, ale ryzyko to nie jest przyznawane <xref:System.Security.Permissions.UIPermission>.</span><span class="sxs-lookup"><span data-stu-id="111ce-173">This could cause security issues if the partial-trust code could read that information, but the risk is mitigated by not granting <xref:System.Security.Permissions.UIPermission>.</span></span> <span data-ttu-id="111ce-174">Potwierdzenie pełnego zaufania powinno być używane oszczędnie i tylko wtedy, gdy masz pewność, że nie zezwolisz na podniesienie poziomu kodu zaufania do pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="111ce-174">The full-trust assert should be used sparingly and only when you are sure that you are not allowing partial-trust code to elevate to full trust.</span></span> <span data-ttu-id="111ce-175">Zgodnie z regułą nie należy wywoływać kodu, który nie jest zaufany w tej samej funkcji, i po wywołaniu potwierdzenia pełnego zaufania.</span><span class="sxs-lookup"><span data-stu-id="111ce-175">As a rule, do not call code you do not trust in the same function and after you called an assert for full trust.</span></span> <span data-ttu-id="111ce-176">Dobrym sposobem jest zawsze przywrócenie potwierdzenia po zakończeniu korzystania z niego.</span><span class="sxs-lookup"><span data-stu-id="111ce-176">It is good practice to always revert the assert when you have finished using it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="111ce-177">Przykład</span><span class="sxs-lookup"><span data-stu-id="111ce-177">Example</span></span>  
 <span data-ttu-id="111ce-178">Poniższy przykład implementuje procedurę opisaną w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="111ce-178">The following example implements the procedure in the previous section.</span></span> <span data-ttu-id="111ce-179">W przykładzie projekt o nazwie `Sandboxer` w rozwiązaniu programu Visual Studio zawiera również projekt o nazwie `UntrustedCode`, który implementuje klasę `UntrustedClass`.</span><span class="sxs-lookup"><span data-stu-id="111ce-179">In the example, a project named `Sandboxer` in a Visual Studio solution also contains a project named `UntrustedCode`, which implements the class `UntrustedClass`.</span></span> <span data-ttu-id="111ce-180">W tym scenariuszu przyjęto założenie, że pobrano zestaw biblioteczny zawierający metodę, która powinna zwracać `true` lub `false`, aby wskazać, czy podany numer jest numerem Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="111ce-180">This scenario assumes that you have downloaded a library assembly containing a method that is expected to return `true` or `false` to indicate whether the number you provided is a Fibonacci number.</span></span> <span data-ttu-id="111ce-181">Zamiast tego Metoda próbuje odczytać plik z komputera.</span><span class="sxs-lookup"><span data-stu-id="111ce-181">Instead, the method attempts to read a file from your computer.</span></span> <span data-ttu-id="111ce-182">Poniższy przykład pokazuje kod niezaufany.</span><span class="sxs-lookup"><span data-stu-id="111ce-182">The following example shows the untrusted code.</span></span>  
  
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
  
 <span data-ttu-id="111ce-183">W poniższym przykładzie pokazano kod aplikacji `Sandboxer`, który wykonuje kod niezaufany.</span><span class="sxs-lookup"><span data-stu-id="111ce-183">The following example shows the `Sandboxer` application code that executes the untrusted code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="111ce-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="111ce-184">See also</span></span>

- [<span data-ttu-id="111ce-185">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="111ce-185">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
