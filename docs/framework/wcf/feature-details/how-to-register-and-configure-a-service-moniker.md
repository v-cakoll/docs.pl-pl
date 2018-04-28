---
title: 'Porady: zarejestrować i skonfigurować krótkiej nazwy'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52b3ec27560ca2dc47b7951cb209f33f307fa7ea
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="64f34-102">Porady: zarejestrować i skonfigurować krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="64f34-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="64f34-103">Przed użyciem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] krótkiej nazwy w aplikacji modelu COM z typu kontraktu, musisz zarejestrować wymagane typy oparte na atrybutach w modelu COM i skonfigurować za pomocą konfiguracji powiązania wymaganych aplikacji modelu COM i krótka nazwa.</span><span class="sxs-lookup"><span data-stu-id="64f34-103">Before using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="64f34-104">Aby zarejestrować wymagane typy oparte na atrybutach w modelu COM</span><span class="sxs-lookup"><span data-stu-id="64f34-104">To register the required attributed types with COM</span></span>  
  
1.  <span data-ttu-id="64f34-105">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia do pobierania metadanych umowy z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="64f34-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="64f34-106">Generuje kod źródłowy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zestaw klienta i pliku konfiguracji aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="64f34-106">This generates the source code for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly and a client application configuration file.</span></span>  
  
2.  <span data-ttu-id="64f34-107">Upewnij się, że typy w zestawie są oznaczone jako `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="64f34-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="64f34-108">Aby to zrobić, Dodaj następujący atrybut w pliku AssemblyInfo.cs w projektu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64f34-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3.  <span data-ttu-id="64f34-109">Kompiluj zarządzanej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta jako zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="64f34-109">Compile the managed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client as a strong-named assembly.</span></span> <span data-ttu-id="64f34-110">Wymaga podpisywania za pomocą klucza kryptograficznego.</span><span class="sxs-lookup"><span data-stu-id="64f34-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="64f34-111">Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu o silnej nazwie](http://go.microsoft.com/fwlink/?LinkId=94874) w Podręczniku dewelopera programu .NET.</span><span class="sxs-lookup"><span data-stu-id="64f34-111">For more information, see [Signing an Assembly with a Strong Name](http://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4.  <span data-ttu-id="64f34-112">Użyj narzędzia do rejestrowania zestawów (Regasm.exe) z `/tlb` możliwość zarejestrowania typów w zestawie z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="64f34-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5.  <span data-ttu-id="64f34-113">Narzędzie Global Assembly Cache (Gacutil.exe) można dodać zestawu do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="64f34-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64f34-114">Podpisywanie zestawu i dodanie go do globalnej pamięci podręcznej zestawów są opcjonalne kroki, ale ich uprościć proces ładowania zestawu we właściwej lokalizacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="64f34-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="64f34-115">Aby skonfigurować za pomocą konfiguracji powiązania wymaganych aplikacji modelu COM i krótka nazwa</span><span class="sxs-lookup"><span data-stu-id="64f34-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
-   <span data-ttu-id="64f34-116">Umieść definicje powiązania (generowane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) w pliku konfiguracyjnym aplikacji wygenerowanego klienta) w pliku konfiguracyjnym aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="64f34-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="64f34-117">Na przykład dla programu Visual Basic 6.0 pliku wykonywalnego o nazwie CallCenterClient.exe, Konfiguracja powinna zostać umieszczona w pliku o nazwie CallCenterConfig.exe.config w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="64f34-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="64f34-118">Aplikacja kliencka można teraz używać krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="64f34-118">The client application can now use the moniker.</span></span> <span data-ttu-id="64f34-119">Należy pamiętać, że konfiguracja powiązania nie jest wymagane, jeśli przy użyciu jednej ze standardowych typów dostarczanych przez powiązanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64f34-119">Note that the binding configuration is not required if using one of the standard binding types provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
     <span data-ttu-id="64f34-120">Następujący typ jest zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="64f34-120">The following type is registered.</span></span>  
  
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
  
     <span data-ttu-id="64f34-121">Aplikacja jest uwidaczniany za pomocą `wsHttpBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="64f34-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="64f34-122">Dla danego typu i konfiguracji aplikacji są używane następujące ciągi przykład krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="64f34-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="64f34-123">Możesz użyć dowolnej z tych ciągów krótkiej nazwy z aplikacji Visual Basic 6.0, po dodaniu odwołanie do zestawu, który zawiera `IMathService` typy, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="64f34-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="64f34-124">W tym przykładzie definicji konfiguracji powiązania `Binding1` są przechowywane w pliku konfiguracji nazwanych odpowiednio do aplikacji klienckiej, takich jak vb6appname.exe.config.</span><span class="sxs-lookup"><span data-stu-id="64f34-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64f34-125">Można użyć podobny kod w C#, C++ lub innych aplikacji języka .NET.</span><span class="sxs-lookup"><span data-stu-id="64f34-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64f34-126">: Jeśli krótka nazwa jest nieprawidłowo sformułowany lub usługa jest niedostępna, wywołanie `GetObject` błędu "Nieprawidłowa składnia".</span><span class="sxs-lookup"><span data-stu-id="64f34-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="64f34-127">Jeśli zostanie wyświetlony ten błąd, upewnij się, krótkiej nazwy, którego używasz, jest poprawny i usługa jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="64f34-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="64f34-128">Chociaż ten temat koncentruje się na korzystanie z kodu VB 6.0 moniker usługi, możesz użyć krótkiej nazwy z innych języków.</span><span class="sxs-lookup"><span data-stu-id="64f34-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="64f34-129">Gdy przy użyciu krótkiej nazwy z C++ kod Svcutil.exe wygenerowany zestawu należy zaimportować z "no_namespace — named_guids — raw_interfaces_only —", jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="64f34-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="64f34-130">Modyfikuje definicje interfejsu importowane, tak, aby zwrócić wszystkie metody `HResult`.</span><span class="sxs-lookup"><span data-stu-id="64f34-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="64f34-131">Wszelkie inne wartości są konwertowane na parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="64f34-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="64f34-132">Ogólny wykonywanie metod jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="64f34-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="64f34-133">Dzięki temu można ustalić przyczynę Wystąpił wyjątek podczas wywoływania metody na serwerze proxy.</span><span class="sxs-lookup"><span data-stu-id="64f34-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="64f34-134">Ta funkcja jest dostępna tylko z kodu C++.</span><span class="sxs-lookup"><span data-stu-id="64f34-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f34-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64f34-135">See Also</span></span>  
 [<span data-ttu-id="64f34-136">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="64f34-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
