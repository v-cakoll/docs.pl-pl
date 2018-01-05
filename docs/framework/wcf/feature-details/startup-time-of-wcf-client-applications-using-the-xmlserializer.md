---
title: "Instrukcje: Skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2ac51a99db002633aaf80070d8820ce6e3144a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="f4084-102">Instrukcje: Skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f4084-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="f4084-103">Usługi i aplikacje klienckie, które używają typów danych, które są do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilacja kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować wolne uruchamiania wydajności.</span><span class="sxs-lookup"><span data-stu-id="f4084-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f4084-104">Kod serializacji wstępnie wygenerowane można tylko w aplikacjach klienckich, a nie w usługach.</span><span class="sxs-lookup"><span data-stu-id="f4084-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="f4084-105">[Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji przez generowania kodu serializacji niezbędne z skompilowane zestawy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4084-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="f4084-106">Svcutil.exe generuje kodu serializacji dla wszystkich typów danych używany w kontraktach usług w zestawie skompilowanej aplikacji, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f4084-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f4084-107">Kontrakty usługi i działania, korzystających z <xref:System.Xml.Serialization.XmlSerializer> są oznaczone ikoną z <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f4084-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="f4084-108">Do generowania kodu serializacji XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="f4084-108">To generate XmlSerializer serialization code</span></span>  
  
1.  <span data-ttu-id="f4084-109">Kompilowanie kodu usługi lub klienta do jednego lub więcej zestawów.</span><span class="sxs-lookup"><span data-stu-id="f4084-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2.  <span data-ttu-id="f4084-110">Otwórz wiersz polecenia z zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="f4084-110">Open an SDK command prompt.</span></span>  
  
3.  <span data-ttu-id="f4084-111">W wierszu polecenia Uruchom narzędzie Svcutil.exe w następującym formacie.</span><span class="sxs-lookup"><span data-stu-id="f4084-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="f4084-112">`assemblyPath` Argument określa ścieżkę do zestawu, który zawiera typy kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f4084-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="f4084-113">Svcutil.exe generuje kodu serializacji dla wszystkich typów danych używany w kontraktach usług w zestawie skompilowanej aplikacji, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f4084-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="f4084-114">Svcutil.exe tylko można wygenerować kodu serializacji C#.</span><span class="sxs-lookup"><span data-stu-id="f4084-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="f4084-115">Jeden plik kod źródłowy jest generowany dla każdego zestawu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="f4084-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="f4084-116">Nie można użyć **/language** przełącznik, aby zmienić język wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f4084-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="f4084-117">Aby określić ścieżkę do zestawów zależnych, użyj **/reference** opcji.</span><span class="sxs-lookup"><span data-stu-id="f4084-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4.  <span data-ttu-id="f4084-118">Udostępnij serializacji wygenerowany kod aplikacji przy użyciu jednej z następujących opcji:</span><span class="sxs-lookup"><span data-stu-id="f4084-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1.  <span data-ttu-id="f4084-119">Skompilować kodu serializacji wygenerowanego w osobny zestaw o nazwie [*oryginalnego zestawu*]. XmlSerializers.dll (na przykład MyApp.XmlSerializers.dll).</span><span class="sxs-lookup"><span data-stu-id="f4084-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="f4084-120">Aplikacja musi być można załadować zestawu, które muszą być podpisane przy użyciu tego samego klucza oryginalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f4084-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="f4084-121">Skompiluj oryginalnego zestawu, musisz ponownie wygenerować zestawu serializacji.</span><span class="sxs-lookup"><span data-stu-id="f4084-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2.  <span data-ttu-id="f4084-122">Skompilować kodu serializacji wygenerowanego w osobny zestaw i użyj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> umowy serwisowej, która używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f4084-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="f4084-123">Ustaw <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości, aby wskazywał zestawu skompilowanego serializacji.</span><span class="sxs-lookup"><span data-stu-id="f4084-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3.  <span data-ttu-id="f4084-124">Skompilować kodu serializacji wygenerowanego do używanego zestawu aplikacji i Dodaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> do umowy serwisowej, która używa <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f4084-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="f4084-125">Nie ustawiaj <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> lub <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4084-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="f4084-126">Domyślny zestaw serializacji zakłada się, że bieżący zestaw.</span><span class="sxs-lookup"><span data-stu-id="f4084-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="f4084-127">Do generowania kodu serializacji XmlSerializer w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f4084-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1.  <span data-ttu-id="f4084-128">Tworzenie usługi WCF i klienta projektów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f4084-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="f4084-129">Następnie należy dodać odwołania do usługi do projektu klienta.</span><span class="sxs-lookup"><span data-stu-id="f4084-129">Then, add a service reference to the client project.</span></span>  
  
2.  <span data-ttu-id="f4084-130">Dodaj <xref:System.ServiceModel.XmlSerializerFormatAttribute> w kontrakcie usługi *reference.cs* plik w projekcie aplikacji klienta, w obszarze **servicereference kierowany** -> **reference.svcmap** .</span><span class="sxs-lookup"><span data-stu-id="f4084-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="f4084-131">Należy pamiętać, że trzeba Pokaż wszystkie pliki w **Eksploratora rozwiązań** aby te pliki.</span><span class="sxs-lookup"><span data-stu-id="f4084-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3.  <span data-ttu-id="f4084-132">Tworzenie aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="f4084-132">Build the client app.</span></span>  
  
4.  <span data-ttu-id="f4084-133">Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do utworzenia wstępnie wygenerowanego serializatora *.cs* pliku za pomocą polecenia:</span><span class="sxs-lookup"><span data-stu-id="f4084-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="f4084-134">Argument zestawu assemblyPath Określa ścieżkę do zestawu klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="f4084-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="f4084-135">Takie jak:</span><span class="sxs-lookup"><span data-stu-id="f4084-135">Such as:</span></span>  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="f4084-136">*WCFClient.XmlSerializers.dll.cs* zostanie utworzony plik.</span><span class="sxs-lookup"><span data-stu-id="f4084-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5.  <span data-ttu-id="f4084-137">Kompilowanie zestawu wstępnie wygenerowane serializacji.</span><span class="sxs-lookup"><span data-stu-id="f4084-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="f4084-138">Oparte na przykład w poprzednim kroku, kompilacji polecenie będzie następujące:</span><span class="sxs-lookup"><span data-stu-id="f4084-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="f4084-139">Sprawdź wygenerowany *WCFClient.XmlSerializers.dll* znajduje się w tym samym katalogu co aplikacja klienta, który jest *WCFClient.exe* w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="f4084-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6.  <span data-ttu-id="f4084-140">Uruchom aplikację klienta w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="f4084-140">Run the client app as usual.</span></span> <span data-ttu-id="f4084-141">Zestaw wstępnie wygenerowane serializacji będą używane.</span><span class="sxs-lookup"><span data-stu-id="f4084-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4084-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4084-142">Example</span></span>  
 <span data-ttu-id="f4084-143">Polecenie generuje typy serializacji dla `XmlSerializer` typów, które usługi umów w przypadku użycia zestawu.</span><span class="sxs-lookup"><span data-stu-id="f4084-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4084-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4084-144">See Also</span></span>  
 [<span data-ttu-id="f4084-145">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="f4084-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
