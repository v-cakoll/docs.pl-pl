---
title: Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: 607d0eaabde4e00c1a00b995356bb6d4e1a39234
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855760"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="94b41-102">Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych</span><span class="sxs-lookup"><span data-stu-id="94b41-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="94b41-103">Windows Communication Foundation (WCF) ma opcję trybu zgodności ASP.NET, aby umożliwić aplikacjom WCF zaprogramowane i skonfigurowane, takie jak ASP.NET usługi sieci Web, i naśladowanie zachowania.</span><span class="sxs-lookup"><span data-stu-id="94b41-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="94b41-104">W poniższych sekcjach porównano usługi sieci Web ASP.NET i WCF na podstawie tego, co jest wymagane do opracowania aplikacji przy użyciu obu technologii.</span><span class="sxs-lookup"><span data-stu-id="94b41-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="94b41-105">Reprezentacja danych</span><span class="sxs-lookup"><span data-stu-id="94b41-105">Data Representation</span></span>

<span data-ttu-id="94b41-106">Opracowywanie usługi sieci Web za pomocą ASP.NET zwykle zaczyna się od definiowania złożonych typów danych, których usługa ma używać.</span><span class="sxs-lookup"><span data-stu-id="94b41-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="94b41-107">ASP.NET opiera się na usłudze <xref:System.Xml.Serialization.XmlSerializer> , aby przetłumaczyć dane reprezentowane przez .NET Framework typy na XML na potrzeby przesyłania danych do lub z usługi oraz do translacji danych odebranych jako XML do obiektów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94b41-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="94b41-108">Definiowanie złożonych typów danych, których usługa ASP.net ma używać, wymaga definicji klas .NET Framework, które <xref:System.Xml.Serialization.XmlSerializer> mogą serializować do i z XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="94b41-109">Takie klasy mogą być zapisywane ręcznie lub generowane na podstawie definicji typów w schemacie XML przy użyciu schematów XML wiersza polecenia/typów danych narzędzia, XSD. exe.</span><span class="sxs-lookup"><span data-stu-id="94b41-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="94b41-110">Poniżej przedstawiono listę najważniejszych zagadnień, które należy znać podczas definiowania klas .NET Framework, które <xref:System.Xml.Serialization.XmlSerializer> mogą serializować do i z XML:</span><span class="sxs-lookup"><span data-stu-id="94b41-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="94b41-111">Tylko pola publiczne i właściwości obiektów .NET Framework są tłumaczone na XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="94b41-112">Wystąpienia klas kolekcji można serializować do kodu XML tylko wtedy, gdy klasy implementują <xref:System.Collections.IEnumerable> interfejs lub. <xref:System.Collections.ICollection></span><span class="sxs-lookup"><span data-stu-id="94b41-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="94b41-113">Klasy implementujące <xref:System.Collections.IDictionary> interfejs, takie jak <xref:System.Collections.Hashtable>, nie mogą być serializowane do kodu XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="94b41-114">Wiele typów atrybutów w <xref:System.Xml.Serialization> przestrzeni nazw można dodać do klasy .NET Framework i jej elementów członkowskich, aby kontrolować sposób, w jaki wystąpienia klasy są reprezentowane w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="94b41-115">Projektowanie aplikacji WCF zwykle zaczyna się także od definicji typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="94b41-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="94b41-116">W programie WCF można używać tych samych .NET Framework typów co ASP.NET Web Services.</span><span class="sxs-lookup"><span data-stu-id="94b41-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="94b41-117">Funkcję WCF<xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> można dodać do typów .NET Framework, aby wskazać, że wystąpienia typu mają być serializowane do kodu XML, a określone pola lub właściwości typu mają być serializowane, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="94b41-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<span data-ttu-id="94b41-118">Oznacza <xref:System.Runtime.Serialization.DataContractAttribute> to, że co najmniej zero pól lub właściwości typu jest serializowany, <xref:System.Runtime.Serialization.DataMemberAttribute> podczas gdy wskazuje, że określone pole lub właściwość ma być serializowana.</span><span class="sxs-lookup"><span data-stu-id="94b41-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="94b41-119"><xref:System.Runtime.Serialization.DataContractAttribute> Można zastosować do klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="94b41-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="94b41-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Można zastosować do pola lub właściwości, a pola i właściwości, do których zastosowano atrybut, mogą być publiczne lub prywatne.</span><span class="sxs-lookup"><span data-stu-id="94b41-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="94b41-121">Wystąpienia typów, które mają <xref:System.Runtime.Serialization.DataContractAttribute> zastosowane do nich, są określane jako Kontrakty danych w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="94b41-122">Są one serializowane do kodu <xref:System.Runtime.Serialization.DataContractSerializer>XML przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="94b41-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="94b41-123">Poniżej znajduje się lista ważnych różnic między użyciem <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> i różnymi atrybutami <xref:System.Xml.Serialization> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="94b41-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="94b41-124"><xref:System.Xml.Serialization.XmlSerializer> I atrybuty<xref:System.Xml.Serialization> przestrzeni nazw zostały zaprojektowane tak, aby umożliwiały Mapowanie typów .NET Framework do dowolnego prawidłowego typu zdefiniowanego w schemacie XML i dlatego zapewniają bardzo precyzyjne sterowanie sposobem, w jaki typ jest reprezentowany w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="94b41-125"><xref:System.Runtime.Serialization.DataContractSerializer> Izapewniająbardzoniewielkąkontrolęnadsposobemreprezentowania<xref:System.Runtime.Serialization.DataMemberAttribute> typu w kodzie XML. <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="94b41-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="94b41-126">Można określić tylko obszary nazw i nazwy używane do reprezentowania typu i jego pól lub właściwości w kodzie XML oraz sekwencję, w której pola i właściwości są wyświetlane w kodzie XML:</span><span class="sxs-lookup"><span data-stu-id="94b41-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

  ```csharp
  [DataContract(
  Namespace="urn:Contoso:2006:January:29",
  Name="LineItem")]
  public class LineItem
  {
        [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
        public string itemNumber;
        [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
        public decimal quantity;
        [DataMember(Name="Price",IsRequired=false,Order = 2)]
        public decimal unitPrice;
  }
  ```

  <span data-ttu-id="94b41-127">Wszystkie inne informacje o strukturze kodu XML użytego do reprezentowania typu .NET są określane przez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="94b41-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="94b41-128">Przez nieumożliwienie kontroli nad sposobem reprezentowania typu w kodzie XML, proces serializacji jest wysoce przewidywalny dla <xref:System.Runtime.Serialization.DataContractSerializer>, i, w tym celu, łatwiej zoptymalizować.</span><span class="sxs-lookup"><span data-stu-id="94b41-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="94b41-129">Praktyczną zaletą projektowania <xref:System.Runtime.Serialization.DataContractSerializer> jest lepsza wydajność, około dziesięciu procent lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="94b41-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="94b41-130">Atrybuty do użycia z <xref:System.Xml.Serialization.XmlSerializer> nie wskazują, które pola lub właściwości typu są serializowane do kodu XML, <xref:System.Runtime.Serialization.DataMemberAttribute> natomiast do użycia z <xref:System.Runtime.Serialization.DataContractSerializer> pokazuje jawnie, które pola lub właściwości są serializowane.</span><span class="sxs-lookup"><span data-stu-id="94b41-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="94b41-131">W związku z tym Kontrakty danych są jawnymi umowami dotyczącymi struktury danych wysyłanych i odbieranych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="94b41-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="94b41-132">Może przetłumaczyć tylko publiczne elementy członkowskie obiektu platformy .NET na XML <xref:System.Runtime.Serialization.DataContractSerializer> , może przetłumaczyć elementy członkowskie obiektów na XML, niezależnie od modyfikatorów dostępu tych elementów członkowskich. <xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="94b41-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="94b41-133">W związku z tym <xref:System.Runtime.Serialization.DataContractSerializer> , że można serializować niepubliczne składowe typów do XML, ma mniejszą liczbę ograniczeń dla różnych typów .NET, które mogą serializować w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="94b41-134">W szczególności można przetłumaczyć na typy XML, <xref:System.Collections.Hashtable> takie jak <xref:System.Collections.IDictionary> implementujący interfejs.</span><span class="sxs-lookup"><span data-stu-id="94b41-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="94b41-135"><xref:System.Runtime.Serialization.DataContractSerializer> Jest to znacznie bardziej możliwe, aby można było serializować wystąpienia dowolnego istniejącego typu .NET do XML bez konieczności modyfikowania definicji typu lub tworzenia otoki dla niej.</span><span class="sxs-lookup"><span data-stu-id="94b41-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="94b41-136">Kolejną konsekwencją <xref:System.Runtime.Serialization.DataContractSerializer> uzyskiwania dostępu do niepublicznych składowych typu jest to, że wymaga pełnego zaufania, a w <xref:System.Xml.Serialization.XmlSerializer> przeciwnym razie nie.</span><span class="sxs-lookup"><span data-stu-id="94b41-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="94b41-137">Uprawnienie dostępu do kodu pełnego zaufania zapewnia pełny dostęp do wszystkich zasobów na komputerze, do którego można uzyskać dostęp przy użyciu poświadczeń, w których wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="94b41-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="94b41-138">Tej opcji należy używać w przypadku, gdy w pełni zaufany kod uzyskuje dostęp do wszystkich zasobów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="94b41-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="94b41-139"><xref:System.Runtime.Serialization.DataContractSerializer> Firma obejmuje niektóre wsparcie dla wersji:</span><span class="sxs-lookup"><span data-stu-id="94b41-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="94b41-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Mawłaściwość,którejmożnaprzypisaćwartośćfalsedlaelementówczłonkowskich,któresądodawanedonowychwersjikontraktudanych,któreniebyłyobecnewewcześniejszychwersjach,atymsamymZezwalanienaaplikacjez<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> nowszą wersją kontraktu możliwość przetworzenia wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="94b41-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="94b41-141">Jeśli kontrakt danych implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs, jeden z nich może <xref:System.Runtime.Serialization.DataContractSerializer> umożliwić przekazanie elementów członkowskich zdefiniowanych w nowszych wersjach kontraktu danych za pomocą aplikacji ze starszymi wersjami kontraktu.</span><span class="sxs-lookup"><span data-stu-id="94b41-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="94b41-142">Pomimo wszystkich różnic, kod XML, do którego <xref:System.Xml.Serialization.XmlSerializer> domyślnie serializowane serializacji typu jest semantycznie identyczny z XML, do <xref:System.Runtime.Serialization.DataContractSerializer> którego jest serializowany typ, pod warunkiem, że przestrzeń nazw XML jest jawnie zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="94b41-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="94b41-143">Poniższa klasa, która ma atrybuty do użycia z obu serializatorów, jest przetłumaczona na semantycznie identyczne XML przez <xref:System.Xml.Serialization.XmlSerializer>: <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="94b41-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

<span data-ttu-id="94b41-144">Zestaw Windows Software Development Kit (SDK) zawiera narzędzie wiersza polecenia o nazwie Narzędzie do [przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="94b41-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="94b41-145">Podobnie jak narzędzie XSD. exe używane z usługami sieci Web ASP.NET, Svcutil. exe może generować definicje typów danych .NET ze schematu XML.</span><span class="sxs-lookup"><span data-stu-id="94b41-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="94b41-146">Typy są kontraktami danych, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> mogą emitować kod XML w formacie zdefiniowanym przez schemat XML; w przeciwnym razie są one przeznaczone do serializacji <xref:System.Xml.Serialization.XmlSerializer>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="94b41-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="94b41-147">Svcutil. exe może również generować schemat XML z kontraktów danych przy użyciu jego `dataContractOnly` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="94b41-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="94b41-148">Mimo że usługi sieci Web ASP.NET <xref:System.Xml.Serialization.XmlSerializer>korzystają z programu, a tryb zgodności WCF ASP.NET sprawia, że usługi WCF zaśladią zachowanie usług sieci Web ASP.NET, opcja zgodności ASP.NET nie ogranicza <xref:System.Xml.Serialization.XmlSerializer>do użycia.</span><span class="sxs-lookup"><span data-stu-id="94b41-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="94b41-149">Może nadal korzystać <xref:System.Runtime.Serialization.DataContractSerializer> z usług z usługami uruchomionymi w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="94b41-150">Opracowywanie usług</span><span class="sxs-lookup"><span data-stu-id="94b41-150">Service Development</span></span>

<span data-ttu-id="94b41-151">Aby opracować usługę przy użyciu ASP.NET, jest ona niestandardowa, aby dodać <xref:System.Web.Services.WebService> atrybut do klasy, <xref:System.Web.Services.WebMethodAttribute> oraz do dowolnej metody klasy, które mają być operacją usługi:</span><span class="sxs-lookup"><span data-stu-id="94b41-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="94b41-152">W ASP.NET 2,0 wprowadzono opcję dodania atrybutu <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> do interfejsu, a nie do klasy, i zapisanie klasy w celu zaimplementowania interfejsu:</span><span class="sxs-lookup"><span data-stu-id="94b41-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<span data-ttu-id="94b41-153">Użycie tej opcji jest preferowane, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybutem stanowi kontrakt dla operacji wykonywanych przez usługę, które mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="94b41-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="94b41-154">Usługa WCF jest świadczona przez zdefiniowanie jednego lub większej liczby punktów końcowych WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="94b41-155">Punkt końcowy jest definiowany przy użyciu adresu, powiązania i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="94b41-156">Adres definiuje lokalizację usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-156">The address defines where the service is located.</span></span> <span data-ttu-id="94b41-157">Powiązanie określa sposób komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="94b41-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="94b41-158">Kontrakt usługi definiuje operacje, które mogą być wykonywane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="94b41-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="94b41-159">Kontrakt usługi jest zwykle definiowany jako pierwszy, przez dodanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> do interfejsu:</span><span class="sxs-lookup"><span data-stu-id="94b41-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="94b41-160">Określa, że interfejs definiuje kontrakt usługi WCF <xref:System.ServiceModel.OperationContractAttribute> i wskazuje, które z metod interfejsu definiują operacje kontraktu usługi. <xref:System.ServiceModel.ServiceContractAttribute></span><span class="sxs-lookup"><span data-stu-id="94b41-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="94b41-161">Po zdefiniowaniu kontraktu usługi jest on implementowany w klasie, przez posiadanie klasy implementującej interfejs, w którym jest zdefiniowany kontrakt usługi:</span><span class="sxs-lookup"><span data-stu-id="94b41-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="94b41-162">Klasa implementująca kontrakt usługi jest określana jako typ usługi w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="94b41-163">Następnym krokiem jest skojarzenie adresu i powiązania z typem usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="94b41-164">Zwykle jest to wykonywane w pliku konfiguracji, edytując plik bezpośrednio lub korzystając z edytora konfiguracji dostarczonego z WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="94b41-165">Oto przykład pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="94b41-165">Here is an example of a configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

<span data-ttu-id="94b41-166">Powiązanie określa zestaw protokołów do komunikacji z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="94b41-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="94b41-167">Poniższa tabela zawiera listę powiązań dostarczonych przez system, które reprezentują typowe opcje.</span><span class="sxs-lookup"><span data-stu-id="94b41-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="94b41-168">Nazwa</span><span class="sxs-lookup"><span data-stu-id="94b41-168">Name</span></span>|<span data-ttu-id="94b41-169">Cel</span><span class="sxs-lookup"><span data-stu-id="94b41-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="94b41-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-170">BasicHttpBinding</span></span>|<span data-ttu-id="94b41-171">Współdziałanie z usługami sieci Web i klientami obsługującymi protokół WS-BasicProfile 1,1 i podstawowy profil zabezpieczeń 1,0.</span><span class="sxs-lookup"><span data-stu-id="94b41-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="94b41-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-172">WSHttpBinding</span></span>|<span data-ttu-id="94b41-173">Współdziałanie z usługami sieci Web i klientami, które obsługują protokoły WS-\* za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="94b41-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="94b41-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-174">WSDualHttpBinding</span></span>|<span data-ttu-id="94b41-175">Bezstronna komunikacja HTTP, przez którą odbiorca wiadomości początkowej nie odpowiada bezpośrednio nadawcy inicjującemu, ale może przesłać dowolną liczbę odpowiedzi w danym okresie, używając protokołu HTTP zgodnego z protokołami WS-\*.</span><span class="sxs-lookup"><span data-stu-id="94b41-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="94b41-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-176">WSFederationBinding</span></span>|<span data-ttu-id="94b41-177">Komunikacja HTTP, w której dostęp do zasobów usługi może być kontrolowany na podstawie poświadczeń wystawionych przez jawnie określonego dostawcę poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="94b41-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="94b41-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-178">NetTcpBinding</span></span>|<span data-ttu-id="94b41-179">Bezpieczna, niezawodna i wysoce wydajna komunikacja między jednostkami oprogramowania WCF w sieci.</span><span class="sxs-lookup"><span data-stu-id="94b41-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="94b41-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="94b41-181">Bezpieczna, niezawodna i wysoce wydajna komunikacja między jednostkami oprogramowania WCF na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="94b41-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="94b41-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-182">NetMsmqBinding</span></span>|<span data-ttu-id="94b41-183">Komunikacja między jednostkami oprogramowania WCF przy użyciu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="94b41-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="94b41-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="94b41-185">Komunikacja między jednostką oprogramowania WCF i inną jednostką oprogramowania przy użyciu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="94b41-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="94b41-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="94b41-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="94b41-187">Komunikacja między jednostkami oprogramowania WCF przy użyciu sieci równorzędnej systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94b41-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="94b41-188">Powiązanie <xref:System.ServiceModel.BasicHttpBinding>dostarczone z systemem, zawiera zestaw protokołów obsługiwanych przez usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="94b41-189">Niestandardowe powiązania dla aplikacji WCF są łatwo zdefiniowane jako kolekcje klas elementów powiązania używanych przez program WCF do implementowania poszczególnych protokołów.</span><span class="sxs-lookup"><span data-stu-id="94b41-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="94b41-190">Nowe elementy powiązania można napisać, aby reprezentować dodatkowe protokoły.</span><span class="sxs-lookup"><span data-stu-id="94b41-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="94b41-191">Wewnętrzne zachowanie typów usług można dostosować przy użyciu właściwości rodziny klas o nazwie Behaviors.</span><span class="sxs-lookup"><span data-stu-id="94b41-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="94b41-192">W tym miejscu Klasa jest używana do określenia, czy typ usługi ma być wielowątkowy. <xref:System.ServiceModel.ServiceBehaviorAttribute></span><span class="sxs-lookup"><span data-stu-id="94b41-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="94b41-193">Niektóre zachowania, takie <xref:System.ServiceModel.ServiceBehaviorAttribute>jak, są atrybutami.</span><span class="sxs-lookup"><span data-stu-id="94b41-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="94b41-194">Inne osoby, które mają właściwości, które Administratorzy chcą ustawić, mogą być modyfikowane w konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="94b41-195">W przypadku typów usług programistycznych należy wykonać <xref:System.ServiceModel.OperationContext> częste użycie klasy.</span><span class="sxs-lookup"><span data-stu-id="94b41-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="94b41-196">Jej właściwość <xref:System.ServiceModel.OperationContext.Current%2A> statyczna zapewnia dostęp do informacji dotyczących kontekstu, w którym jest uruchomiona operacja.</span><span class="sxs-lookup"><span data-stu-id="94b41-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="94b41-197"><xref:System.ServiceModel.OperationContext>jest podobna do <xref:System.Web.HttpContext> klas i <xref:System.EnterpriseServices.ContextUtil> .</span><span class="sxs-lookup"><span data-stu-id="94b41-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="94b41-198">Hosting</span><span class="sxs-lookup"><span data-stu-id="94b41-198">Hosting</span></span>

<span data-ttu-id="94b41-199">Usługi sieci Web ASP.NET są kompilowane do zestawu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="94b41-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="94b41-200">Plik o nazwie plik usługi jest dostarczany z rozszerzeniem ASMX i zawiera `@ WebService` dyrektywę identyfikującą klasę, która zawiera kod dla usługi i zestaw, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="94b41-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="94b41-201">Plik usługi jest kopiowany do katalogu głównego aplikacji ASP.NET w programie Internet Information Services (IIS), a zestaw jest kopiowany do podkatalogu \Bin tego katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="94b41-202">Aplikacja jest następnie dostępna przy użyciu adresu URL (Uniform Resource Locator) pliku usługi w katalogu głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="94b41-203">Usługi WCF mogą być łatwo hostowane w usługach IIS 5,1 lub 6,0, w ramach usługi aktywacji procesów systemu Windows (WAS), która jest dostępna jako część usług IIS 7,0 i w ramach dowolnej aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="94b41-204">Aby hostować usługę w usługach IIS 5,1 lub 6,0, usługa musi używać protokołu HTTP jako protokołu transportowego komunikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="94b41-205">Aby hostować usługę w usługach IIS 5,1, 6,0 lub w ramach programu, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="94b41-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="94b41-206">Kompiluj typ usługi do zestawu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="94b41-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="94b41-207">Utwórz plik usługi z rozszerzeniem SVC z `@ ServiceHost` dyrektywą w celu zidentyfikowania typu usługi:</span><span class="sxs-lookup"><span data-stu-id="94b41-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="94b41-208">Skopiuj plik usługi do katalogu wirtualnego, a następnie zestaw do podkatalogu \Bin tego katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="94b41-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="94b41-209">Skopiuj plik konfiguracji do katalogu wirtualnego, a następnie nadaj mu nazwę Web. config.</span><span class="sxs-lookup"><span data-stu-id="94b41-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="94b41-210">Następnie aplikacja jest dostępna przy użyciu adresu URL pliku usługi w katalogu głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="94b41-211">Aby hostować usługę WCF w ramach aplikacji .NET, skompiluj typ usługi do zestawu biblioteki klas, do którego odwołuje się aplikacja, i zaprogramowanie aplikacji do hostowania usługi <xref:System.ServiceModel.ServiceHost> przy użyciu klasy.</span><span class="sxs-lookup"><span data-stu-id="94b41-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="94b41-212">Poniżej znajduje się przykład wymaganego programowania podstawowego:</span><span class="sxs-lookup"><span data-stu-id="94b41-212">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="94b41-213">Ten przykład pokazuje, jak adresy dla co najmniej jednego protokołu transportowego są określone w konstrukcji <xref:System.ServiceModel.ServiceHost>a.</span><span class="sxs-lookup"><span data-stu-id="94b41-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="94b41-214">Te adresy są określane jako adresy podstawowe.</span><span class="sxs-lookup"><span data-stu-id="94b41-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="94b41-215">Adres podany dla dowolnego punktu końcowego usługi WCF jest adresem względem adresu podstawowego hosta punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94b41-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="94b41-216">Host może mieć jeden adres podstawowy dla każdego protokołu transportu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="94b41-217">W przykładowej konfiguracji w poprzednim pliku <xref:System.ServiceModel.BasicHttpBinding> konfiguracyjnym wybrane dla punktu końcowego używa protokołu HTTP jako protokołu transportowego, więc adres `EchoService`punktu końcowego jest określany względem adresu podstawowego http hosta.</span><span class="sxs-lookup"><span data-stu-id="94b41-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="94b41-218">W przypadku hosta w poprzednim przykładzie adres podstawowy HTTP to `http://www.contoso.com:8000/`.</span><span class="sxs-lookup"><span data-stu-id="94b41-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="94b41-219">W przypadku usługi hostowanej w ramach usług IIS lub jako adres podstawowy to adres URL pliku usługi usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="94b41-220">Tylko usługi hostowane w usługach IIS lub były skonfigurowane z użyciem protokołu HTTP jako protokołu transportowego, można użyć opcji Tryb zgodności programu WCF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="94b41-221">Włączenie tej opcji wymaga wykonania następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="94b41-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="94b41-222">Programista musi dodać <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atrybut do typu usługi i określić, że tryb zgodności ASP.NET jest dozwolony lub wymagany.</span><span class="sxs-lookup"><span data-stu-id="94b41-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="94b41-223">Administrator musi skonfigurować aplikację tak, aby korzystała z trybu zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="94b41-224">Aplikacje WCF można także skonfigurować do używania. asmx jako rozszerzenia dla plików usługi, a nie SVC.</span><span class="sxs-lookup"><span data-stu-id="94b41-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="94b41-225">Ta opcja umożliwia modyfikację klientów skonfigurowanych do korzystania z adresów URL plików usługi asmx podczas modyfikowania usługi do korzystania z programu WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="94b41-226">Tworzenie aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="94b41-226">Client Development</span></span>

<span data-ttu-id="94b41-227">Klienci dla usług sieci Web ASP.NET są generowane przy użyciu narzędzia wiersza polecenia, WSDL. exe, który udostępnia adres URL pliku. asmx jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="94b41-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="94b41-228">Odpowiednie narzędzie dostarczone przez funkcję WCF to [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="94b41-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="94b41-229">Generuje moduł kodu z definicją kontraktu usługi i definicją klasy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="94b41-230">Generuje również plik konfiguracji z adresem i powiązaniem usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="94b41-231">W programowaniu klienta usługi zdalnej ogólnie zaleca się, aby program był zgodny ze wzorcem asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="94b41-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="94b41-232">Kod wygenerowany przez narzędzie WSDL. exe zawsze zapewnia domyślnie zarówno wzorzec synchroniczny, jak i asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="94b41-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="94b41-233">Kod wygenerowany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może zapewnić dla obu wzorców.</span><span class="sxs-lookup"><span data-stu-id="94b41-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="94b41-234">Domyślnie oferuje wzorzec synchroniczny.</span><span class="sxs-lookup"><span data-stu-id="94b41-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="94b41-235">Jeśli narzędzie jest wykonywane z `/async` przełącznikiem, wygenerowany kod zapewnia wzorzec asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="94b41-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="94b41-236">Nie ma gwarancji, że nazwy w klasach klienta WCF generowane przez ASP. Narzędzie NET. exe języka WSDL domyślnie dopasowuje nazwy w klasach klienta WCF generowanych przez narzędzie Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="94b41-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="94b41-237">W szczególności nazwy właściwości klas, które mają być serializowane przy użyciu <xref:System.Xml.Serialization.XmlSerializer> , domyślnie mają właściwość sufiks w kodzie wygenerowanym przez narzędzie Svcutil. exe, które nie jest przypadkiem narzędzia WSDL. exe.</span><span class="sxs-lookup"><span data-stu-id="94b41-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="94b41-238">Reprezentacja komunikatów</span><span class="sxs-lookup"><span data-stu-id="94b41-238">Message Representation</span></span>

<span data-ttu-id="94b41-239">Nagłówki komunikatów protokołu SOAP wysyłane i odbierane przez usługi sieci Web ASP.NET można dostosować.</span><span class="sxs-lookup"><span data-stu-id="94b41-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="94b41-240">Klasa pochodzi od <xref:System.Web.Services.Protocols.SoapHeader> , aby zdefiniować strukturę nagłówka, a <xref:System.Web.Services.Protocols.SoapHeaderAttribute> następnie służy do wskazywania obecności nagłówka.</span><span class="sxs-lookup"><span data-stu-id="94b41-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

<span data-ttu-id="94b41-241">WCF udostępnia atrybuty, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute>, i <xref:System.ServiceModel.MessageBodyMemberAttribute> opisują strukturę komunikatów protokołu SOAP wysyłanych i odbieranych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="94b41-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

<span data-ttu-id="94b41-242">Ta składnia daje jawną reprezentację struktury komunikatów, podczas gdy struktura komunikatów jest implikowana przez kod usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="94b41-243">Ponadto w składni ASP.NET nagłówki wiadomości są reprezentowane jako właściwości usługi, takie jak `ProtocolHeader` właściwość w poprzednim przykładzie, natomiast w składni programu WCF są one bardziej dokładnie reprezentowane jako właściwości komunikatów.</span><span class="sxs-lookup"><span data-stu-id="94b41-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="94b41-244">Ponadto WCF zezwala na Dodawanie nagłówków wiadomości do konfiguracji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="94b41-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

<span data-ttu-id="94b41-245">Ta opcja pozwala uniknąć dowolnych odwołań do nagłówków protokołu infrastruktury w kodzie dla klienta lub usługi: nagłówki są dodawane do komunikatów ze względu na sposób konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94b41-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="94b41-246">Opis usługi</span><span class="sxs-lookup"><span data-stu-id="94b41-246">Service Description</span></span>

<span data-ttu-id="94b41-247">Wydawanie żądania HTTP GET dla pliku. asmx usługi sieci Web ASP.NET za pomocą języka WSDL zapytania powoduje, że ASP.NET do wygenerowania kodu WSDL w celu opisania usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="94b41-248">Zwraca ten plik WSDL jako odpowiedź do żądania.</span><span class="sxs-lookup"><span data-stu-id="94b41-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="94b41-249">ASP.NET 2,0 może sprawdzić, czy usługa jest zgodna z profilem Basic 1,1 w organizacji usługi sieci Web — współdziałanie (WS-I), a następnie wstawić do niej zastrzeżenie, że usługa jest zgodna ze specyfikacją WSDL.</span><span class="sxs-lookup"><span data-stu-id="94b41-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="94b41-250">Jest to wykonywane przy użyciu `ConformsTo` parametrów `EmitConformanceClaims` <xref:System.Web.Services.WebServiceBindingAttribute> i atrybutu.</span><span class="sxs-lookup"><span data-stu-id="94b41-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="94b41-251">WSDL, który ASP.NET generuje dla usługi, można dostosować.</span><span class="sxs-lookup"><span data-stu-id="94b41-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="94b41-252">Dostosowania są wykonywane przez utworzenie klasy <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pochodnej, aby dodać elementy do WSDL.</span><span class="sxs-lookup"><span data-stu-id="94b41-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="94b41-253">Wydawanie żądania HTTP GET za pomocą języka WSDL zapytania dla pliku SVC usługi WCF za pomocą punktu końcowego HTTP hostowanego w usługach IIS 51, 6,0 lub zostało spowodowane przez program WCF w celu opisywania usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="94b41-254">Wygenerowanie żądania HTTP GET przy użyciu zapytania WSDL dla adresu podstawowego HTTP usługi hostowanej w aplikacji .NET ma ten sam efekt, jeśli httpGetEnabled jest ustawiona na wartość true.</span><span class="sxs-lookup"><span data-stu-id="94b41-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="94b41-255">Jednak funkcja WCF reaguje na żądania WS-MetadataExchange za pomocą języka WSDL, który generuje do opisywania usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="94b41-256">Usługi sieci Web ASP.NET nie mają wbudowanej obsługi żądań WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="94b41-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="94b41-257">Język WSDL generowany przez funkcję WCF może być szeroko dostosowany.</span><span class="sxs-lookup"><span data-stu-id="94b41-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="94b41-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Klasa zawiera niektóre obiekty do dostosowania WSDL.</span><span class="sxs-lookup"><span data-stu-id="94b41-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="94b41-259">Program WCF można również skonfigurować tak, aby nie generował WSDL, ale zamiast tego użyć statycznego pliku WSDL pod podanym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="94b41-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a><span data-ttu-id="94b41-260">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="94b41-260">Exception Handling</span></span>

<span data-ttu-id="94b41-261">W usługach sieci Web ASP.NET Nieobsłużone wyjątki są zwracane do klientów jako błędy SOAP.</span><span class="sxs-lookup"><span data-stu-id="94b41-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="94b41-262">Można również jawnie zgłosić wystąpienia <xref:System.Web.Services.Protocols.SoapException> klasy i mieć większą kontrolę nad zawartością błędu protokołu SOAP, który jest przesyłany do klienta.</span><span class="sxs-lookup"><span data-stu-id="94b41-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="94b41-263">W usługach WCF Nieobsłużone wyjątki nie są zwracane klientom jako błędy protokołu SOAP, aby zapobiec przypadkowemu ujawnieniu poufnych informacji przez wyjątki.</span><span class="sxs-lookup"><span data-stu-id="94b41-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="94b41-264">Ustawienie konfiguracji zapewnia Nieobsłużone wyjątki zwracane klientom na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="94b41-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="94b41-265">Aby zwrócić do klientów błędy SOAP, można zgłosić wystąpienia typu ogólnego, <xref:System.ServiceModel.FaultException%601>przy użyciu typu kontraktu danych jako typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="94b41-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="94b41-266">Możesz również dodać <xref:System.ServiceModel.FaultContractAttribute> atrybuty do operacji, aby określić błędy, które może przynieść operacja.</span><span class="sxs-lookup"><span data-stu-id="94b41-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

<span data-ttu-id="94b41-267">Powoduje to, że potencjalne błędy są anonsowane w języku WSDL dla usługi, dzięki czemu programiści mogą przewidzieć, które błędy może wynikać z operacji, i napisać odpowiednie instrukcje catch.</span><span class="sxs-lookup"><span data-stu-id="94b41-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a><span data-ttu-id="94b41-268">Zarządzanie stanem</span><span class="sxs-lookup"><span data-stu-id="94b41-268">State Management</span></span>

<span data-ttu-id="94b41-269">Klasa użyta do zaimplementowania usługi sieci Web ASP.NET może być <xref:System.Web.Services.WebService>pochodną.</span><span class="sxs-lookup"><span data-stu-id="94b41-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="94b41-270">W takim przypadku Klasa może być zaprogramowany, aby użyć <xref:System.Web.Services.WebService> właściwości kontekstu klasy podstawowej w celu <xref:System.Web.HttpContext> uzyskania dostępu do obiektu.</span><span class="sxs-lookup"><span data-stu-id="94b41-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="94b41-271"><xref:System.Web.HttpContext> Obiekt może służyć do aktualizowania i pobierania informacji o stanie aplikacji przy użyciu właściwości aplikacji i może służyć do aktualizowania i pobierania informacji o stanie sesji przy użyciu właściwości sesji.</span><span class="sxs-lookup"><span data-stu-id="94b41-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="94b41-272">ASP.NET zapewnia znaczącą kontrolę nad tym, gdzie informacje o stanie sesji, do których uzyskuje <xref:System.Web.HttpContext> się dostęp przy użyciu właściwości Session w rzeczywistości, są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="94b41-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="94b41-273">Mogą być przechowywane w plikach cookie, w bazie danych, w pamięci bieżącego serwera lub w pamięci określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="94b41-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="94b41-274">Wybór jest dokonywany w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="94b41-275">Funkcja WCF zapewnia Rozszerzalne obiekty do zarządzania stanem.</span><span class="sxs-lookup"><span data-stu-id="94b41-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="94b41-276">Rozszerzalne obiekty to obiekty, <xref:System.ServiceModel.IExtensibleObject%601>które implementują.</span><span class="sxs-lookup"><span data-stu-id="94b41-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="94b41-277">Najważniejsze Rozszerzalne obiekty to <xref:System.ServiceModel.ServiceHostBase> i. <xref:System.ServiceModel.InstanceContext></span><span class="sxs-lookup"><span data-stu-id="94b41-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="94b41-278">`ServiceHostBase`pozwala zachować stan, w którym wszystkie wystąpienia wszystkich typów usług na tym samym hoście mogą uzyskać dostęp, a jednocześnie `InstanceContext` pozwala zachować stan, do którego można uzyskać dostęp za pomocą dowolnego kodu uruchomionego w ramach tego samego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="94b41-279">W tym miejscu typ usługi, `TradingSystem`,,, <xref:System.ServiceModel.ServiceBehaviorAttribute> określa, że wszystkie wywołania z tego samego wystąpienia klienta programu WCF są kierowane do tego samego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="94b41-280">Klasa, `DealData`, definiuje stan, do którego można uzyskać dostęp za pomocą dowolnego kodu uruchomionego w tym samym wystąpieniu typu usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="94b41-281">W kodzie typu usługi, który implementuje jedną z operacji kontraktu usługi, `DealData` obiekt stanu jest dodawany do stanu bieżącego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="94b41-282">Ten obiekt stanu może następnie zostać pobrany i zmodyfikowany przez kod implementujący inny element operacji kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="94b41-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="94b41-283">Program ASP.NET zapewnia kontrolę nad tym, gdzie w rzeczywistości <xref:System.Web.HttpContext> są przechowywane informacje o stanie w klasie, WCF, co najmniej w wersji wstępnej, nie zapewnia kontroli nad tym, gdzie są przechowywane Rozszerzalne obiekty.</span><span class="sxs-lookup"><span data-stu-id="94b41-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="94b41-284">Stanowi to bardzo najlepszy powód wyboru ASP.NET tryb zgodności dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="94b41-285">Jeśli konfigurowalne zarządzanie stanem jest bezwzględne, to w trybie zgodności ASP.NET można używać obiektów <xref:System.Web.HttpContext> klasy dokładnie tak, jak są one używane w ASP.NET, a także do konfigurowania informacji o stanie zarządzanych przy użyciu <xref:System.Web.HttpContext> Klasa jest przechowywana.</span><span class="sxs-lookup"><span data-stu-id="94b41-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="94b41-286">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="94b41-286">Security</span></span>

<span data-ttu-id="94b41-287">Opcje zabezpieczania usług sieci Web ASP.NET są tymi, które służą do zabezpieczania dowolnej aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="94b41-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="94b41-288">Ponieważ aplikacje WCF mogą być hostowane nie tylko w ramach usług IIS, ale również w ramach dowolnego pliku wykonywalnego platformy .NET, opcje zabezpieczania aplikacji WCF muszą być niezależne od obiektów usług IIS.</span><span class="sxs-lookup"><span data-stu-id="94b41-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="94b41-289">Dostępne są jednak funkcje usługi sieci Web ASP.NET dla usług WCF działających w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="94b41-290">Bezpieczeństw Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="94b41-290">Security: Authentication</span></span>

<span data-ttu-id="94b41-291">Usługi IIS zapewniają funkcje do kontrolowania dostępu do aplikacji, w których można wybrać dostęp anonimowy lub wiele różnych trybów uwierzytelniania: Uwierzytelnianie systemu Windows, uwierzytelnianie szyfrowane, uwierzytelnianie podstawowe i uwierzytelnianie .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="94b41-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="94b41-292">Opcji uwierzytelniania systemu Windows można użyć do kontrolowania dostępu do usług sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="94b41-293">Jeśli jednak aplikacje WCF są hostowane w usługach IIS, usługi IIS muszą być skonfigurowane tak, aby zezwalały na dostęp anonimowy do aplikacji, dzięki czemu uwierzytelnianie może być zarządzane przez usługę WCF, która obsługuje uwierzytelnianie systemu Windows między różnymi innymi opcjami.</span><span class="sxs-lookup"><span data-stu-id="94b41-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="94b41-294">Inne opcje, które są wbudowane, obejmują tokeny username, certyfikaty X. 509, tokeny SAML i karty CardSpace, ale można również zdefiniować niestandardowe mechanizmy uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="94b41-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="94b41-295">Bezpieczeństw Personifikacja</span><span class="sxs-lookup"><span data-stu-id="94b41-295">Security: Impersonation</span></span>

<span data-ttu-id="94b41-296">ASP.NET udostępnia element tożsamości, za pomocą którego można przeprowadzić usługę sieci Web ASP.NET w celu personifikacji określonego użytkownika lub poświadczeń użytkownika, które są dostarczane z bieżącym żądaniem.</span><span class="sxs-lookup"><span data-stu-id="94b41-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="94b41-297">Tego elementu można użyć do skonfigurowania personifikacji w aplikacjach WCF działających w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="94b41-298">System konfiguracji WCF udostępnia swój własny element tożsamości służący do wyznaczania określonego użytkownika do personifikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="94b41-299">Ponadto klienci i usługi WCF mogą być skonfigurowane niezależnie do personifikacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="94b41-300">Klientów można skonfigurować do personifikacji bieżącego użytkownika podczas przesyłania żądań.</span><span class="sxs-lookup"><span data-stu-id="94b41-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="94b41-301">Operacje usługi można skonfigurować w taki sposób, aby personifikowanie poświadczeń użytkownika zostało zapewnione przy użyciu bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="94b41-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="94b41-302">Bezpieczeństw Autoryzacja za pomocą list Access Control</span><span class="sxs-lookup"><span data-stu-id="94b41-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="94b41-303">Listy Access Control (ACL) mogą służyć do ograniczania dostępu do plików. asmx.</span><span class="sxs-lookup"><span data-stu-id="94b41-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="94b41-304">Listy ACL plików programu WCF. svc są jednak ignorowane, z wyjątkiem trybu zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="94b41-305">Bezpieczeństw Autoryzacja oparta na rolach</span><span class="sxs-lookup"><span data-stu-id="94b41-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="94b41-306">Opcji uwierzytelniania systemu Windows w usługach IIS można używać w połączeniu z elementem autoryzacji udostępnianym przez język konfiguracji ASP.NET, aby ułatwić autoryzację opartą na rolach dla usług sieci Web ASP.NET w oparciu o grupy systemu Windows, do których są przypisani użytkownicy .</span><span class="sxs-lookup"><span data-stu-id="94b41-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="94b41-307">W ASP.NET 2,0 wprowadzono bardziej ogólny mechanizm autoryzacji oparty na rolach: dostawcy ról.</span><span class="sxs-lookup"><span data-stu-id="94b41-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="94b41-308">Dostawcy ról to klasy, które implementują podstawowy interfejs do uzyskiwania informacji o rolach przypisanych do użytkownika, ale każdy dostawca roli wie, jak pobrać te informacje z innego źródła.</span><span class="sxs-lookup"><span data-stu-id="94b41-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="94b41-309">ASP.NET 2,0 zapewnia dostawcę roli, który może pobierać przypisania ról z bazy danych Microsoft SQL Server, a druga, która może pobierać przypisania ról z Menedżera autoryzacji systemu Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="94b41-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="94b41-310">Mechanizm dostawcy roli można faktycznie używać niezależnie od ASP.NET w dowolnej aplikacji platformy .NET, w tym aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="94b41-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="94b41-311">Poniższa Konfiguracja przykładowa aplikacji WCF pokazuje, jak używać dostawcy roli ASP.NET jest opcją wybraną za <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>pomocą.</span><span class="sxs-lookup"><span data-stu-id="94b41-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a><span data-ttu-id="94b41-312">Bezpieczeństw Autoryzacja oparta na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="94b41-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="94b41-313">Jednym z najważniejszych innowacji usługi WCF jest kompleksowa obsługa autoryzacji dostępu do chronionych zasobów w oparciu o oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="94b41-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="94b41-314">Oświadczenia składają się z typu, praw i wartości, na przykład licencji na sterowniki.</span><span class="sxs-lookup"><span data-stu-id="94b41-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="94b41-315">Tworzy zestaw oświadczeń dotyczących okaziciela, z których jedna jest datą urodzenia okaziciela.</span><span class="sxs-lookup"><span data-stu-id="94b41-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="94b41-316">Typ tego zgłoszenia to data urodzenia, podczas gdy wartość żądania jest datą urodzenia sterownika.</span><span class="sxs-lookup"><span data-stu-id="94b41-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="94b41-317">Prawo, że w odniesieniu do osoby korzystającej z roszczeń określa, co może zrobić, z wartością żądania.</span><span class="sxs-lookup"><span data-stu-id="94b41-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="94b41-318">W przypadku roszczeń dotyczących daty urodzenia sterownika, prawo jest posiadanie: kierowca ma tę datę urodzenia, ale nie może na przykład zmienić.</span><span class="sxs-lookup"><span data-stu-id="94b41-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="94b41-319">Autoryzacja oparta na oświadczeniach obejmuje autoryzację opartą na rolach, ponieważ role są typem oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="94b41-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="94b41-320">Autoryzacja oparta na oświadczeniach jest realizowana poprzez porównanie zestawu oświadczeń z wymaganiami dostępu operacji i, w zależności od wyniku porównania, przyznanie lub odmowa dostępu do operacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="94b41-321">W programie WCF można określić klasę, która ma być używana do uruchamiania autoryzacji opartej na oświadczeniach, przez przypisanie wartości do `ServiceAuthorizationManager` <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>właściwości.</span><span class="sxs-lookup"><span data-stu-id="94b41-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="94b41-322">Klasy służące do uruchamiania autoryzacji opartej na oświadczeniach <xref:System.ServiceModel.ServiceAuthorizationManager>muszą pochodzić od `AccessCheck()`elementu, który ma tylko jedną metodę przesłonięcia.</span><span class="sxs-lookup"><span data-stu-id="94b41-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="94b41-323">Funkcja WCF wywołuje tę metodę za każdym razem, gdy zostanie wywołana operacja usługi i <xref:System.ServiceModel.OperationContext> udostępnia obiekt, który ma oświadczenia dla użytkownika w jego `ServiceSecurityContext.AuthorizationContext` właściwości.</span><span class="sxs-lookup"><span data-stu-id="94b41-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="94b41-324">Program WCF wykonuje zadania składania oświadczeń dotyczących użytkownika z dowolnego tokenu zabezpieczającego, który użytkownik dostarczył do uwierzytelniania, co pozostawia zadanie oceny, czy te oświadczenia są wystarczające dla danej operacji.</span><span class="sxs-lookup"><span data-stu-id="94b41-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="94b41-325">Usługa WCF automatycznie łączy oświadczenia z dowolnego rodzaju tokenów zabezpieczających, ponieważ sprawia, że kod autoryzacji jest oparty na oświadczeniach całkowicie niezależnie od mechanizmu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="94b41-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="94b41-326">Z kolei autoryzacja przy użyciu list ACL lub ról w ASP.NET jest ściśle związana z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="94b41-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="94b41-327">Bezpieczeństw Poufne</span><span class="sxs-lookup"><span data-stu-id="94b41-327">Security: Confidentiality</span></span>

<span data-ttu-id="94b41-328">Poufność komunikatów wymienianych z usługami sieci Web ASP.NET można zapewnić na poziomie transportu przez skonfigurowanie aplikacji w usługach IIS do korzystania z protokołu HTTPS (Secure Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="94b41-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="94b41-329">Tę samą funkcję można wykonać w przypadku aplikacji WCF hostowanych w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="94b41-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="94b41-330">Jednak aplikacje WCF hostowane poza usługami IIS można także skonfigurować do korzystania z protokołu Secure Transport Protocol.</span><span class="sxs-lookup"><span data-stu-id="94b41-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="94b41-331">Ważniejsze aplikacje usług WCF można także skonfigurować w celu zabezpieczenia komunikatów przed ich transportem przy użyciu protokołu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="94b41-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="94b41-332">Zabezpieczenie tylko treści wiadomości za pomocą usługi WS-Security pozwala na ich przekazanie poufne w ramach pośredników przed osiągnięciem ostatecznego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="94b41-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="94b41-333">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="94b41-333">Globalization</span></span>

<span data-ttu-id="94b41-334">Język konfiguracji ASP.NET umożliwia określenie kultury dla poszczególnych usług.</span><span class="sxs-lookup"><span data-stu-id="94b41-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="94b41-335">Funkcja WCF nie obsługuje tego ustawienia konfiguracji, z wyjątkiem trybu zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="94b41-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="94b41-336">Aby zlokalizować usługę WCF, która nie korzysta z trybu zgodności ASP.NET, skompiluj typ usługi do zestawów specyficznych dla kultury i mają oddzielne punkty końcowe specyficzne dla kultury dla każdego zestawu specyficznego dla kultury.</span><span class="sxs-lookup"><span data-stu-id="94b41-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="94b41-337">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94b41-337">See also</span></span>

- [<span data-ttu-id="94b41-338">Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów</span><span class="sxs-lookup"><span data-stu-id="94b41-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
