---
title: 'Instrukcje: Skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: ca15d710a30586135f0d030e155b09b63a22ee45
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976062"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="0d606-102">Instrukcje: Skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="0d606-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="0d606-103">Usługi i aplikacje klienckie korzystające z typów danych, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer> generowanie i kompilowanie kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować spowolnienie wydajności.</span><span class="sxs-lookup"><span data-stu-id="0d606-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d606-104">Wstępnie wygenerowany kod serializacji może być używany tylko w aplikacjach klienckich, a nie w usługach.</span><span class="sxs-lookup"><span data-stu-id="0d606-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="0d606-105">[Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może zwiększyć wydajność uruchamiania tych aplikacji, generując wymagany kod serializacji z skompilowanych zestawów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d606-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="0d606-106">Svcutil. exe generuje kod serializacji dla wszystkich typów danych używanych w kontraktach usług w skompilowanym zestawie aplikacji, które mogą być serializowane przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0d606-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0d606-107">Kontrakty usługi i operacji, które używają <xref:System.Xml.Serialization.XmlSerializer> są oznaczone <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0d606-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="0d606-108">Aby wygenerować kod serializacji XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="0d606-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="0d606-109">Skompiluj kod usługi lub klienta w jednym lub kilku zestawach.</span><span class="sxs-lookup"><span data-stu-id="0d606-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="0d606-110">Otwórz wiersz polecenia zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="0d606-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="0d606-111">W wierszu polecenia Uruchom narzędzie Svcutil. exe, używając następującego formatu.</span><span class="sxs-lookup"><span data-stu-id="0d606-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="0d606-112">`assemblyPath` argument określa ścieżkę do zestawu, który zawiera typy kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="0d606-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="0d606-113">Svcutil. exe generuje kod serializacji dla wszystkich typów danych używanych w kontraktach usług w skompilowanym zestawie aplikacji, które mogą być serializowane przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0d606-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="0d606-114">Svcutil. exe może generować C# tylko kod serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d606-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="0d606-115">Dla każdego zestawu wejściowego jest generowany jeden plik kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0d606-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="0d606-116">Nie można użyć przełącznika **/Language** , aby zmienić język wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="0d606-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="0d606-117">Aby określić ścieżkę do zestawów zależnych, użyj opcji **/Reference** .</span><span class="sxs-lookup"><span data-stu-id="0d606-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="0d606-118">Udostępnij wygenerowany kod serializacji aplikacji przy użyciu jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="0d606-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="0d606-119">Kompiluj wygenerowany kod serializacji w osobnym zestawie o nazwie [*oryginalny zestaw*]. XmlSerializers. dll (na przykład MojaApl. XmlSerializers. dll).</span><span class="sxs-lookup"><span data-stu-id="0d606-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="0d606-120">Aplikacja musi być w stanie załadować zestaw, który musi być podpisany przy użyciu tego samego klucza co oryginalny zestaw.</span><span class="sxs-lookup"><span data-stu-id="0d606-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="0d606-121">W przypadku ponownej kompilacji oryginalnego zestawu należy ponownie wygenerować zestaw serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d606-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="0d606-122">Skompiluj wygenerowany kod serializacji do oddzielnego zestawu i użyj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> w kontrakcie usługi używającym <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0d606-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="0d606-123">Ustaw właściwości <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> w taki sposób, aby wskazywały skompilowany zestaw serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d606-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="0d606-124">Skompiluj wygenerowany kod serializacji do zestawu aplikacji i Dodaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> do kontraktu usługi korzystającego z <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0d606-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="0d606-125">Nie ustawiaj właściwości <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ani <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d606-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="0d606-126">Przyjęto, że domyślny zestaw serializacji jest bieżącym zestawem.</span><span class="sxs-lookup"><span data-stu-id="0d606-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="0d606-127">Aby wygenerować kod serializacji XmlSerializer w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d606-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="0d606-128">Utwórz usługę WCF i projekty klienta w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d606-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="0d606-129">Następnie Dodaj odwołanie do usługi do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="0d606-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="0d606-130">Dodaj <xref:System.ServiceModel.XmlSerializerFormatAttribute> do kontraktu usługi w pliku *Reference.cs* w projekcie aplikacji klienta w obszarze **ServiceReference** -> **Reference. svcmap**.</span><span class="sxs-lookup"><span data-stu-id="0d606-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="0d606-131">Zwróć uwagę, że musisz wyświetlić wszystkie pliki w **Eksplorator rozwiązań** , aby wyświetlić te pliki.</span><span class="sxs-lookup"><span data-stu-id="0d606-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="0d606-132">Utwórz aplikację kliencką.</span><span class="sxs-lookup"><span data-stu-id="0d606-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="0d606-133">Użyj [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , aby utworzyć wstępnie wygenerowany plik serializator *. cs* przy użyciu polecenia:</span><span class="sxs-lookup"><span data-stu-id="0d606-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="0d606-134">Argument assemblyPath określa ścieżkę do zestawu klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="0d606-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="0d606-135">Takie jak:</span><span class="sxs-lookup"><span data-stu-id="0d606-135">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="0d606-136">Plik *WCFClient.XmlSerializers.dll.cs* zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="0d606-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="0d606-137">Kompiluj wstępnie wygenerowany zestaw serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d606-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="0d606-138">Na podstawie przykładu w poprzednim kroku polecenie Kompiluj będzie następujące:</span><span class="sxs-lookup"><span data-stu-id="0d606-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="0d606-139">Upewnij się, że wygenerowane *WCFClient. XmlSerializers. dll* znajduje się w tym samym katalogu, w którym znajduje się aplikacja kliencka, w tym przypadku *WCFClient. exe* .</span><span class="sxs-lookup"><span data-stu-id="0d606-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="0d606-140">Uruchom aplikację kliencką w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="0d606-140">Run the client app as usual.</span></span> <span data-ttu-id="0d606-141">Zostanie użyty wstępnie wygenerowany zestaw serializacji.</span><span class="sxs-lookup"><span data-stu-id="0d606-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d606-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d606-142">Example</span></span>  
 <span data-ttu-id="0d606-143">Następujące polecenie generuje typy serializacji dla `XmlSerializer` typów, które są używane przez wszystkie kontrakty usługi w zestawie.</span><span class="sxs-lookup"><span data-stu-id="0d606-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d606-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d606-144">See also</span></span>

- [<span data-ttu-id="0d606-145">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="0d606-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
