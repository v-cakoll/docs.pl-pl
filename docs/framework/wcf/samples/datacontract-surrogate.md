---
title: DataContract — surogat
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 9677e3cf024e6c1e5b2f3360423ab55536748495
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600052"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="34009-102">DataContract — surogat</span><span class="sxs-lookup"><span data-stu-id="34009-102">DataContract Surrogate</span></span>
<span data-ttu-id="34009-103">Ten przykład pokazuje, jak procesy, takie jak serializacji, deserializacji, eksportu schematu i importowania schematu, można dostosować przy użyciu klasy zastępczej kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="34009-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="34009-104">Ten przykład pokazuje, jak używać surogatu w scenariuszu klienta i serwera, w którym dane są serializowane i przesyłane między klientem a usługą Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="34009-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34009-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="34009-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="34009-106">W przykładzie zastosowano następujący kontrakt usługi:</span><span class="sxs-lookup"><span data-stu-id="34009-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="34009-107">`AddEmployee`Dzięki tej operacji użytkownicy mogą dodawać dane dotyczące nowych pracowników, a `GetEmployee` operacja obsługuje wyszukiwanie pracowników na podstawie nazwy.</span><span class="sxs-lookup"><span data-stu-id="34009-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="34009-108">Te operacje używają następującego typu danych:</span><span class="sxs-lookup"><span data-stu-id="34009-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="34009-109">W `Employee` typie `Person` nie można serializować klasy (pokazanej w następującym przykładowym kodzie), <xref:System.Runtime.Serialization.DataContractSerializer> ponieważ nie jest ona prawidłową klasą kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="34009-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="34009-110">Można zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do `Person` klasy, ale nie zawsze jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="34009-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="34009-111">Na przykład `Person` Klasa może być zdefiniowana w osobnym zestawie, w którym nie ma kontroli.</span><span class="sxs-lookup"><span data-stu-id="34009-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="34009-112">Uwzględniając to ograniczenie, jeden ze sposobów serializacji `Person` klasy jest zastępowany inną klasą, która jest oznaczona <xref:System.Runtime.Serialization.DataContractAttribute> i kopiuje dane do nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="34009-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="34009-113">Celem jest to, aby `Person` Klasa była wyświetlana jako element DataContract do <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="34009-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="34009-114">Należy zauważyć, że jest to jeden ze sposobów serializacji klas kontraktu nie będących danymi.</span><span class="sxs-lookup"><span data-stu-id="34009-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="34009-115">Przykład logicznie zastępuje `Person` klasę inną klasą o nazwie `PersonSurrogated` .</span><span class="sxs-lookup"><span data-stu-id="34009-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="34009-116">Surogat kontraktu danych służy do osiągnięcia tego zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="34009-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="34009-117">Surogat kontraktu danych jest klasą implementującą <xref:System.Runtime.Serialization.IDataContractSurrogate> .</span><span class="sxs-lookup"><span data-stu-id="34009-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="34009-118">W tym przykładzie `AllowNonSerializableTypesSurrogate` Klasa implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="34009-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="34009-119">W implementacji interfejsu pierwsze zadanie polega na ustanowieniu mapowania typu z `Person` do `PersonSurrogated` .</span><span class="sxs-lookup"><span data-stu-id="34009-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="34009-120">Ta opcja jest używana zarówno w czasie serializacji, jak i w czasie eksportowania schematu.</span><span class="sxs-lookup"><span data-stu-id="34009-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="34009-121">To mapowanie jest osiągane przez implementację <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> metody.</span><span class="sxs-lookup"><span data-stu-id="34009-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="34009-122"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29>Metoda mapuje `Person` wystąpienie do `PersonSurrogated` wystąpienia podczas serializacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34009-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="34009-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29>Metoda zapewnia mapowanie odwrotne dla deserializacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34009-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="34009-124">Aby zmapować `PersonSurrogated` kontrakt danych do istniejącej `Person` klasy podczas importowania schematu, przykład implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> metodę, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="34009-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="34009-125">Następujący przykładowy kod uzupełnia implementację <xref:System.Runtime.Serialization.IDataContractSurrogate> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="34009-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="34009-126">W tym przykładzie Surogat jest włączony w ServiceModel przez atrybut o nazwie `AllowNonSerializableTypesAttribute` .</span><span class="sxs-lookup"><span data-stu-id="34009-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="34009-127">Deweloperzy będą musieli zastosować ten atrybut zgodnie z umową usługi, jak pokazano w `IPersonnelDataService` powyższym kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="34009-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="34009-128">Ten atrybut implementuje `IContractBehavior` i konfiguruje Surogat w operacjach `ApplyClientBehavior` i `ApplyDispatchBehavior` metodach.</span><span class="sxs-lookup"><span data-stu-id="34009-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="34009-129">Ten atrybut nie jest konieczny w tym przypadku — jest używany do celów demonstracyjnych w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34009-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="34009-130">Użytkownicy mogą alternatywnie włączyć Surogat, ręcznie dodając podobny `IContractBehavior` `IEndpointBehavior` lub `IOperationBehavior` wykorzystując kod lub korzystając z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34009-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="34009-131">`IContractBehavior`Implementacja szuka operacji, które używają obiektu DataContract, sprawdzając, czy mają `DataContractSerializerOperationBehavior` zarejestrowane.</span><span class="sxs-lookup"><span data-stu-id="34009-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="34009-132">Jeśli tak, ustawia `DataContractSurrogate` Właściwość dla tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="34009-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="34009-133">Poniższy przykładowy kod przedstawia, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="34009-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="34009-134">Ustawienie surogatu dla tego zachowania operacji umożliwia jego serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="34009-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="34009-135">Aby podłączyć Surogat do użycia podczas generowania metadanych, należy podjąć dodatkowe czynności.</span><span class="sxs-lookup"><span data-stu-id="34009-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="34009-136">Jednym z mechanizmów, które należy wykonać, jest dostarczenie tego `IWsdlExportExtension` , co ilustruje ten przykład.</span><span class="sxs-lookup"><span data-stu-id="34009-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="34009-137">Innym sposobem jest bezpośrednie zmodyfikowanie `WsdlExporter` .</span><span class="sxs-lookup"><span data-stu-id="34009-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="34009-138">`AllowNonSerializableTypesAttribute`Atrybut implementuje `IWsdlExportExtension` i `IContractBehavior` .</span><span class="sxs-lookup"><span data-stu-id="34009-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="34009-139">Rozszerzenie może być albo `IContractBehavior` `IEndpointBehavior` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="34009-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="34009-140">Jego `IWsdlExportExtension.ExportContract` Implementacja metody umożliwia Surogat przez dodanie go do `XsdDataContractExporter` użycia podczas generowania schematu dla obiektu DataContract.</span><span class="sxs-lookup"><span data-stu-id="34009-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="34009-141">Poniższy fragment kodu przedstawia, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="34009-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="34009-142">Po uruchomieniu przykładu klient wywołuje polecenie AddEmployee, a następnie wywołanie GetEmployee, aby sprawdzić, czy pierwsze wywołanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="34009-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="34009-143">W oknie konsoli klienta zostanie wyświetlony wynik żądania operacji GetEmployee.</span><span class="sxs-lookup"><span data-stu-id="34009-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="34009-144">Operacja GetEmployee musi się powieść, aby znaleźć pracownika i wydrukować "znaleziono".</span><span class="sxs-lookup"><span data-stu-id="34009-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34009-145">Ten przykład pokazuje, jak podłączyć Surogat do serializacji, deserializacji i generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="34009-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="34009-146">Nie pokazuje, jak podłączyć Surogat do generowania kodu z metadanych.</span><span class="sxs-lookup"><span data-stu-id="34009-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="34009-147">Aby zobaczyć przykład sposobu użycia surogatu w celu podłączenia do generowania kodu klienta, zobacz przykład [niestandardowej publikacji WSDL](custom-wsdl-publication.md) .</span><span class="sxs-lookup"><span data-stu-id="34009-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="34009-148">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="34009-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="34009-149">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34009-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="34009-150">Aby skompilować wersję języka C# rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34009-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="34009-151">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="34009-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="34009-152">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="34009-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="34009-153">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="34009-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="34009-154">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="34009-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="34009-155">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="34009-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
