---
title: 'Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: d14facf435d575b9db5129b732938658c921f97f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934316"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="9726a-102">Instrukcje: rejestrowanie i konfigurowanie krótkiej nazwy usługi</span><span class="sxs-lookup"><span data-stu-id="9726a-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="9726a-103">Przed użyciem monikera usługi Windows Communication Foundation (WCF) w ramach aplikacji COM z umową z określonym typem, należy zarejestrować wymagane typy z atrybutami COM i skonfigurować aplikację COM oraz moniker z wymaganym powiązaniem skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="9726a-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="9726a-104">Aby zarejestrować wymagane typy atrybutów z modelem COM</span><span class="sxs-lookup"><span data-stu-id="9726a-104">To register the required attributed types with COM</span></span>  
  
1. <span data-ttu-id="9726a-105">Użyj narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , aby pobrać kontrakt metadanych z usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="9726a-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="9726a-106">Spowoduje to wygenerowanie kodu źródłowego dla zestawu klienta WCF i pliku konfiguracji aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="9726a-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2. <span data-ttu-id="9726a-107">Upewnij się, że typy w zestawie są oznaczone jako `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="9726a-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="9726a-108">Aby to zrobić, Dodaj następujący atrybut do pliku AssemblyInfo.cs w projekcie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9726a-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3. <span data-ttu-id="9726a-109">Kompiluj zarządzany klient WCF jako zestaw o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="9726a-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="9726a-110">Wymaga to podpisania za pomocą pary kluczy kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="9726a-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="9726a-111">Aby uzyskać więcej informacji, zobacz Podpisywanie [zestawu za pomocą silnej nazwy](https://go.microsoft.com/fwlink/?LinkId=94874) w przewodniku dewelopera platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9726a-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4. <span data-ttu-id="9726a-112">Użyj narzędzia rejestracji zestawu (Regasm. exe) z `/tlb` opcją zarejestrowania typów w zestawie przy użyciu modelu com.</span><span class="sxs-lookup"><span data-stu-id="9726a-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5. <span data-ttu-id="9726a-113">Użyj narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe), aby dodać zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9726a-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9726a-114">Podpisywanie zestawu i dodawanie go do globalnej pamięci podręcznej zestawów to kroki opcjonalne, ale mogą uprościć proces ładowania zestawu z właściwej lokalizacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9726a-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="9726a-115">Aby skonfigurować aplikację COM i moniker z wymaganą konfiguracją powiązania</span><span class="sxs-lookup"><span data-stu-id="9726a-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
- <span data-ttu-id="9726a-116">Umieść definicje powiązań (wygenerowane przez [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w pliku konfiguracyjnym wygenerowanej aplikacji klienta) w pliku konfiguracyjnym aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="9726a-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="9726a-117">Na przykład w przypadku pliku wykonywalnego Visual Basic 6,0 o nazwie CallCenterClient. exe Konfiguracja powinna zostać umieszczona w pliku o nazwie CallCenterConfig. exe. config w tym samym katalogu, w którym znajduje się plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="9726a-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="9726a-118">Aplikacja kliencka może teraz używać monikera.</span><span class="sxs-lookup"><span data-stu-id="9726a-118">The client application can now use the moniker.</span></span> <span data-ttu-id="9726a-119">Należy pamiętać, że konfiguracja powiązania nie jest wymagana, jeśli używany jest jeden ze standardowych typów powiązań dostarczonych przez program WCF.</span><span class="sxs-lookup"><span data-stu-id="9726a-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="9726a-120">Następujący typ jest zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="9726a-120">The following type is registered.</span></span>  
  
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
  
     <span data-ttu-id="9726a-121">Aplikacja zostanie udostępniona przy użyciu `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="9726a-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="9726a-122">W przypadku danego typu i konfiguracji aplikacji używane są następujące przykładowe ciągi monikera.</span><span class="sxs-lookup"><span data-stu-id="9726a-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="9726a-123">Można użyć dowolnego z tych ciągów monikera z poziomu aplikacji Visual Basic 6,0, po dodaniu odwołania do zestawu zawierającego `IMathService` typy, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9726a-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="9726a-124">W tym przykładzie Definicja konfiguracji `Binding1` powiązania jest przechowywana w pliku konfiguracyjnym o odpowiednich nazwach dla aplikacji klienckiej, takiej jak vb6appname. exe. config.</span><span class="sxs-lookup"><span data-stu-id="9726a-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9726a-125">Możesz użyć podobnego kodu w C#, a C++lub dowolnej innej aplikacji języka .NET.</span><span class="sxs-lookup"><span data-stu-id="9726a-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9726a-126">: Jeśli moniker jest źle sformułowany lub usługa jest niedostępna, wywołanie do `GetObject` zwraca błąd "Nieprawidłowa składnia".</span><span class="sxs-lookup"><span data-stu-id="9726a-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="9726a-127">Jeśli wystąpi ten błąd, upewnij się, że moniker, którego używasz, jest poprawna i że usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="9726a-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="9726a-128">Chociaż ten temat koncentruje się na używaniu monikera usługi w kodzie VB 6,0, można użyć monikera usługi z innych języków.</span><span class="sxs-lookup"><span data-stu-id="9726a-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="9726a-129">W przypadku używania monikera C++ z kodu, zestaw wygenerowany przez Svcutil. exe powinien zostać zaimportowany za pomocą polecenia "no_namespace named_guids raw_interfaces_only", jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9726a-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="9726a-130">Powoduje to modyfikację zaimportowanych definicji interfejsu, tak aby `HResult`wszystkie metody zwracały.</span><span class="sxs-lookup"><span data-stu-id="9726a-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="9726a-131">Wszystkie inne zwracane wartości są konwertowane na parametry out.</span><span class="sxs-lookup"><span data-stu-id="9726a-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="9726a-132">Ogólne wykonywanie metod pozostaje bez zmian.</span><span class="sxs-lookup"><span data-stu-id="9726a-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="9726a-133">Pozwala to określić przyczynę wyjątku podczas wywoływania metody na serwerze proxy.</span><span class="sxs-lookup"><span data-stu-id="9726a-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="9726a-134">Ta funkcja jest dostępna tylko w C++ kodzie.</span><span class="sxs-lookup"><span data-stu-id="9726a-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9726a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9726a-135">See also</span></span>

- [<span data-ttu-id="9726a-136">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="9726a-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
