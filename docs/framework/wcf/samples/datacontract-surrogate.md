---
title: "DataContract — surogat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ffb8ec71d6a8bbbdf365b78ad13af7524cc33ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="datacontract-surrogate"></a>DataContract — surogat
W przykładzie pokazano, jak procesy, takie jak serializacji, deserializacji schematu eksportowania i importowania schematu można dostosować za pomocą kontraktu danych dwuskładnikowy klasy. Ten przykład przedstawia sposób użycia surogatu w przypadku scenariusza klienta i serwera, gdy dane są serializowane i przesyłane między [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta i usługi.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
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
  
 `AddEmployee` Operacji umożliwia użytkownikom dodanie danych dotyczących nowych pracowników i `GetEmployee` operacja obsługuje wyszukiwania dla pracowników na podstawie nazwy.  
  
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
  
 W `Employee` typu `Person` klasy (wyświetlone czcionką następujący przykładowy kod) nie może być serializowany przez <xref:System.Runtime.Serialization.DataContractSerializer> , ponieważ nie jest klasą kontraktu prawidłowe dane.  
  
```  
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 Możesz zastosować `DataContract` atrybutu `Person` klasy, ale nie zawsze jest możliwe. Na przykład `Person` w osobny zestaw, w którym masz kontrolka nie można zdefiniować klasy.  
  
 Podane to ograniczenie, aby serializować `Person` klasa ma zastąpić go z innej klasy, która jest oznaczony atrybutem `DataContractAttribute` i skopiuj przez dane niezbędne do nowej klasy. Celem jest zapewnienie `Person` klasy są wyświetlane jako DataContract do <xref:System.Runtime.Serialization.DataContractSerializer>. Należy pamiętać, że jest jednym ze sposobów serializować klasy kontraktu bez danych.  
  
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
  
 Surogatu kontraktu danych służy do osiągnięcia tego zastąpienia. Zastępcza Umowa danych jest klasa, która implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate>. W tym przykładzie `AllowNonSerializableTypesSurrogate` klasa implementuje ten interfejs.  
  
 W implementacji interfejsu pierwszego zadania jest ustanowienie mapowanie typu `Person` do `PersonSurrogated`. To jest używany zarówno w czasie serializacji, jak i w czasie eksportowania schematu. Zaimplementowanie odbywa się to mapowanie <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> Mapy metody `Person` wystąpienie do `PersonSurrogated` wystąpienie podczas serializacji, jak pokazano w poniższym kodzie próbki.  
  
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
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> Metoda zapewnia wstecznego mapowania do deserializacji, jak pokazano w poniższym kodzie próbki.  
  
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
  
 Do mapowania `PersonSurrogated` kontraktu danych do istniejącej `Person` klasy podczas importowania schematu, implementuje próbki <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> metody, jak pokazano w poniższym kodzie próbki.  
  
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
  
 Następujący przykładowy kod zakończeniu realizacji <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu.  
  
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
  
 W tym przykładzie surogatu jest włączone w modelu ServiceModel przez atrybut o nazwie `AllowNonSerializableTypesAttribute`. Deweloperzy należy zastosować ten atrybut na ich kontraktu usługi, jak pokazano na `IPersonnelDataService` powyżej kontraktu usługi. Ten atrybut implementuje `IContractBehavior` i konfiguruje surogatu na operacje w jego `ApplyClientBehavior` i `ApplyDispatchBehavior` metody.  
  
 Ten atrybut nie jest konieczne w takim przypadku — służy do celów demonstracyjnych, w tym przykładzie. Użytkownicy mogą również włączyć surogatu przez ręczne dodanie podobne `IContractBehavior`, `IEndpointBehavior` lub `IOperationBehavior` przy użyciu kodu lub konfiguracji.  
  
 `IContractBehavior` Wygląda implementację dla operacji korzystających z DataContract przez sprawdzenie, czy mają one `DataContractSerializerOperationBehavior` zarejestrowany. Jeśli nie, ustawia `DataContractSurrogate` właściwości tego zachowania. Następujący przykładowy kod pokazuje, jak to zrobić. Ustawienie to zachowanie operacji surogatu włączy ją do serializacji i deserializacji.  
  
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
  
 Dodatkowe kroki należy podjąć w celu podłączenia surogatu do użycia podczas generowania metadanych. Jeden mechanizm w tym celu jest zapewnienie `IWsdlExportExtension` czyli przykładzie pokazano. Innym sposobem jest zmodyfikowanie `WsdlExporter` bezpośrednio.  
  
 `AllowNonSerializableTypesAttribute` Atrybutu implementuje `IWsdlExportExtension` i `IContractBehavior`. Rozszerzenia mogą być `IContractBehavior` lub `IEndpointBehavior` w takim przypadku. Jego `IWsdlExportExtension.ExportContract` implementacji metody umożliwia surogatu, dodając ją do `XsdDataContractExporter` używane podczas generowania schematu DataContract. Poniższy fragment kodu pokazano, jak to zrobić.  
  
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
  
 Po uruchomieniu próbki, gdy klient wywołuje AddEmployee następuje wywołanie GetEmployee w celu sprawdzenia, jeśli pierwsze wywołanie zakończyło się pomyślnie. Wynik żądania operacji GetEmployee jest wyświetlany w oknie konsoli klienta. Operacja GetEmployee musi pomyślnie w znajdowaniu pracownik i wydrukować "znaleziono".  
  
> [!NOTE]
>  W tym przykładzie pokazano, jak dołączyć surogatu serializacja, deserializacji a Generowanie metadanych. Jak dołączyć surogatu dla generowanie kodu na podstawie metadanych nie są wyświetlane. Aby zapoznać się przykładem sposobu surogatu może służyć do generowania kodu klienta, zobacz [niestandardowa publikacja WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) próbki.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby utworzyć edition C# rozwiązania, postępuj zgodnie z instrukcjami w [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
  
## <a name="see-also"></a>Zobacz też
