---
title: 'Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 68d651a396aa748d53f9121e9861260bdbf2dffa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="7136c-102">Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="7136c-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="7136c-103">Svcutil.exe można wyeksportować metadane dla usług, kontrakty i typów danych w zestawach skompilowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7136c-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
-   <span data-ttu-id="7136c-104">Aby wyeksportować metadane dla wszystkich skompilowany kontraktów usług dla zestawu zestawów przy użyciu Svcutil.exe, określ zestawy jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="7136c-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="7136c-105">Jest to zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="7136c-105">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="7136c-106">Aby wyeksportować metadane dla usługi skompilowanych przy użyciu Svcutil.exe, określ usługi zestawu lub zestawów jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="7136c-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="7136c-107">Należy użyć `/serviceName` możliwość wskazania nazwy konfiguracji usługi do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="7136c-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="7136c-108">Svcutil.exe automatycznie ładuje plik konfiguracji dla określonego zestawu pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="7136c-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
-   <span data-ttu-id="7136c-109">Aby wyeksportować wszystkie typy kontraktu danych w ramach zestawu zestawów, należy użyć `/dataContractOnly` opcji.</span><span class="sxs-lookup"><span data-stu-id="7136c-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7136c-110">Użyj `/reference` można określić ścieżki pliku do żadnych zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="7136c-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="7136c-111">Aby wyeksportować metadane dla skompilowanych kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="7136c-111">To export metadata for compiled service contracts</span></span>  
  
1.  <span data-ttu-id="7136c-112">Kompiluj z implementacji kontraktu usługi do co najmniej jeden libraries.1 — klasa</span><span class="sxs-lookup"><span data-stu-id="7136c-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2.  <span data-ttu-id="7136c-113">Uruchom Svcutil.exe na skompilowane zestawy.</span><span class="sxs-lookup"><span data-stu-id="7136c-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7136c-114">Być może należy użyć `/reference` przełącznik, aby określić ścieżkę pliku do żadnych zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="7136c-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="7136c-115">Aby wyeksportować metadane dla skompilowanych usługi</span><span class="sxs-lookup"><span data-stu-id="7136c-115">To export metadata for a compiled service</span></span>  
  
1.  <span data-ttu-id="7136c-116">Kompiluj implementacji usługi do pliku wykonywalnego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7136c-116">Compile your service implementation into an executable assembly.</span></span>  
  
2.  <span data-ttu-id="7136c-117">Utwórz plik konfiguracji do pliku wykonywalnego usługi i Dodaj konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="7136c-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3.  <span data-ttu-id="7136c-118">Uruchom Svcutil.exe na usługa skompilowanego pliku wykonywalnego używa `/serviceName` przełącznik, aby określić nazwę konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="7136c-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7136c-119">Być może należy użyć `/reference` przełącznik, aby określić ścieżkę pliku do żadnych zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="7136c-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="7136c-120">Aby wyeksportować metadane dla skompilowanych kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="7136c-120">To export metadata for compiled data contracts</span></span>  
  
1.  <span data-ttu-id="7136c-121">Kompiluj z implementacji kontraktu danych do jednego lub więcej bibliotek klas.</span><span class="sxs-lookup"><span data-stu-id="7136c-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2.  <span data-ttu-id="7136c-122">Uruchom Svcutil.exe na skompilowane zestawy za pomocą `/dataContract` przełącznika dla kontraktów danych powinny być generowane tylko metadane.</span><span class="sxs-lookup"><span data-stu-id="7136c-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7136c-123">Być może należy użyć `/reference` przełącznik, aby określić ścieżkę pliku do żadnych zestawów zależnych.</span><span class="sxs-lookup"><span data-stu-id="7136c-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="7136c-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="7136c-124">Example</span></span>  
 <span data-ttu-id="7136c-125">W poniższym przykładzie pokazano sposób generowania metadanych dla implementacji usługi proste i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7136c-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="7136c-126">Aby wyeksportować metadane dla kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="7136c-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="7136c-127">Aby wyeksportować metadane dla kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="7136c-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="7136c-128">Aby wyeksportować metadane dla implementacji usługi.</span><span class="sxs-lookup"><span data-stu-id="7136c-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="7136c-129">`<path>` To ścieżka do Contracts.dll.</span><span class="sxs-lookup"><span data-stu-id="7136c-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7136c-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7136c-130">See Also</span></span>  
 [<span data-ttu-id="7136c-131">Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="7136c-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="7136c-132">Eksportowanie i importowanie metadanych</span><span class="sxs-lookup"><span data-stu-id="7136c-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
