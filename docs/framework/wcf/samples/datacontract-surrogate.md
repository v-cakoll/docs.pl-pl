---
title: DataContract — surogat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: f08226d3d871caea2dea3eeaf1cd411557853e45
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976728"
---
# <a name="datacontract-surrogate"></a>DataContract — surogat
Ten przykład pokazuje, jak procesy, takie jak serializacji, deserializacji, eksportu schematu i importowania schematu, można dostosować przy użyciu klasy zastępczej kontraktu danych. Ten przykład pokazuje, jak używać surogatu w scenariuszu klienta i serwera, w którym dane są serializowane i przesyłane między klientem a usługą Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie zastosowano następujący kontrakt usługi:  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 Operacja `AddEmployee` umożliwia użytkownikom dodawanie danych o nowych pracownikach, a operacja `GetEmployee` obsługuje wyszukiwanie pracowników na podstawie nazwy.  
  
 Te operacje używają następującego typu danych:  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 W typie `Employee` nie można serializować klasy `Person` (pokazanej w następującym kodzie przykładowym) przez <xref:System.Runtime.Serialization.DataContractSerializer>, ponieważ nie jest ona prawidłową klasą kontraktu danych.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Do klasy `Person` można zastosować atrybut <xref:System.Runtime.Serialization.DataContractAttribute>, ale nie zawsze jest to możliwe. Na przykład Klasa `Person` może być zdefiniowana w osobnym zestawie, w którym nie ma kontroli.  
  
 Uwzględniając to ograniczenie, jeden ze sposobów serializacji klasy `Person` jest zastępowany inną klasą, która jest oznaczona za pomocą <xref:System.Runtime.Serialization.DataContractAttribute> i kopiuje dane do nowej klasy. Celem jest, aby Klasa `Person` była wyświetlana jako element DataContract do <xref:System.Runtime.Serialization.DataContractSerializer>. Należy zauważyć, że jest to jeden ze sposobów serializacji klas kontraktu nie będących danymi.  
  
 Przykład logicznie zastępuje klasę `Person` inną klasą o nazwie `PersonSurrogated`.  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 Surogat kontraktu danych służy do osiągnięcia tego zastąpienia. Surogat kontraktu danych jest klasą, która implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. W tym przykładzie Klasa `AllowNonSerializableTypesSurrogate` implementuje ten interfejs.  
  
 W implementacji interfejsu pierwsze zadanie polega na ustanowieniu mapowania typu z `Person` do `PersonSurrogated`. Ta opcja jest używana zarówno w czasie serializacji, jak i w czasie eksportowania schematu. To mapowanie jest osiągane przez implementację metody <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29>.  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapuje wystąpienie `Person` do wystąpienia `PersonSurrogated` podczas serializacji, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> zapewnia mapowanie odwrotne dla deserializacji, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
public object GetDeserializedObject(object obj,   
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 Aby zmapować kontrakt danych `PersonSurrogated` do istniejącej klasy `Person` podczas importowania schematu, przykład implementuje metodę <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29>, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,   
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 Następujący przykładowy kod uzupełnia implementację interfejsu <xref:System.Runtime.Serialization.IDataContractSurrogate>.  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,   
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,   
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 W tym przykładzie Surogat jest włączony w ServiceModel przez atrybut o nazwie `AllowNonSerializableTypesAttribute`. Deweloperzy będą musieli zastosować ten atrybut zgodnie z umową usługi, jak pokazano w powyższym kontrakcie usługi `IPersonnelDataService`. Ten atrybut implementuje `IContractBehavior` i konfiguruje Surogat w operacjach w jego `ApplyClientBehavior` i `ApplyDispatchBehavior` metodach.  
  
 Ten atrybut nie jest konieczny w tym przypadku — jest używany do celów demonstracyjnych w tym przykładzie. Użytkownicy mogą alternatywnie włączyć Surogat, ręcznie dodając podobne `IContractBehavior`, `IEndpointBehavior` lub `IOperationBehavior` przy użyciu kodu lub za pomocą konfiguracji.  
  
 Implementacja `IContractBehavior` wyszukuje operacje, które używają obiektu DataContract, sprawdzając, czy mają `DataContractSerializerOperationBehavior` zarejestrowane. Jeśli tak, ustawia właściwość `DataContractSurrogate` dla tego zachowania. Poniższy przykładowy kod przedstawia, jak to zrobić. Ustawienie surogatu dla tego zachowania operacji umożliwia jego serializacji i deserializacji.  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 Aby podłączyć Surogat do użycia podczas generowania metadanych, należy podjąć dodatkowe czynności. Jednym z mechanizmów jest zapewnienie `IWsdlExportExtension`, który ilustruje ten przykład. Innym sposobem jest zmodyfikowanie `WsdlExporter` bezpośrednio.  
  
 Atrybut `AllowNonSerializableTypesAttribute` implementuje `IWsdlExportExtension` i `IContractBehavior`. W takim przypadku rozszerzenie może być `IContractBehavior` lub `IEndpointBehavior`. Jego implementacja metody `IWsdlExportExtension.ExportContract` włącza Surogat przez dodanie go do `XsdDataContractExporter` używany podczas generowania schematu dla obiektu DataContract. Poniższy fragment kodu przedstawia, jak to zrobić.  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 Po uruchomieniu przykładu klient wywołuje polecenie AddEmployee, a następnie wywołanie GetEmployee, aby sprawdzić, czy pierwsze wywołanie zakończyło się pomyślnie. W oknie konsoli klienta zostanie wyświetlony wynik żądania operacji GetEmployee. Operacja GetEmployee musi się powieść, aby znaleźć pracownika i wydrukować "znaleziono".  
  
> [!NOTE]
> Ten przykład pokazuje, jak podłączyć Surogat do serializacji, deserializacji i generowania metadanych. Nie pokazuje, jak podłączyć Surogat do generowania kodu z metadanych. Aby zobaczyć przykład sposobu użycia surogatu w celu podłączenia do generowania kodu klienta, zobacz przykład [niestandardowej publikacji WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) .  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# wydanie rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
