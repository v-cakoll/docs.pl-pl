---
title: "Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b6998333c3e49b24ad5bb96f36be65af94b6033
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe
Svcutil.exe można wyeksportować metadane dla usług, kontrakty i typów danych w zestawach skompilowany w następujący sposób:  
  
-   Aby wyeksportować metadane dla wszystkich skompilowany kontraktów usług dla zestawu zestawów przy użyciu Svcutil.exe, określ zestawy jako parametry wejściowe. Jest to zachowanie domyślne.  
  
-   Aby wyeksportować metadane dla usługi skompilowanych przy użyciu Svcutil.exe, określ usługi zestawu lub zestawów jako parametry wejściowe. Należy użyć `/serviceName` możliwość wskazania nazwy konfiguracji usługi do wyeksportowania. Svcutil.exe automatycznie ładuje plik konfiguracji dla określonego zestawu pliku wykonywalnego.  
  
-   Aby wyeksportować wszystkie typy kontraktu danych w ramach zestawu zestawów, należy użyć `/dataContractOnly` opcji.  
  
> [!NOTE]
>  Użyj `/reference` można określić ścieżki pliku do żadnych zestawów zależnych.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Aby wyeksportować metadane dla skompilowanych kontraktów usług  
  
1.  Kompiluj z implementacji kontraktu usługi do co najmniej jeden libraries.1 — klasa  
  
2.  Uruchom Svcutil.exe na skompilowane zestawy.  
  
    > [!NOTE]
    >  Być może należy użyć `/reference` przełącznik, aby określić ścieżkę pliku do żadnych zestawów zależnych.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Aby wyeksportować metadane dla skompilowanych usługi  
  
1.  Kompiluj implementacji usługi do pliku wykonywalnego zestawu.  
  
2.  Utwórz plik konfiguracji do pliku wykonywalnego usługi i Dodaj konfiguracji usługi.  
  
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
  
3.  Uruchom Svcutil.exe na usługa skompilowanego pliku wykonywalnego używa `/serviceName` przełącznik, aby określić nazwę konfiguracji usługi.  
  
    > [!NOTE]
    >  Być może należy użyć `/reference` przełącznik, aby określić ścieżkę pliku do żadnych zestawów zależnych.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Aby wyeksportować metadane dla skompilowanych kontraktów danych  
  
1.  Kompiluj z implementacji kontraktu danych do jednego lub więcej bibliotek klas.  
  
2.  Uruchom Svcutil.exe na skompilowane zestawy za pomocą `/dataContract` przełącznika dla kontraktów danych powinny być generowane tylko metadane.  
  
    > [!NOTE]
    >  Być może należy użyć `/reference` przełącznik, aby określić ścieżkę pliku do żadnych zestawów zależnych.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób generowania metadanych dla implementacji usługi proste i konfiguracji.  
  
 Aby wyeksportować metadane dla kontraktu usługi.  
  
```  
svcutil.exe Contracts.dll  
```  
  
 Aby wyeksportować metadane dla kontraktów danych.  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Aby wyeksportować metadane dla implementacji usługi.  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>` To ścieżka do Contracts.dll.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Eksportowanie i Importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
