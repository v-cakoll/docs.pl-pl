---
title: 'Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: dfac833cc7517af00d0264fc5d11fc83ae543569
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313583"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="4aa8f-102">Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi</span><span class="sxs-lookup"><span data-stu-id="4aa8f-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="4aa8f-103">Przed użyciem monikera programu Windows Communication Foundation (WCF) w ramach aplikacji modelu COM z kontrolą typów kontraktu, musisz zarejestrować wymaganych typów opartego na atrybutach z modelem COM i konfigurowanie aplikacji modelu COM i moniker z powiązaniem wymagane Konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="4aa8f-104">Aby zarejestrować wymaganych typów opartego na atrybutach z modelem COM</span><span class="sxs-lookup"><span data-stu-id="4aa8f-104">To register the required attributed types with COM</span></span>  
  
1. <span data-ttu-id="4aa8f-105">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia do pobierania metadanych kontraktu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="4aa8f-106">Spowoduje to wygenerowanie kodu źródłowego dla zestawu klienta WCF i pliku konfiguracji aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2. <span data-ttu-id="4aa8f-107">Upewnij się, że typy w zestawie są oznaczone jako `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="4aa8f-108">Aby to zrobić, Dodaj następujący atrybut w pliku AssemblyInfo.cs w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3. <span data-ttu-id="4aa8f-109">Skompiluj zarządzanego klienta programu WCF jako zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="4aa8f-110">Ta migracja wymaga logowania przy użyciu pary kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="4aa8f-111">Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](https://go.microsoft.com/fwlink/?LinkId=94874) w Podręczniku dewelopera programu .NET.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4. <span data-ttu-id="4aa8f-112">Narzędzie rejestracji zestawów (Regasm.exe), za pomocą `/tlb` opcję, aby można było zarejestrować typy w zestawie przy użyciu modelu COM.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5. <span data-ttu-id="4aa8f-113">Aby dodać zestaw do globalnej pamięci podręcznej, należy użyć narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe).</span><span class="sxs-lookup"><span data-stu-id="4aa8f-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4aa8f-114">Podpisywanie zestawu i dodanie go do globalnej pamięci podręcznej zestawów są opcjonalne kroki, ale upraszczają proces ładowania zestawu we właściwej lokalizacji, w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="4aa8f-115">Aby skonfigurować aplikacji modelu COM i moniker przy użyciu konfiguracji powiązania wymagane</span><span class="sxs-lookup"><span data-stu-id="4aa8f-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="4aa8f-116">Umieść definicji powiązania (generowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w pliku konfiguracyjnym aplikacji wygenerowanego klienta) w pliku konfiguracyjnym aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="4aa8f-117">Na przykład Visual Basic 6.0 pliku wykonywalnego o nazwie CallCenterClient.exe, konfiguracji powinny być umieszczane w pliku o nazwie CallCenterConfig.exe.config w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="4aa8f-118">Aplikacja kliencka można teraz używać krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-118">The client application can now use the moniker.</span></span> <span data-ttu-id="4aa8f-119">Pamiętaj, że konfiguracja powiązania nie jest wymagane, jeśli przy użyciu jednej ze standardowych powiązań typów dostarczonych przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="4aa8f-120">Następujący typ jest zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="4aa8f-121">Aplikacja jest udostępniana przy użyciu `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="4aa8f-122">Dla danego typu i konfiguracji aplikacji są używane następujące ciągi moniker przykładu.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="4aa8f-123">Można użyć dowolnego z tych ciągów krótkiej nazwy z aplikacji Visual Basic 6.0, po dodaniu odwołania do zestawu, który zawiera `IMathService` typów, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="4aa8f-124">W tym przykładzie definicji dla konfiguracji powiązania `Binding1` są przechowywane w pliku konfiguracji odpowiednio nazwanych w aplikacji klienckiej, takich jak vb6appname.exe.config.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4aa8f-125">Możesz użyć podobny kod w języku C#, C++ lub inna aplikacja języka .NET.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4aa8f-126">: Jeśli moniker jest źle sformułowany lub jeśli usługa jest niedostępna, wywołanie `GetObject` zwraca błąd "Nieprawidłowa składnia".</span><span class="sxs-lookup"><span data-stu-id="4aa8f-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="4aa8f-127">Jeśli zostanie wyświetlony ten błąd, upewnij się, moniker elementu, którego używasz jest poprawna i ta usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="4aa8f-128">Chociaż ten temat koncentruje się na temat korzystania z kodu VB 6.0 monikera programu, można użyć krótkiej nazwy z innych języków.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="4aa8f-129">Korzystając z monikerem z C++ kodu Svcutil.exe wygenerowanego zestawu powinny być importowane z "no_namespace named_guids — raw_interfaces_only —", jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="4aa8f-130">Modyfikuje definicje interfejsu importowanych, tak, aby zwrócić wszystkie metody `HResult`.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="4aa8f-131">Zwracane wartości są konwertowane na parametrów out.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="4aa8f-132">Ogólny wykonywanie metody pozostaje taka sama.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="4aa8f-133">Dzięki temu można ustalić przyczynę Wystąpił wyjątek podczas wywoływania metody na serwerze proxy.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="4aa8f-134">Ta funkcja jest dostępna tylko w kodzie języka C++.</span><span class="sxs-lookup"><span data-stu-id="4aa8f-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa8f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4aa8f-135">See also</span></span>

- [<span data-ttu-id="4aa8f-136">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="4aa8f-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
