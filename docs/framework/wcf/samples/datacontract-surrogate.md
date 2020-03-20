---
title: DataContract — surogat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 7ef78c4361c055d7be35c03a3c8717e86aceddab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183836"
---
# <a name="datacontract-surrogate"></a>DataContract — surogat
W tym przykładzie pokazano, jak procesy, takie jak serializacji, deserializacji, eksportu schematu i importu schematu można dostosować przy użyciu klasy zastępczej kontraktu danych. W tym przykładzie pokazano, jak używać surogatu w scenariuszu klienta i serwera, w którym dane są serializowane i przesyłane między klientem i usługą Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie użyto następującej umowy serwisowej:  
  
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
  
 Operacja `AddEmployee` umożliwia użytkownikom dodawanie danych o nowych `GetEmployee` pracownikach, a operacja obsługuje wyszukiwanie pracowników na podstawie nazwy.  
  
 Operacje te używają następującego typu danych:  
  
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
  
 W `Employee` typie `Person` klasy (pokazane w poniższym kodzie przykładu) nie może być serializowany <xref:System.Runtime.Serialization.DataContractSerializer> przez, ponieważ nie jest prawidłową klasą kontraktu danych.  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Można zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do `Person` klasy, ale nie zawsze jest to możliwe. Na przykład `Person` klasa może być zdefiniowana w oddzielnym zestawie, nad którym nie masz kontroli.  
  
 Biorąc pod uwagę to ograniczenie, `Person` jednym ze sposobów serializacji klasy <xref:System.Runtime.Serialization.DataContractAttribute> jest zastąpienie jej inną klasą, która jest oznaczona i skopiować niezbędne dane do nowej klasy. Celem jest, aby `Person` klasa była wyświetlana jako <xref:System.Runtime.Serialization.DataContractSerializer>DataContract do . Należy zauważyć, że jest to jeden ze sposobów serializacji klas kontraktów innych niż dane.  
  
 Próbka logicznie zastępuje `Person` klasę inną klasą o nazwie `PersonSurrogated`.  
  
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
  
 Surogat kontraktu danych jest używany do osiągnięcia tego zastąpienia. Surogat kontraktu danych jest <xref:System.Runtime.Serialization.IDataContractSurrogate>klasą, która implementuje . W tym przykładzie `AllowNonSerializableTypesSurrogate` klasa implementuje ten interfejs.  
  
 W implementacji interfejsu pierwszym zadaniem jest ustanowienie `Person` `PersonSurrogated`mapowania typu od do . Jest to używane zarówno w czasie serializacji, jak i w czasie eksportowania schematu. To mapowanie jest osiągane <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> przez wdrożenie metody.  
  
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
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapuje `Person` wystąpienie `PersonSurrogated` do wystąpienia podczas serializacji, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> zapewnia mapowanie wsteczne dla deserializacji, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Aby zamapować kontrakt `PersonSurrogated` `Person` danych do istniejącej klasy podczas <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> importowania schematu, przykład implementuje metodę, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Poniższy przykładowy kod kończy <xref:System.Runtime.Serialization.IDataContractSurrogate> implementację interfejsu.  
  
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
  
 W tym przykładzie surogat jest włączony w ServiceModel przez atrybut o nazwie `AllowNonSerializableTypesAttribute`. Deweloperzy musieliby zastosować ten atrybut w umowie `IPersonnelDataService` serwisowej, jak pokazano w umowie serwisowej powyżej. Ten atrybut implementuje i konfiguruje `IContractBehavior` zastępczego na operacje w jego `ApplyClientBehavior` i `ApplyDispatchBehavior` metod.  
  
 Atrybut nie jest konieczne w tym przypadku - jest on używany do celów demonstracyjnych w tej próbce. Użytkownicy mogą alternatywnie włączyć surogat, `IEndpointBehavior` `IOperationBehavior` ręcznie dodając podobny `IContractBehavior`, lub przy użyciu kodu lub przy użyciu konfiguracji.  
  
 Implementacja `IContractBehavior` wyszukuje operacje, które używają DataContract, sprawdzając, czy mają zarejestrowane. `DataContractSerializerOperationBehavior` Jeśli tak, ustawia `DataContractSurrogate` właściwość na to zachowanie. Poniższy przykładowy kod pokazuje, jak to zrobić. Ustawienie surogatu na to zachowanie operacji umożliwia serializacji i deserializacji.  
  
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
  
 Należy podjąć dodatkowe kroki, aby podłączyć surogat do użycia podczas generowania metadanych. Jednym z mechanizmów, aby `IWsdlExportExtension` to zrobić, jest zapewnienie, co pokazuje ten przykład. Innym sposobem jest `WsdlExporter` zmodyfikowanie bezpośrednio.  
  
 Atrybut `AllowNonSerializableTypesAttribute` implementuje `IWsdlExportExtension` i `IContractBehavior`. Rozszerzenie może być albo `IContractBehavior` `IEndpointBehavior` w tym przypadku. Jego `IWsdlExportExtension.ExportContract` implementacja metody umożliwia zastępcze `XsdDataContractExporter` przez dodanie go do używane podczas generowania schematu dla DataContract. Poniższy fragment kodu pokazuje, jak to zrobić.  
  
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
  
 Po uruchomieniu próbki, klient wywołuje AddEmployee następuje Wywołanie GetEmployee, aby sprawdzić, czy pierwsze wywołanie zakończyło się pomyślnie. Wynik żądania operacji GetEmployee jest wyświetlany w oknie konsoli klienta. Operacja GetEmployee musi zakończyć się pomyślnie znalezieniem pracownika i wydrukowaniem "found".  
  
> [!NOTE]
> W tym przykładzie pokazano, jak podłączyć surogat do serializacji, deserializacji i generowania metadanych. Nie pokazuje, jak podłączyć surogat dla generowania kodu z metadanych. Aby zobaczyć przykład, jak surogat może służyć do podłączenia do generowania kodu klienta, zobacz przykład [publikacji niestandardowe WSDL.](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
