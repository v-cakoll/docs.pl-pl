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
# <a name="datacontract-surrogate"></a><span data-ttu-id="d4b64-102">DataContract — surogat</span><span class="sxs-lookup"><span data-stu-id="d4b64-102">DataContract Surrogate</span></span>
<span data-ttu-id="d4b64-103">W tym przykładzie pokazano, jak procesy, takie jak serializacji, deserializacji, eksportu schematu i importu schematu można dostosować przy użyciu klasy zastępczej kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="d4b64-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="d4b64-104">W tym przykładzie pokazano, jak używać surogatu w scenariuszu klienta i serwera, w którym dane są serializowane i przesyłane między klientem i usługą Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d4b64-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4b64-105">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d4b64-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d4b64-106">W przykładzie użyto następującej umowy serwisowej:</span><span class="sxs-lookup"><span data-stu-id="d4b64-106">The sample uses the following service contract:</span></span>  
  
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
  
 <span data-ttu-id="d4b64-107">Operacja `AddEmployee` umożliwia użytkownikom dodawanie danych o nowych `GetEmployee` pracownikach, a operacja obsługuje wyszukiwanie pracowników na podstawie nazwy.</span><span class="sxs-lookup"><span data-stu-id="d4b64-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="d4b64-108">Operacje te używają następującego typu danych:</span><span class="sxs-lookup"><span data-stu-id="d4b64-108">These operations use the following data type:</span></span>  
  
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
  
 <span data-ttu-id="d4b64-109">W `Employee` typie `Person` klasy (pokazane w poniższym kodzie przykładu) nie może być serializowany <xref:System.Runtime.Serialization.DataContractSerializer> przez, ponieważ nie jest prawidłową klasą kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="d4b64-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="d4b64-110">Można zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do `Person` klasy, ale nie zawsze jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d4b64-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="d4b64-111">Na przykład `Person` klasa może być zdefiniowana w oddzielnym zestawie, nad którym nie masz kontroli.</span><span class="sxs-lookup"><span data-stu-id="d4b64-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="d4b64-112">Biorąc pod uwagę to ograniczenie, `Person` jednym ze sposobów serializacji klasy <xref:System.Runtime.Serialization.DataContractAttribute> jest zastąpienie jej inną klasą, która jest oznaczona i skopiować niezbędne dane do nowej klasy.</span><span class="sxs-lookup"><span data-stu-id="d4b64-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="d4b64-113">Celem jest, aby `Person` klasa była wyświetlana jako <xref:System.Runtime.Serialization.DataContractSerializer>DataContract do .</span><span class="sxs-lookup"><span data-stu-id="d4b64-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="d4b64-114">Należy zauważyć, że jest to jeden ze sposobów serializacji klas kontraktów innych niż dane.</span><span class="sxs-lookup"><span data-stu-id="d4b64-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="d4b64-115">Próbka logicznie zastępuje `Person` klasę inną klasą o nazwie `PersonSurrogated`.</span><span class="sxs-lookup"><span data-stu-id="d4b64-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-116">Surogat kontraktu danych jest używany do osiągnięcia tego zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="d4b64-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="d4b64-117">Surogat kontraktu danych jest <xref:System.Runtime.Serialization.IDataContractSurrogate>klasą, która implementuje .</span><span class="sxs-lookup"><span data-stu-id="d4b64-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="d4b64-118">W tym przykładzie `AllowNonSerializableTypesSurrogate` klasa implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="d4b64-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="d4b64-119">W implementacji interfejsu pierwszym zadaniem jest ustanowienie `Person` `PersonSurrogated`mapowania typu od do .</span><span class="sxs-lookup"><span data-stu-id="d4b64-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="d4b64-120">Jest to używane zarówno w czasie serializacji, jak i w czasie eksportowania schematu.</span><span class="sxs-lookup"><span data-stu-id="d4b64-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="d4b64-121">To mapowanie jest osiągane <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> przez wdrożenie metody.</span><span class="sxs-lookup"><span data-stu-id="d4b64-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-122">Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> mapuje `Person` wystąpienie `PersonSurrogated` do wystąpienia podczas serializacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4b64-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-123">Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> zapewnia mapowanie wsteczne dla deserializacji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4b64-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-124">Aby zamapować kontrakt `PersonSurrogated` `Person` danych do istniejącej klasy podczas <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> importowania schematu, przykład implementuje metodę, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4b64-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-125">Poniższy przykładowy kod kończy <xref:System.Runtime.Serialization.IDataContractSurrogate> implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d4b64-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-126">W tym przykładzie surogat jest włączony w ServiceModel przez atrybut o nazwie `AllowNonSerializableTypesAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d4b64-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="d4b64-127">Deweloperzy musieliby zastosować ten atrybut w umowie `IPersonnelDataService` serwisowej, jak pokazano w umowie serwisowej powyżej.</span><span class="sxs-lookup"><span data-stu-id="d4b64-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="d4b64-128">Ten atrybut implementuje i konfiguruje `IContractBehavior` zastępczego na operacje w jego `ApplyClientBehavior` i `ApplyDispatchBehavior` metod.</span><span class="sxs-lookup"><span data-stu-id="d4b64-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="d4b64-129">Atrybut nie jest konieczne w tym przypadku - jest on używany do celów demonstracyjnych w tej próbce.</span><span class="sxs-lookup"><span data-stu-id="d4b64-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="d4b64-130">Użytkownicy mogą alternatywnie włączyć surogat, `IEndpointBehavior` `IOperationBehavior` ręcznie dodając podobny `IContractBehavior`, lub przy użyciu kodu lub przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d4b64-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="d4b64-131">Implementacja `IContractBehavior` wyszukuje operacje, które używają DataContract, sprawdzając, czy mają zarejestrowane. `DataContractSerializerOperationBehavior`</span><span class="sxs-lookup"><span data-stu-id="d4b64-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="d4b64-132">Jeśli tak, ustawia `DataContractSurrogate` właściwość na to zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d4b64-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="d4b64-133">Poniższy przykładowy kod pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d4b64-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="d4b64-134">Ustawienie surogatu na to zachowanie operacji umożliwia serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d4b64-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-135">Należy podjąć dodatkowe kroki, aby podłączyć surogat do użycia podczas generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4b64-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="d4b64-136">Jednym z mechanizmów, aby `IWsdlExportExtension` to zrobić, jest zapewnienie, co pokazuje ten przykład.</span><span class="sxs-lookup"><span data-stu-id="d4b64-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="d4b64-137">Innym sposobem jest `WsdlExporter` zmodyfikowanie bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="d4b64-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="d4b64-138">Atrybut `AllowNonSerializableTypesAttribute` implementuje `IWsdlExportExtension` i `IContractBehavior`.</span><span class="sxs-lookup"><span data-stu-id="d4b64-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="d4b64-139">Rozszerzenie może być albo `IContractBehavior` `IEndpointBehavior` w tym przypadku.</span><span class="sxs-lookup"><span data-stu-id="d4b64-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="d4b64-140">Jego `IWsdlExportExtension.ExportContract` implementacja metody umożliwia zastępcze `XsdDataContractExporter` przez dodanie go do używane podczas generowania schematu dla DataContract.</span><span class="sxs-lookup"><span data-stu-id="d4b64-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="d4b64-141">Poniższy fragment kodu pokazuje, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d4b64-141">The following code snippet shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="d4b64-142">Po uruchomieniu próbki, klient wywołuje AddEmployee następuje Wywołanie GetEmployee, aby sprawdzić, czy pierwsze wywołanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d4b64-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="d4b64-143">Wynik żądania operacji GetEmployee jest wyświetlany w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="d4b64-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="d4b64-144">Operacja GetEmployee musi zakończyć się pomyślnie znalezieniem pracownika i wydrukowaniem "found".</span><span class="sxs-lookup"><span data-stu-id="d4b64-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4b64-145">W tym przykładzie pokazano, jak podłączyć surogat do serializacji, deserializacji i generowania metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4b64-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="d4b64-146">Nie pokazuje, jak podłączyć surogat dla generowania kodu z metadanych.</span><span class="sxs-lookup"><span data-stu-id="d4b64-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="d4b64-147">Aby zobaczyć przykład, jak surogat może służyć do podłączenia do generowania kodu klienta, zobacz przykład [publikacji niestandardowe WSDL.](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)</span><span class="sxs-lookup"><span data-stu-id="d4b64-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d4b64-148">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="d4b64-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d4b64-149">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4b64-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d4b64-150">Aby utworzyć wersję C# rozwiązania, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4b64-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d4b64-151">Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d4b64-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d4b64-152">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d4b64-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d4b64-153">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="d4b64-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d4b64-154">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="d4b64-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d4b64-155">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d4b64-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
