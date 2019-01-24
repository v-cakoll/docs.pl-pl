---
title: 'Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: 6af43b076f7c508fd17cac367caeed30065b0c4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648113"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Instrukcje: Eksportowanie metadanych ze skompilowanego kodu usługi za pomocą programu Svcutil.exe
Svcutil.exe można wyeksportować metadane dotyczące usług, kontrakty i typów danych w skompilowanych zestawach w następujący sposób:  
  
-   Aby wyeksportować metadane dla wszystkich skompilowany kontraktów usług zbiór zestawów przy użyciu Svcutil.exe, określ zestawy jako parametry wejściowe. Jest to zachowanie domyślne.  
  
-   Aby wyeksportować metadane usługi skompilowanych przy użyciu Svcutil.exe, należy określić zestaw usług lub zestawów jako parametry wejściowe. Należy użyć `/serviceName` opcję, aby wskazać nazwę konfiguracji usługi, którą chcesz wyeksportować. Svcutil.exe automatycznie ładuje plik konfiguracji dla określonego zestawu wykonywalnego.  
  
-   Aby wyeksportować wszystkie typy kontraktu danych w obrębie zbioru zestawów, należy użyć `/dataContractOnly` opcji.  
  
> [!NOTE]
>  Użyj `/reference` możliwość określenia ścieżki do plików do żadnych zestawów zależnych.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Aby wyeksportować metadane dla skompilowanych kontraktów usług  
  
1.  Kompiluj swoje implementacji kontraktu usługi do co najmniej jeden libraries.1 klasy  
  
2.  Uruchom Svcutil.exe skompilowanych zestawów.  
  
    > [!NOTE]
    >  Może być konieczne użycie `/reference` przełącznik, aby określić ścieżkę pliku, do wszelkich zestawów zależnych.  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Aby wyeksportować metadane dla skompilowanych usługi  
  
1.  Skompiluj implementacji usługi do zestawu pliku wykonywalnego.  
  
2.  Utwórz plik konfiguracji dla Twojego pliku wykonywalnego usługi i Dodaj konfigurację usługi.  
  
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
  
3.  Uruchom Svcutil.exe w pliku wykonywalnego usługi skompilowanych przy użyciu `/serviceName` przełącznika, aby określić nazwę konfiguracji usługi.  
  
    > [!NOTE]
    >  Może być konieczne użycie `/reference` przełącznik, aby określić ścieżkę pliku, do wszelkich zestawów zależnych.  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Aby wyeksportować metadane dla skompilowanych kontraktów danych  
  
1.  Skompiluj swoje implementacji kontraktu danych do co najmniej jedną bibliotekę klas.  
  
2.  Uruchom Svcutil.exe w skompilowanych zestawach, za pomocą `/dataContract` przełącznika dla kontraktów danych powinny być generowane tylko metadane.  
  
    > [!NOTE]
    >  Może być konieczne użycie `/reference` przełącznik, aby określić ścieżkę pliku, do wszelkich zestawów zależnych.  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można wygenerować metadane dotyczące konfiguracji i implementacji usługi simple.  
  
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
  
 `<path>` Jest ścieżką do Contracts.dll.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Eksportowanie i importowanie metadanych](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
