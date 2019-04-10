---
title: DataContract — surogat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: a56fbcabfacf146142f7b0c0623325cc8e69c29a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312634"
---
# <a name="datacontract-surrogate"></a>DataContract — surogat
Niniejszy przykład pokazuje, jak procesy takie jak serializacji, deserializacji, schemat eksportu i importu schematu można dostosować za pomocą kontraktu danych zastępczych klas. W tym przykładzie pokazano, jak używać zastępczy w ramach scenariusza klienta i serwera, gdzie dane są serializacji i przesyłane między klientem usługi Windows Communication Foundation (WCF) i usługi.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W przykładzie użyto następujących kontraktu usługi:  
  
```  
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
  
 `AddEmployee` Operacji umożliwia użytkownikom dodawanie danych dotyczących nowych pracowników i `GetEmployee` operacja obsługuje wyszukiwanie pracowników na podstawie nazwy.  
  
 Te operacje przy użyciu następującego typu danych:  
  
```  
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
  
 W `Employee` typu `Person` klasy (pokazano w poniższym przykładowym kodzie) nie może być serializowany przez <xref:System.Runtime.Serialization.DataContractSerializer> , ponieważ nie jest klasą kontraktu prawidłowe dane.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Można zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu `Person` klasy, ale nie zawsze jest możliwe. Na przykład `Person` klasy można zdefiniować w oddzielnym zestawie, nad którym masz żadnej kontroli.  
  
 Biorąc pod uwagę to ograniczenie jest jednym ze sposobów, aby serializować `Person` ma zastąpić inną klasę, która jest oznaczona za pomocą klasy <xref:System.Runtime.Serialization.DataContractAttribute> i skopiuj niezbędne dane do nowej klasy. Celem jest zapewnienie `Person` klasy są traktowane jako DataContract do <xref:System.Runtime.Serialization.DataContractSerializer>. Należy pamiętać, że jest jednym ze sposobów serializacji kontrakt danych innych klas.  
  
 Przykład logicznie zastępuje `Person` klasy z inną klasę o nazwie `PersonSurrogated`.  
  
```  
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
  
 Zastępczy kontraktu danych jest wykorzystywana do osiągania ta zastępowania. Zastępczy kontraktu danych, to klasa, która implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. W tym przykładzie `AllowNonSerializableTypesSurrogate` klasa implementuje ten interfejs.  
  
 W implementacji interfejsu pierwsze zadanie jest ustanowienie mapowanie typu `Person` do `PersonSurrogated`. Jest to używane zarówno w czasie serializacji, a także w czasie eksportu schematu. To mapowanie jest osiągane poprzez implementację <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.  
  
```  
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Mapy metoda `Person` wystąpienia do `PersonSurrogated` wystąpienia podczas serializacji, jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Metoda zapewnia mapowania odwrotnego do deserializacji, jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
  
 Aby zamapować `PersonSurrogated` kontraktu danych do istniejących `Person` klasy podczas importowania schematu, implementuje przykładowe <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> metodzie, jak pokazano w poniższym przykładowym kodzie.  
  
```  
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
  
 Następujący przykładowy kod kończy wykonania <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu.  
  
```  
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
  
 W tym przykładzie surogatu jest włączone w modelu ServiceModel przez atrybut o nazwie `AllowNonSerializableTypesAttribute`. Deweloperzy należy zastosować ten atrybut na ich kontraktu usługi, jak pokazano na `IPersonnelDataService` powyżej kontraktu usługi. Ten atrybut implementuje `IContractBehavior` i konfiguruje zastępczy na operacje w jej `ApplyClientBehavior` i `ApplyDispatchBehavior` metody.  
  
 Ten atrybut nie jest konieczne w tym przypadku - służy w celach demonstracyjnych, w tym przykładzie. Użytkowników można również włączyć zastępczy, ręcznie dodając podobny `IContractBehavior`, `IEndpointBehavior` lub `IOperationBehavior` za pomocą kodu lub konfiguracji.  
  
 `IContractBehavior` Implementacji szuka operacji korzystających z DataContract przez sprawdzenie, czy mają one `DataContractSerializerOperationBehavior` zarejestrowany. Jeśli tak jest, ustawia `DataContractSurrogate` właściwość tego zachowania. Poniższy przykład kodu pokazuje, jak to zrobić. Ustawienie to zachowanie operacji surogatu włączy ją do serializacji i deserializacji.  
  
```  
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
  
 Dodatkowe kroki konieczne do wykonania, monit o podłączenie zastępczy do użycia podczas generowania metadanych. Jeden mechanizm, w tym celu jest zapewnienie `IWsdlExportExtension` czyli w tym przykładzie przedstawiono. Innym sposobem jest zmodyfikowanie `WsdlExporter` bezpośrednio.  
  
 `AllowNonSerializableTypesAttribute` Atrybutu implementuje `IWsdlExportExtension` i `IContractBehavior`. Rozszerzenie może być `IContractBehavior` lub `IEndpointBehavior` w tym przypadku. Jego `IWsdlExportExtension.ExportContract` implementacji metody umożliwia surogatu przez dodanie jej do `XsdDataContractExporter` używane podczas generowania schematu DataContract. Poniższy fragment kodu pokazuje, jak to zrobić.  
  
```  
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
  
 Po uruchomieniu przykładu, gdy klient wywołuje AddEmployee następuje wywołanie GetEmployee, aby sprawdzić, jeśli pierwsze wywołanie zakończyło się pomyślnie. Wynik żądania operacji GetEmployee jest wyświetlany w oknie konsoli klienta. Operacja GetEmployee musi przeprowadzić udany przyrost znajdowanie pracownika i Drukuj "znaleziono".  
  
> [!NOTE]
>  Niniejszy przykład pokazuje, jak podłączyć surogatu serializacja, deserializacji a Generowanie metadanych. Jak monit o podłączenie substytut dla generowania kodu z metadanych, nie są wyświetlane. Aby zobaczyć przykładowy sposób zastępczy mogą być używane do generowania kodu klienta, zobacz [niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) próbki.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować wersji języka C# rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
