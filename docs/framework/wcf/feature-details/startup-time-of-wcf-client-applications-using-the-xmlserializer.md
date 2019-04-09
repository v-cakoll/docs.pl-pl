---
title: 'Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: dfc3dc8247a25442511d422192fea4f49bee5d92
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169809"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="dc504-102">Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="dc504-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="dc504-103">Usługi i aplikacje klienckie, które używają typów danych, które są możliwe do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilowanie kodu serializacji dla tych typów danych w czasie wykonywania, co może skutkować wydajności uruchamiania powolne.</span><span class="sxs-lookup"><span data-stu-id="dc504-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc504-104">Serializacja wstępnie wygenerowanego kodu należy używać tylko w aplikacjach klienckich, a nie w usługach.</span><span class="sxs-lookup"><span data-stu-id="dc504-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="dc504-105">[Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji, generowania kodu serializacji niezbędne z skompilowanych zestawów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc504-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="dc504-106">Svcutil.exe generuje kod serializacji dla wszystkich typów danych używane w kontraktach usług w zestawie skompilowanej aplikacji, który może być Zserializowany za pomocą <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc504-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="dc504-107">Kontrakty usługi i operacji, korzystających z <xref:System.Xml.Serialization.XmlSerializer> są oznaczone <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dc504-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="dc504-108">Do generowania kodu serializacji elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="dc504-108">To generate XmlSerializer serialization code</span></span>  
  
1.  <span data-ttu-id="dc504-109">Skompilować kod usługi lub klienta do jednego lub więcej zestawów.</span><span class="sxs-lookup"><span data-stu-id="dc504-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2.  <span data-ttu-id="dc504-110">Otwórz wiersz polecenia zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="dc504-110">Open an SDK command prompt.</span></span>  
  
3.  <span data-ttu-id="dc504-111">W wierszu polecenia Uruchom narzędzia Svcutil.exe w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="dc504-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="dc504-112">`assemblyPath` Argument określa ścieżkę do zestawu, który zawiera typy kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="dc504-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="dc504-113">Svcutil.exe generuje kod serializacji dla wszystkich typów danych używane w kontraktach usług w zestawie skompilowanej aplikacji, który może być Zserializowany za pomocą <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc504-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="dc504-114">Svcutil.exe może generować jedynie C# kodu serializacji.</span><span class="sxs-lookup"><span data-stu-id="dc504-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="dc504-115">Jeden plik kodu źródłowego jest generowany dla każdego zestawu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="dc504-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="dc504-116">Nie można użyć **/language** przełącznik, aby zmienić język generowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="dc504-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="dc504-117">Aby określić ścieżkę do zestawów zależnych, użyj **/reference** opcji.</span><span class="sxs-lookup"><span data-stu-id="dc504-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4.  <span data-ttu-id="dc504-118">Udostępnij kodu wygenerowanego serializacji do aplikacji przy użyciu jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="dc504-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="dc504-119">Kompilowanie kodu wygenerowanego serializacji w osobnym zestawie o nazwie [*oryginalny zestaw*]. XmlSerializers.dll (na przykład MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="dc504-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="dc504-120">Aplikacja musi umożliwiać można załadować zestawu, który musi być podpisany przy użyciu tego samego klucza jako oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="dc504-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="dc504-121">Jeśli oryginalny zestaw zostanie ponownie skompilowany, należy ponownie wygenerować zestawu serializacji.</span><span class="sxs-lookup"><span data-stu-id="dc504-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="dc504-122">Kompilowanie kodu wygenerowanego serializacji w osobnym zestawie i użyj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> na kontrakt usługi, która używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dc504-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="dc504-123">Ustaw <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości, aby wskazywał zestawu skompilowanego serializacji.</span><span class="sxs-lookup"><span data-stu-id="dc504-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="dc504-124">Kompilowanie kodu wygenerowanego serializacji do swojego zestawu aplikacji i Dodaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> umową serwisową, który używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="dc504-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="dc504-125">Nie należy ustawiać <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="dc504-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="dc504-126">Domyślny zestaw serializacji zakłada się, że bieżący zestaw.</span><span class="sxs-lookup"><span data-stu-id="dc504-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="dc504-127">Do generowania kodu serializacji elementu XmlSerializer w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dc504-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1.  <span data-ttu-id="dc504-128">Tworzenie usługi i klienta WCF projektów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc504-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="dc504-129">Następnie dodaj odwołanie do usługi do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="dc504-129">Then, add a service reference to the client project.</span></span>  
  
2.  <span data-ttu-id="dc504-130">Dodaj <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi *reference.cs* pliku w projekcie aplikacji klienckich, w obszarze **serviceReference** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="dc504-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="dc504-131">Należy zauważyć, że należy do wyświetlenia wszystkich plików w **Eksploratora rozwiązań** aby te pliki.</span><span class="sxs-lookup"><span data-stu-id="dc504-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3.  <span data-ttu-id="dc504-132">Tworzenie aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="dc504-132">Build the client app.</span></span>  
  
4.  <span data-ttu-id="dc504-133">Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia wstępnie wygenerowanego serializatora *.cs* pliku przy użyciu polecenia:</span><span class="sxs-lookup"><span data-stu-id="dc504-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="dc504-134">Argument Ścieżkazestawu Określa ścieżkę do zestawu klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="dc504-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="dc504-135">Przykład:</span><span class="sxs-lookup"><span data-stu-id="dc504-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="dc504-136">*WCFClient.XmlSerializers.dll.cs* zostanie wygenerowany plik.</span><span class="sxs-lookup"><span data-stu-id="dc504-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5.  <span data-ttu-id="dc504-137">Skompiluj zestaw wstępnie wygenerowanego serializacji.</span><span class="sxs-lookup"><span data-stu-id="dc504-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="dc504-138">Na podstawie przykładu w poprzednim kroku, polecenie compile będzie następująca:</span><span class="sxs-lookup"><span data-stu-id="dc504-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="dc504-139">Sprawdź wygenerowany *WCFClient.XmlSerializers.dll* znajduje się w tym samym katalogu co aplikacja klienta, która jest *WCFClient.exe* w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="dc504-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6.  <span data-ttu-id="dc504-140">Uruchom aplikację kliencką w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="dc504-140">Run the client app as usual.</span></span> <span data-ttu-id="dc504-141">Zestaw serializacji wstępnie wygenerowanego będą używane.</span><span class="sxs-lookup"><span data-stu-id="dc504-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc504-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc504-142">Example</span></span>  
 <span data-ttu-id="dc504-143">Następujące polecenie generuje typy serializacji dla `XmlSerializer` typy, które każda usługa umów z użyciem zestawu.</span><span class="sxs-lookup"><span data-stu-id="dc504-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc504-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc504-144">See also</span></span>

- [<span data-ttu-id="dc504-145">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="dc504-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
