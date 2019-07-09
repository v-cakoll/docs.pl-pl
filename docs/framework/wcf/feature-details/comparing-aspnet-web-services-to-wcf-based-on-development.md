---
title: Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: 8b0e26f0b76ee56d06c426cd3c11b169a74b1896
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663368"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="fada0-102">Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych</span><span class="sxs-lookup"><span data-stu-id="fada0-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="fada0-103">Windows Communication Foundation (WCF) znajduje się opcja Tryb zgodności ASP.NET umożliwiają aplikacjom WCF zaprogramowane i skonfigurowane, takich jak usługi sieci Web platformy ASP.NET i naśladować ich zachowania.</span><span class="sxs-lookup"><span data-stu-id="fada0-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="fada0-104">W poniższych sekcjach porównano usługi sieci Web platformy ASP.NET i WCF oparte na co jest wymagane do tworzenia aplikacji przy użyciu obu technologii.</span><span class="sxs-lookup"><span data-stu-id="fada0-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="fada0-105">Reprezentacja danych</span><span class="sxs-lookup"><span data-stu-id="fada0-105">Data Representation</span></span>

<span data-ttu-id="fada0-106">Tworzenie usługi sieci Web programu ASP.NET zwykle zaczyna się od definiowania wszystkich typów złożonych danych, które jest użycie usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="fada0-107">ASP.NET opiera się na <xref:System.Xml.Serialization.XmlSerializer> do translacji dane reprezentowane przez typów programu .NET Framework do pliku XML w celu przesłania go do lub z usługi i translację dane odebrane w formacie XML do obiektów platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fada0-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="fada0-108">Definiowanie typów złożonych danych, które jest użycie usługi ASP.NET wymaga definicji programu .NET Framework klas <xref:System.Xml.Serialization.XmlSerializer> może wykonywać serializację do i z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="fada0-109">Takich klas mogą być zapisywane ręcznie lub generowany na podstawie definicje typów w schemacie XML przy użyciu wiersza polecenia XML schematów/danych typów obsługę narzędzia, xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="fada0-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="fada0-110">Oto lista kluczowych problemów, aby dowiedzieć się, gdy Definiowanie .NET Framework klas <xref:System.Xml.Serialization.XmlSerializer> może wykonywać serializację do i z pliku XML:</span><span class="sxs-lookup"><span data-stu-id="fada0-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="fada0-111">Tylko pola publiczne i właściwości obiektów .NET Framework są tłumaczone na XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="fada0-112">Wystąpienia klas kolekcji może być Zserializowany w formacie XML, tylko wtedy, gdy klasy implementuje albo <xref:System.Collections.IEnumerable> lub <xref:System.Collections.ICollection> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fada0-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="fada0-113">Klasy, które implementują <xref:System.Collections.IDictionary> interfejsu, takich jak <xref:System.Collections.Hashtable>, nie może być serializowany do XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="fada0-114">Świetnie atrybutu wiele typów w <xref:System.Xml.Serialization> przestrzeni nazw mogą być dodawane do klasy .NET Framework i jej elementów członkowskich, aby kontrolować sposób wystąpienia klasy są reprezentowane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="fada0-115">Tworzenie aplikacji WCF zwykle także rozpoczyna się od definicji typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="fada0-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="fada0-116">Usługi WCF może również używać tych samych typów programu .NET Framework jako usług sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="fada0-117">WCF<xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> mogą być dodawane do typów programu .NET Framework, aby wskazać, że wystąpień typu mają być serializowany do XML i które pola lub właściwości typu mają być Zserializowany, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fada0-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

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

<span data-ttu-id="fada0-118"><xref:System.Runtime.Serialization.DataContractAttribute> Oznacza, że zero lub więcej z typu pola lub właściwości mają być Zserializowany, podczas gdy <xref:System.Runtime.Serialization.DataMemberAttribute> wskazuje, że określonego pola lub właściwości jest serializacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="fada0-119"><xref:System.Runtime.Serialization.DataContractAttribute> Można zastosować do klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fada0-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="fada0-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Mogą być stosowane do pola lub właściwości i pola i właściwości, do których zastosowano ten atrybut może być publicznym lub prywatnym.</span><span class="sxs-lookup"><span data-stu-id="fada0-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="fada0-121">Wystąpień typów, które mają <xref:System.Runtime.Serialization.DataContractAttribute> stosowane do ich są określane jako dane zamówień w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="fada0-122">Są one serializacji do formatu XML przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fada0-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="fada0-123">Poniżej przedstawiono listę istotne różnice między <xref:System.Runtime.Serialization.DataContractSerializer> i przy użyciu <xref:System.Xml.Serialization.XmlSerializer> i różne atrybuty <xref:System.Xml.Serialization> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fada0-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="fada0-124"><xref:System.Xml.Serialization.XmlSerializer> i atrybutów <xref:System.Xml.Serialization> przestrzeni nazw są zaprojektowane, aby umożliwić do mapowania typów programu .NET Framework na dowolny prawidłowy typ zdefiniowanej w schemacie XML, a więc zapewniają dla bardzo precyzyjną kontrolę nad tym, jak typ są reprezentowane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="fada0-125"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> zapewniają bardzo mało kontrolę nad jak typ są reprezentowane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="fada0-126">Można określić tylko obszary nazw i nazwy, używana do reprezentowania typu i jego pól lub właściwości w pliku XML i kolejność, w jakiej pola i właściwości są wyświetlane w pliku XML:</span><span class="sxs-lookup"><span data-stu-id="fada0-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

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

  <span data-ttu-id="fada0-127">Wszystkie inne informacje o strukturze XML używany do reprezentowania typ architektury .NET jest określana przez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fada0-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="fada0-128">Przez nie pozwala na znacznie kontrolę nad jak typ ma być reprezentowane w formacie XML, procesem serializacji staje się bardzo przewidywalny dla <xref:System.Runtime.Serialization.DataContractSerializer>i dzięki temu łatwiej optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="fada0-129">Praktyczne zaletą projektowania <xref:System.Runtime.Serialization.DataContractSerializer> jest lepszą wydajność, około dziesięciu procent lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="fada0-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="fada0-130">Atrybuty do użycia z usługą <xref:System.Xml.Serialization.XmlSerializer> nie wskazują pola lub właściwości typu są serializowane w formacie XML, natomiast <xref:System.Runtime.Serialization.DataMemberAttribute> do użytku z programem <xref:System.Runtime.Serialization.DataContractSerializer> pokazuje jawnie, właściwości lub pól, które są serializowane.</span><span class="sxs-lookup"><span data-stu-id="fada0-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="fada0-131">Dlatego kontraktów danych są jawne kontraktach struktury danych, która aplikacja ma być wysyłania i odbierania.</span><span class="sxs-lookup"><span data-stu-id="fada0-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="fada0-132"><xref:System.Xml.Serialization.XmlSerializer> Można tłumaczyć tylko publiczne elementy członkowskie obiektu platformy .NET do formatu XML, <xref:System.Runtime.Serialization.DataContractSerializer> może dokonywać translacji elementy członkowskie obiektów do formatu XML niezależnie od tego, modyfikatory dostępu dla tych członków.</span><span class="sxs-lookup"><span data-stu-id="fada0-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="fada0-133">W wyniku jest możliwe do serializacji elementów członkowskich niepublicznych typy w formacie XML, <xref:System.Runtime.Serialization.DataContractSerializer> ma mniej ograniczeń różnych typów .NET, które mogą zserializować do formatu XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="fada0-134">W szczególności można tłumaczyć na typy XML, takich jak <xref:System.Collections.Hashtable> które implementują <xref:System.Collections.IDictionary> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fada0-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="fada0-135"><xref:System.Runtime.Serialization.DataContractSerializer> Jest znacznie bardziej prawdopodobne można było serializować wystąpień wszelkie istniejące typ architektury .NET do formatu XML bez konieczności tworzenia otoki dla niego lub zmodyfikuj definicję typu.</span><span class="sxs-lookup"><span data-stu-id="fada0-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="fada0-136">Inny konsekwencją <xref:System.Runtime.Serialization.DataContractSerializer> możliwość uzyskania dostępu do elementów członkowskich niepublicznych typu jest wymaga pełnego zaufania, natomiast <xref:System.Xml.Serialization.XmlSerializer> nie.</span><span class="sxs-lookup"><span data-stu-id="fada0-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="fada0-137">Uprawnienie Full Trust dostępu kodu zapewnia pełny dostęp do wszystkich zasobów na komputerze, który jest możliwy przy użyciu poświadczeń, w których kod jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="fada0-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="fada0-138">Ta opcja powinna być używana z rozwagą, zgodnie z w pełni zaufany kod uzyskuje dostęp do wszystkich zasobów na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fada0-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="fada0-139"><xref:System.Runtime.Serialization.DataContractSerializer> Zawiera niektóre obsługę wersji:</span><span class="sxs-lookup"><span data-stu-id="fada0-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="fada0-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Ma <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość, którą można przypisać wartość false dla elementów członkowskich, które są dodawane do nowych wersji kontraktu danych, które nie były obecne w starszych wersjach, umożliwiając aplikacji z nowszą wersją kontraktu jako Umożliwia przetwarzanie wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="fada0-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="fada0-141">Dzięki implementacji kontraktu danych <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu, jeden Zezwalaj <xref:System.Runtime.Serialization.DataContractSerializer> do przekazania składowych zdefiniowanych w nowszych wersjach kontraktu danych za pomocą aplikacji ze starszymi wersjami kontraktu.</span><span class="sxs-lookup"><span data-stu-id="fada0-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="fada0-142">Pomimo wszystkich różnic, XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje semantycznie taka sama jak XML, do którego jest typem domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typem parametru przestrzeni nazw XML jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="fada0-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="fada0-143">Następujące klasy, która zawiera atrybuty do używania z programem serializatory, jest tłumaczony na semantycznie identyczne XML przez <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="fada0-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

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

<span data-ttu-id="fada0-144">Zestaw Windows software development kit (SDK) zawiera narzędzia wiersza polecenia o nazwie [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fada0-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="fada0-145">Narzędzia xsd.exe używać z usługami sieci Web platformy ASP.NET, takich jak Svcutil.exe może generować definicje typów danych .NET ze schematu XML.</span><span class="sxs-lookup"><span data-stu-id="fada0-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="fada0-146">Istnieją typy kontraktów danych, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> może emitować XML w formacie definiowana przez schemat XML; w przeciwnym razie są przeznaczone do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fada0-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fada0-147">Svcutil.exe można również wygenerować schematu XML z kontraktów danych przy użyciu jego `dataContractOnly` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="fada0-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="fada0-148">Mimo że użycia usług sieci Web platformy ASP.NET <xref:System.Xml.Serialization.XmlSerializer>, a tryb zgodności WCF ASP.NET sprawia, że usługi WCF, które naśladują zachowanie usług sieci Web platformy ASP.NET, opcję zgodności ASP.NET nie ogranicza do przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fada0-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fada0-149">Jeden można nadal używać <xref:System.Runtime.Serialization.DataContractSerializer> za pomocą usług działających w trybie zgodności platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="fada0-150">Tworzenie usługi</span><span class="sxs-lookup"><span data-stu-id="fada0-150">Service Development</span></span>

<span data-ttu-id="fada0-151">Tworzenie usługi przy użyciu platformy ASP.NET, był zwyczajowego, aby dodać <xref:System.Web.Services.WebService> atrybutu dla klasy i <xref:System.Web.Services.WebMethodAttribute> do dowolnej metody tej klasy, które mają być operacje usługi:</span><span class="sxs-lookup"><span data-stu-id="fada0-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

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

<span data-ttu-id="fada0-152">Program ASP.NET 2.0 wprowadzono możliwość dodania atrybutu <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> do interfejsu, a nie klasę w celu zapisywania klasy do zaimplementowania interfejsu:</span><span class="sxs-lookup"><span data-stu-id="fada0-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

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

<span data-ttu-id="fada0-153">Użycie tej opcji zaleca się, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybut definiuje kontrakt dla operacji wykonywanych przez usługę, która może być ponownie używane z różnymi klasami, które mogą implementować tej samej umowy na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="fada0-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="fada0-154">Usługa WCF jest zapewniana przez definiowanie punktami końcowymi programu WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="fada0-155">Punkt końcowy jest definiowany przez adres i powiązanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="fada0-156">Adres Określa, gdzie usługa się znajduje.</span><span class="sxs-lookup"><span data-stu-id="fada0-156">The address defines where the service is located.</span></span> <span data-ttu-id="fada0-157">Powiązanie określa sposób komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="fada0-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="fada0-158">Kontrakt usługi określa operacje, które można wykonać usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="fada0-159">Kontrakt usługi jest zwykle definiowana jako pierwsza, dodając <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> do interfejsu:</span><span class="sxs-lookup"><span data-stu-id="fada0-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="fada0-160"><xref:System.ServiceModel.ServiceContractAttribute> Określa, że interfejs definiuje kontrakt usługi WCF i <xref:System.ServiceModel.OperationContractAttribute> wskazuje, ile, metod interfejsu definiującą operacji kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="fada0-161">Po zdefiniowaniu kontraktu usługi jest zaimplementowana w klasie, konfigurując klasy implementuj interfejs za pomocą którego zdefiniowano kontraktu usługi:</span><span class="sxs-lookup"><span data-stu-id="fada0-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="fada0-162">Klasa, która implementuje kontraktu usługi jest określany jako usługę, wpisz w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="fada0-163">Następnym krokiem jest, aby skojarzyć adres i powiązanie z typem usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="fada0-164">Który odbywa się zwykle w pliku konfiguracji, edytując plik bezpośrednio lub za pomocą edytora konfiguracji dostarczane z programem WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="fada0-165">Oto przykładowy plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fada0-165">Here is an example of a configuration file.</span></span>

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

<span data-ttu-id="fada0-166">Powiązanie określa zestaw protokołów do komunikacji z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="fada0-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="fada0-167">W poniższej tabeli wymieniono powiązania dostarczane przez system, które reprezentują typowe opcje.</span><span class="sxs-lookup"><span data-stu-id="fada0-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="fada0-168">Nazwa</span><span class="sxs-lookup"><span data-stu-id="fada0-168">Name</span></span>|<span data-ttu-id="fada0-169">Cel</span><span class="sxs-lookup"><span data-stu-id="fada0-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="fada0-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-170">BasicHttpBinding</span></span>|<span data-ttu-id="fada0-171">Współdziałanie z usługami sieci Web i klientów obsługi protokołu WS-BasicProfile 1.1 i podstawowe 1.0 profilu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="fada0-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="fada0-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-172">WSHttpBinding</span></span>|<span data-ttu-id="fada0-173">Współdziałanie z usługami sieci Web i klientów, którzy obsługują WS-\* protokołów za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fada0-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="fada0-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-174">WSDualHttpBinding</span></span>|<span data-ttu-id="fada0-175">Komunikację dupleksową HTTP za pomocą którego odbiorca pierwszy komunikat odpowiadaj bezpośrednio na początkowej nadawcy, ale może przekazać dowolną liczbę odpowiedzi w określonym czasie przy użyciu protokołu HTTP, zgodnie z WS-\* protokołów.</span><span class="sxs-lookup"><span data-stu-id="fada0-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="fada0-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-176">WSFederationBinding</span></span>|<span data-ttu-id="fada0-177">Protokołu HTTP do komunikacji, w którym można kontrolować dostęp do zasobów usługi oparte na poświadczeniach wystawione przez dostawcę jawnie określone poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="fada0-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="fada0-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-178">NetTcpBinding</span></span>|<span data-ttu-id="fada0-179">Bezpieczne, niezawodne i wysoko wydajnych komunikację między jednostkami oprogramowania WCF, sieciach.</span><span class="sxs-lookup"><span data-stu-id="fada0-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="fada0-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="fada0-181">Bezpieczne, niezawodne i wysoko wydajnych komunikację między jednostkami oprogramowania WCF na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fada0-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="fada0-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-182">NetMsmqBinding</span></span>|<span data-ttu-id="fada0-183">Komunikacja między jednostkami oprogramowania WCF za pomocą usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fada0-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="fada0-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="fada0-185">Komunikacja między jednostką oprogramowania WCF i innej jednostki oprogramowania za pomocą usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fada0-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="fada0-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="fada0-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="fada0-187">Komunikacja między jednostkami oprogramowania WCF za pomocą sieci Peer-to-Peer Windows.</span><span class="sxs-lookup"><span data-stu-id="fada0-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="fada0-188">Powiązania dostarczane przez system <xref:System.ServiceModel.BasicHttpBinding>, zawiera zestaw protokołów obsługiwanych przez usługi sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="fada0-189">Powiązań niestandardowych dla aplikacji WCF łatwo są definiowane jako kolekcje klas element powiązania, które korzysta z usługi WCF do zaimplementowania poszczególnych protokołów.</span><span class="sxs-lookup"><span data-stu-id="fada0-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="fada0-190">Nowe elementy powiązania można zapisać do reprezentowania dodatkowych protokołów.</span><span class="sxs-lookup"><span data-stu-id="fada0-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="fada0-191">Wewnętrzne zachowanie typu usługi można dostosować za pomocą właściwości rodzina klasy o nazwie zachowania.</span><span class="sxs-lookup"><span data-stu-id="fada0-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="fada0-192">W tym miejscu <xref:System.ServiceModel.ServiceBehaviorAttribute> klasa jest używana do określenia, że typ usługi ma być wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="fada0-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="fada0-193">Niektórych zachowań, takich jak <xref:System.ServiceModel.ServiceBehaviorAttribute>, atrybutów.</span><span class="sxs-lookup"><span data-stu-id="fada0-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="fada0-194">Inne, te z właściwościami, które Administratorzy, będzie chciała ustawić, można zmodyfikować w konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="fada0-195">W programowaniu typów usług, często stosuje się <xref:System.ServiceModel.OperationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="fada0-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="fada0-196">Jego statyczny <xref:System.ServiceModel.OperationContext.Current%2A> właściwości zapewnia dostęp do informacji o kontekście, w którym jest uruchomiona operacja.</span><span class="sxs-lookup"><span data-stu-id="fada0-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="fada0-197"><xref:System.ServiceModel.OperationContext> jest podobny do obu <xref:System.Web.HttpContext> i <xref:System.EnterpriseServices.ContextUtil> klasy.</span><span class="sxs-lookup"><span data-stu-id="fada0-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="fada0-198">Hosting</span><span class="sxs-lookup"><span data-stu-id="fada0-198">Hosting</span></span>

<span data-ttu-id="fada0-199">Usługi sieci Web platformy ASP.NET są kompilowane w zestawie biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="fada0-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="fada0-200">Plik o nazwie pliku usługi jest warunkiem, że .asmx rozszerzenie, a następnie zawiera `@ WebService` dyrektywę, który identyfikuje klasę, która zawiera kod dla usługi i zestawu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="fada0-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

```
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>
```

<span data-ttu-id="fada0-201">Plik usługi jest kopiowana do katalog główny aplikacji ASP.NET w Internet Information Services (IIS), a zestaw jest kopiowana do podkatalogu \bin ten katalog główny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="fada0-202">Aplikacja będzie dostępna przy użyciu uniwersalnego lokatora zasobów (URL) pliku usługi w katalogu głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="fada0-203">Łatwo można hostować usługi WCF, usługi IIS 5.1 i 6.0, Windows Process Activation Service (WAS), który znajduje się w ramach usług IIS 7.0 i w ramach dowolnej aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="fada0-204">Do hostowania w usługach IIS 5.1 i 6.0, jako protokół transportowy komunikacji usługi należy użyć protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fada0-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="fada0-205">Aby hostować usługi w ramach usługi IIS 5.1 w wersji 6.0 lub WAS, wykonaj kroki poniżej:</span><span class="sxs-lookup"><span data-stu-id="fada0-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="fada0-206">Skompiluj typ usługi, w zestawie biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="fada0-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="fada0-207">Utwórz plik usługi z rozszerzeniem .svc z `@ ServiceHost` dyrektywy do identyfikowania typ usługi:</span><span class="sxs-lookup"><span data-stu-id="fada0-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    ```
    <%@ServiceHost language="c#" Service="MyService" %>
    ```

3. <span data-ttu-id="fada0-208">Skopiuj plik usługi do katalogu wirtualnego, a zestaw w podkatalogu \bin tego katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="fada0-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="fada0-209">Skopiuj plik konfiguracji do katalogu wirtualnego, a następnie nadaj mu nazwę pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="fada0-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="fada0-210">Aplikacja będzie dostępna przy użyciu adresu URL pliku usługi w katalogu głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="fada0-211">Hostowanie usługi WCF w ramach aplikacji .NET, skompilować typ usługi, w zestawie biblioteki klas przywoływany przez aplikację i ją do hosta usługi przy użyciu programu <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="fada0-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="fada0-212">Oto przykład podstawy programowania wymagane:</span><span class="sxs-lookup"><span data-stu-id="fada0-212">The following is an example of the basic programming required:</span></span>

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

<span data-ttu-id="fada0-213">Ten przykład przedstawia, jak podano adresy dla co najmniej jeden protokoły transportowe będące w konstrukcji <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="fada0-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="fada0-214">Te adresy są określane jako adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="fada0-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="fada0-215">Określony dla dowolnego punktu końcowego usługi WCF adres jest określany względem adresu podstawowego hosta punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fada0-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="fada0-216">Host może mieć jeden adres podstawowy dla każdego protokołu transportu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="fada0-217">W przykładowej konfiguracji w poprzednim pliku konfiguracji <xref:System.ServiceModel.BasicHttpBinding> wybrane do używany przez punkt końcowy HTTP jako protokołu transportowego, więc adres punktu końcowego, `EchoService`, jest określana względem podstawowy adres HTTP hosta.</span><span class="sxs-lookup"><span data-stu-id="fada0-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="fada0-218">W przypadku hostów w poprzednim przykładzie, jest podstawowy adres HTTP `http://www.contoso.com:8000/`.</span><span class="sxs-lookup"><span data-stu-id="fada0-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="fada0-219">W przypadku usługi hostowane w usługach IIS i WAS adres podstawowy jest adres URL usługi Usługa pliku.</span><span class="sxs-lookup"><span data-stu-id="fada0-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="fada0-220">Tylko usługi hostowane w usługach IIS i WAS i które są konfigurowane za pośrednictwem protokołu HTTP jako protokołu transportowego wyłącznie, będzie możliwe użycie opcji Tryb zgodności WCF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="fada0-221">Włączenie tej opcji wymaga wykonania następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="fada0-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="fada0-222">Należy dodać programistę <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atrybutu typu usługi i określ, czy tryb zgodności ASP.NET jest dozwolona lub wymagana.</span><span class="sxs-lookup"><span data-stu-id="fada0-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="fada0-223">Administrator musi skonfigurować aplikację do korzystania z trybu zgodności programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

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

    <span data-ttu-id="fada0-224">Aplikacje usług WCF można skonfigurować w taki sposób, na potrzeby .asmx jako rozszerzenie swoich plików usługi zamiast .svc.</span><span class="sxs-lookup"><span data-stu-id="fada0-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

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

    <span data-ttu-id="fada0-225">Tej opcji można zapisać się z konieczności modyfikowania klientów, które są skonfigurowane do używania adresów URL plików usługi .asmx podczas modyfikowania usługi do użycia usług WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="fada0-226">Tworzenie aplikacji klienckich</span><span class="sxs-lookup"><span data-stu-id="fada0-226">Client Development</span></span>

<span data-ttu-id="fada0-227">Klienci usługi sieci Web platformy ASP.NET są generowane przy użyciu narzędzia wiersza polecenia WSDL.exe, który zawiera adres URL pliku .asmx jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="fada0-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="fada0-228">Odpowiedniego narzędzia, które są dostarczane przez architekturę WCF jest [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fada0-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="fada0-229">Generuje moduł kodu o definicję kontraktu usługi, jak i definicja klasy klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="fada0-230">Generuje plik konfiguracji przy użyciu adresu i powiązania usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="fada0-231">W kliencie usługi zdalnej programowania jest na ogół program zgodnie z wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="fada0-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="fada0-232">Kod wygenerowany przez narzędzie WSDL.exe zawsze zawiera zarówno przez synchroniczny i asynchroniczny wzorzec domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fada0-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="fada0-233">Kod wygenerowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może spowodować uzyskanie albo wzorzec.</span><span class="sxs-lookup"><span data-stu-id="fada0-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="fada0-234">Oferuje ona synchroniczne wzorzec domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fada0-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="fada0-235">Jeśli narzędzie jest wykonywane przy użyciu `/async` przełączyć, a następnie wygenerowany kod przewiduje wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="fada0-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="fada0-236">Nie ma żadnej gwarancji, że nazwy w klasach klienta WCF, które są generowane przez program ASP. Narzędzie WSDL.exe firmy NET, domyślnie zgodne z nazwami w generowanych przez narzędzia Svcutil.exe klasy klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="fada0-237">W szczególności, nazwy właściwości klas, trzeba być Zserializowany za pomocą <xref:System.Xml.Serialization.XmlSerializer> domyślnie otrzymują sufiks właściwość, która znajduje się w kod wygenerowany przez narzędzie Svcutil.exe, które nie jest to za pomocą narzędzia WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="fada0-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="fada0-238">Reprezentacja komunikatu</span><span class="sxs-lookup"><span data-stu-id="fada0-238">Message Representation</span></span>

<span data-ttu-id="fada0-239">Można dostosować nagłówków protokołu SOAP komunikatów wysyłanych i odbieranych przez usługi sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="fada0-240">Klasa jest pochodną <xref:System.Web.Services.Protocols.SoapHeader> do definiowania struktury nagłówka, a następnie <xref:System.Web.Services.Protocols.SoapHeaderAttribute> służy do wskazywania obecność nagłówka.</span><span class="sxs-lookup"><span data-stu-id="fada0-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

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

<span data-ttu-id="fada0-241">WCF zawiera atrybuty, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, i <xref:System.ServiceModel.MessageBodyMemberAttribute> do opisania struktury komunikaty protokołu SOAP wysłanych i odebranych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="fada0-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

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

<span data-ttu-id="fada0-242">Ta składnia daje reprezentację w postaci jawnej struktury wiadomości, natomiast struktury wiadomości jest implikowany przez kod z usługi sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="fada0-243">Ponadto w składni ASP.NET nagłówków wiadomości są reprezentowane jako właściwości usługi, takie jak `ProtocolHeader` właściwości w poprzednim przykładzie, w składni WCF są bardziej precyzyjne reprezentowana jako właściwości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="fada0-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="fada0-244">Ponadto WCF umożliwia nagłówków wiadomości, które mają zostać dodane do konfiguracji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="fada0-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

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

<span data-ttu-id="fada0-245">Czy opcja umożliwia uniknięcie każde odwołanie do nagłówków protokołu infrastrukturalnych w kodzie klienta lub usługi: nagłówki są dodawane do komunikatów z powodu konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fada0-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="fada0-246">Opis usługi</span><span class="sxs-lookup"><span data-stu-id="fada0-246">Service Description</span></span>

<span data-ttu-id="fada0-247">Wystawianie żądanie HTTP GET dla plików .asmx usługi sieci Web platformy ASP.NET z zapytaniem WSDL powoduje, że ASP.NET wygeneruje WSDL usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="fada0-248">Zwraca wartość, która WSDL jako odpowiedź na żądanie.</span><span class="sxs-lookup"><span data-stu-id="fada0-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="fada0-249">ASP.NET 2.0 możliwe sprawdzenie, czy usługa jest zgodne z Basic Profile 1.1 organizacji współdziałania usług sieci Web (WS-I) oraz do wstawienia oświadczenia, że usługa jest zgodne w jego WSDL.</span><span class="sxs-lookup"><span data-stu-id="fada0-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="fada0-250">Oznacza to gotowe przy użyciu `ConformsTo` i `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="fada0-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="fada0-251">Można dostosować języka WSDL, który ASP.NET generuje dla usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="fada0-252">Dostosowania zostały wprowadzone, tworząc klasę pochodną z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> do dodawania elementów do pliku WSDL.</span><span class="sxs-lookup"><span data-stu-id="fada0-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="fada0-253">Wydania żądania HTTP GET z zapytaniem WSDL pliku .svc usługi WCF z punktu końcowego HTTP, hostowane w usługach IIS 51, 6.0 lub WAS powoduje, że usługi WCF na odpowiedź z WSDL usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="fada0-254">Wystawianie żądanie HTTP GET z zapytaniem WSDL podstawowy adres HTTP usług hostowanych na platformie aplikacji platformy .NET ma taki sam skutek, jeśli httpGetEnabled jest ustawiona na wartość true.</span><span class="sxs-lookup"><span data-stu-id="fada0-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="fada0-255">Jednak WCF także odpowiada na żądania usługi WS-MetadataExchange za pomocą języka WSDL, który generuje do opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="fada0-256">Usług sieci Web programu ASP.NET nie ma wbudowaną obsługę protokołu WS-MetadataExchange żądań.</span><span class="sxs-lookup"><span data-stu-id="fada0-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="fada0-257">Często można dostosować języka WSDL, który generuje WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="fada0-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Klasa udostępnia niektóre funkcje służące do dostosowywania pliku WSDL.</span><span class="sxs-lookup"><span data-stu-id="fada0-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="fada0-259">WCF można również skonfigurować nie generowania języka WSDL, lecz raczej przy użyciu statycznych pliku WSDL pod danym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="fada0-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

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

## <a name="exception-handling"></a><span data-ttu-id="fada0-260">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="fada0-260">Exception Handling</span></span>

<span data-ttu-id="fada0-261">W usługach sieci Web platformy ASP.NET nieobsłużone wyjątki są zwracane do klientów jako błędach SOAP.</span><span class="sxs-lookup"><span data-stu-id="fada0-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="fada0-262">Można także jawnie generować wystąpień <xref:System.Web.Services.Protocols.SoapException> klasy i mieć większą kontrolę nad zawartością błąd protokołu SOAP, która pobiera przesłana do klienta.</span><span class="sxs-lookup"><span data-stu-id="fada0-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="fada0-263">W usługach WCF nieobsługiwanych wyjątków nie są zwracane do klientów jako błędach SOAP, aby zapobiec przypadkowo są udostępniane za pośrednictwem wyjątki informacji poufnych.</span><span class="sxs-lookup"><span data-stu-id="fada0-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="fada0-264">Ustawienie konfiguracji znajduje się na ma nieobsługiwane wyjątki zwracane do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="fada0-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="fada0-265">Aby przywrócić błędach SOAP dla klientów, może zgłosić wystąpień typu ogólnego <xref:System.ServiceModel.FaultException%601>za pomocą ogólnego typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="fada0-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="fada0-266">Można również dodać <xref:System.ServiceModel.FaultContractAttribute> atrybuty do obsługi operacji do określenia błędy, które może prowadzić operacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

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

<span data-ttu-id="fada0-267">Robi skutkuje możliwych błędów anonsowane w języku WSDL usługi, umożliwiając klienckim ekspertów w programowaniu w celu przewidywania usterek, które można wynika z operacji i zapisu czy odpowiednie catch, instrukcje.</span><span class="sxs-lookup"><span data-stu-id="fada0-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

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

## <a name="state-management"></a><span data-ttu-id="fada0-268">Zarządzanie stanem</span><span class="sxs-lookup"><span data-stu-id="fada0-268">State Management</span></span>

<span data-ttu-id="fada0-269">Klasa używany do implementowania usługi sieci Web ASP.NET może pochodzić od <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="fada0-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="fada0-270">W takim przypadku klasa może być zaprogramowane w taki sposób, aby użyć <xref:System.Web.Services.WebService> podstawowej klasy właściwości kontekstu, aby uzyskać dostęp do <xref:System.Web.HttpContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="fada0-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="fada0-271"><xref:System.Web.HttpContext> Obiekt może być używany do aktualizowania i pobierania informacji o stanie aplikacji za pomocą jego właściwości aplikacji i może służyć do aktualizowania i pobierania informacji o stanie sesji przy użyciu jego właściwość sesji.</span><span class="sxs-lookup"><span data-stu-id="fada0-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="fada0-272">Platforma ASP.NET zapewnia znaczną kontrolę nad którym sesja stanu informacje dostępne przy użyciu właściwości sesji <xref:System.Web.HttpContext> rzeczywiście jest przechowywana.</span><span class="sxs-lookup"><span data-stu-id="fada0-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="fada0-273">Mogą być przechowywane, w plikach cookie, w bazie danych, w pamięci bieżącego serwera lub w pamięci wyznaczonym serwerze.</span><span class="sxs-lookup"><span data-stu-id="fada0-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="fada0-274">Wybór zostanie przeprowadzona w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="fada0-275">WCF zawiera obiekty Rozszerzalne zarządzanie stanem.</span><span class="sxs-lookup"><span data-stu-id="fada0-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="fada0-276">Obiekty rozszerzalne to obiekty, które implementują <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="fada0-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="fada0-277">Są najważniejsze obiekty rozszerzalne <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="fada0-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="fada0-278">`ServiceHostBase` pozwala zachować dostęp do stanu, że typy wszystkich wystąpień wszystkie usługi na tym samym hoście, podczas gdy `InstanceContext` pozwala zachować stan, który może zostać oceniony przez każdy kod uruchomiony w ramach tego samego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="fada0-279">Tutaj, typ usługi `TradingSystem`, ma <xref:System.ServiceModel.ServiceBehaviorAttribute> określający, że wszystkie wywołania z tego samego wystąpienia klienta WCF, są kierowane do tego samego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="fada0-280">Klasa `DealData`, definiuje stan, który może zostać oceniony przez każdy kod uruchomiony w tym samym wystąpieniu typu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="fada0-281">W kodzie typ usługi, który implementuje jednej z operacji kontraktu usługi `DealData` stan obiektu jest dodawany do stanu bieżącego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="fada0-282">Ten obiekt stanu następnie można je pobrać i zmodyfikowane przez kod, który implementuje innej operacji kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="fada0-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="fada0-283">Program ASP.NET zapewnia kontrolę nad, gdzie stan informacje zawarte w <xref:System.Web.HttpContext> klasy rzeczywiście jest przechowywana, WCF, co najmniej w wersji początkowej zapewnia kontrolę przechowywania obiekty rozszerzalne.</span><span class="sxs-lookup"><span data-stu-id="fada0-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="fada0-284">Który stanowi najlepsze Przyczyna wybierając tryb zgodności ASP.NET dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="fada0-285">Jeśli jest rozwiązaniem do zarządzania stanem można skonfigurować, a następnie włączenie trybu zgodności programu ASP.NET pozwala na używanie funkcji <xref:System.Web.HttpContext> klasy dokładnie tak, jak są one używane w programie ASP.NET, a także skonfigurować gdzie informacje stanie zarządzany przy użyciu <xref:System.Web.HttpContext> klasy są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="fada0-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="fada0-286">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="fada0-286">Security</span></span>

<span data-ttu-id="fada0-287">Opcje dotyczące zabezpieczania usług sieci Web platformy ASP.NET są do zabezpieczania dowolnej aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="fada0-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="fada0-288">Ponieważ może być hostowana aplikacji WCF, nie tylko w ramach usług IIS, ale także w dowolnych plików wykonywalnych platformy .NET, opcje zabezpieczania aplikacji WCF muszą być wykonane niezależna od funkcji programu IIS.</span><span class="sxs-lookup"><span data-stu-id="fada0-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="fada0-289">Jednak urządzenia podane dla usług sieci Web platformy ASP.NET są również dostępne dla usługi WCF, uruchomiony w trybie zgodności w programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="fada0-290">Zabezpieczenia: Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="fada0-290">Security: Authentication</span></span>

<span data-ttu-id="fada0-291">IIS oferuje funkcje służące do kontrolowania dostępu do aplikacji za pomocą których można wybrać dostęp anonimowy lub różne tryby uwierzytelniania: Uwierzytelnianie Windows, uwierzytelniania szyfrowanego, uwierzytelnianie podstawowe i uwierzytelnianie na platformie .NET usługi Passport.</span><span class="sxs-lookup"><span data-stu-id="fada0-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="fada0-292">Opcja uwierzytelniania Windows może służyć do kontrolowania dostępu do usług sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="fada0-293">Jednak podczas aplikacji WCF hostowanych w ramach usług IIS, usługi IIS muszą być skonfigurowane, aby zezwolić na anonimowy dostęp do aplikacji, aby można było zarządzać uwierzytelniania przez architekturę WCF, która obsługuje uwierzytelnianie Windows między różnymi inne opcje.</span><span class="sxs-lookup"><span data-stu-id="fada0-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="fada0-294">Inne opcje, które są wbudowane obejmują username tokeny, certyfikaty X.509, tokeny SAML i CardSpace karty, ale można także definiować niestandardowych mechanizmów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fada0-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="fada0-295">Zabezpieczenia: Personifikacja</span><span class="sxs-lookup"><span data-stu-id="fada0-295">Security: Impersonation</span></span>

<span data-ttu-id="fada0-296">Program ASP.NET zapewnia elementu tożsamości przez usługi sieci Web platformy ASP.NET można wprowadzić personifikować określonego użytkownika lub niezależnie od użytkownika poświadczeń są dostarczane z bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="fada0-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="fada0-297">Ten element może służyć do konfigurowania personifikacji aplikacji WCF uruchomionych w trybie zgodności platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="fada0-298">System konfiguracji usługi WCF zawiera element tożsamości wyznaczania dać określonemu użytkownikowi personifikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="fada0-299">Ponadto klienci WCF i usługi można niezależnie skonfigurować personifikacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="fada0-300">Klientów można skonfigurować w taki sposób, aby Personifikuj bieżącego użytkownika, gdy są przez nie przesyłane żądania.</span><span class="sxs-lookup"><span data-stu-id="fada0-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="fada0-301">Operacje usługi można skonfigurować do personifikacji, niezależnie od użytkownika poświadczeń są dostarczane z bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="fada0-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="fada0-302">Zabezpieczenia: Autoryzacja przy użyciu list kontroli dostępu</span><span class="sxs-lookup"><span data-stu-id="fada0-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="fada0-303">List kontroli dostępu (ACL) może służyć do ograniczania dostępu do plików .asmx.</span><span class="sxs-lookup"><span data-stu-id="fada0-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="fada0-304">Jednak list kontroli dostępu do plików .svc WCF są ignorowane z wyjątkiem w trybie zgodności w programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="fada0-305">Zabezpieczenia: Autoryzacja oparta na rolach</span><span class="sxs-lookup"><span data-stu-id="fada0-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="fada0-306">Opcja uwierzytelniania Windows usług IIS może służyć w połączeniu z elementem autoryzacji dostarczonych przez język konfiguracji platformy ASP.NET do ułatwienia autoryzacji opartej na rolach dla usług sieci Web platformy ASP.NET opartych na grupach Windows, do których użytkownicy są przypisani .</span><span class="sxs-lookup"><span data-stu-id="fada0-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="fada0-307">Program ASP.NET 2.0 wprowadzono bardziej ogólnych mechanizmu autoryzacji opartej na rolach: dostawców ról.</span><span class="sxs-lookup"><span data-stu-id="fada0-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="fada0-308">Dostawców ról są klasami, które implementują podstawowy interfejs dla badające o rolach, do których użytkownik jest przypisany, że każdy dostawca ról wie, jak pobrać te informacje z innego źródła.</span><span class="sxs-lookup"><span data-stu-id="fada0-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="fada0-309">Program ASP.NET 2.0 zawiera rolę dostawcę, który można pobrać przypisań ról z bazy danych programu Microsoft SQL Server i drugą do pobrania przypisań ról z Menedżer autoryzacji systemu Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="fada0-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="fada0-310">Mechanizm dostawcy roli faktycznie można niezależnie od platformy ASP.NET w dowolnej aplikacji platformy .NET, w tym aplikacji WCF.</span><span class="sxs-lookup"><span data-stu-id="fada0-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="fada0-311">Następujące Przykładowa konfiguracja dla aplikacji WCF pokazuje, jak używanie dostawcy ról ASP.NET jest opcja wybrana przez <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fada0-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

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

### <a name="security-claims-based-authorization"></a><span data-ttu-id="fada0-312">Zabezpieczenia: Autoryzacja oparta na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="fada0-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="fada0-313">Jedną z najważniejszych innowacyjnych możliwościach programu WCF jest dokładne Obsługa Autoryzowanie dostępu do chronionych zasobów na podstawie oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="fada0-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="fada0-314">Oświadczenia składają się z typem, prawa i wartości, sterowniki licencji, na przykład.</span><span class="sxs-lookup"><span data-stu-id="fada0-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="fada0-315">To sprawia, że zestaw oświadczeń o elementu nośnego, z których jedna jest okaziciela datę urodzenia.</span><span class="sxs-lookup"><span data-stu-id="fada0-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="fada0-316">Typ tego oświadczenia jest data urodzenia, gdy wartość oświadczenia jest data urodzenia sterownika.</span><span class="sxs-lookup"><span data-stu-id="fada0-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="fada0-317">Po prawej stronie, która przyznaje oświadczenie okaziciela określa okaziciela czynności przy użyciu wartości oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="fada0-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="fada0-318">W przypadku oświadczeń sterownika Data urodzenia, po prawej stronie jest posiadanie: sterownik posiada, których data urodzenia ale nie może, na przykład, zmienienia go.</span><span class="sxs-lookup"><span data-stu-id="fada0-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="fada0-319">Autoryzacja oparta na oświadczeniach otacza autoryzacji opartej na rolach, ponieważ typ oświadczenia są role.</span><span class="sxs-lookup"><span data-stu-id="fada0-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="fada0-320">Autoryzacja na podstawie oświadczeń odbywa się przez porównanie zestaw oświadczeń do wymagań dostępu do operacji i, w zależności od tego, w wyniku tego porównania, udzielanie lub odmawianie dostępu do operacji.</span><span class="sxs-lookup"><span data-stu-id="fada0-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="fada0-321">W programie WCF, można określić klasa używana do uruchamiania autoryzacji opartej na oświadczeniach, ponownie przypisując wartość `ServiceAuthorizationManager` właściwość <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fada0-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="fada0-322">Klasy używane do uruchamiania autoryzacji opartej na oświadczeniach muszą pochodzić od <xref:System.ServiceModel.ServiceAuthorizationManager>, który ma tylko jedną metodę, aby zastąpić, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="fada0-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="fada0-323">Usługi WCF wywołuje tę metodę, za każdym razem jest wywoływana operacji usługi i udostępnia <xref:System.ServiceModel.OperationContext> obiektu, który ma oświadczenia dla użytkownika w jego `ServiceSecurityContext.AuthorizationContext` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fada0-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="fada0-324">Usługi WCF wykonuje pracę złożenia oświadczenia dotyczące użytkownika z tokenem zabezpieczającym, niezależnie od użytkownika podany na potrzeby uwierzytelniania, co pozostawia zadania oceny, czy te oświadczenia są wystarczające dla danego działania.</span><span class="sxs-lookup"><span data-stu-id="fada0-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="fada0-325">Czy WCF automatycznie składa oświadczeń z dowolnego rodzaju zabezpieczenia tokenu jest bardzo istotne innowacji, ponieważ dzięki niej kod autoryzacji na podstawie oświadczeń, które są całkowicie niezależne mechanizmu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="fada0-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="fada0-326">Z drugiej strony autoryzację przy użyciu list kontroli dostępu lub role w programie ASP.NET jest ściśle powiązany uwierzytelniania Windows.</span><span class="sxs-lookup"><span data-stu-id="fada0-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="fada0-327">Zabezpieczenia: Poufność</span><span class="sxs-lookup"><span data-stu-id="fada0-327">Security: Confidentiality</span></span>

<span data-ttu-id="fada0-328">Poufność komunikatów wymienianych z usługami sieci Web platformy ASP.NET można zapewnić na poziomie transportu przez skonfigurowanie aplikacji w ramach usług IIS do korzystania z Secure Hypertext Transfer Protocol (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="fada0-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="fada0-329">Taki sam zarówno WCF hostowanych w ramach usług IIS.</span><span class="sxs-lookup"><span data-stu-id="fada0-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="fada0-330">Jednak WCF hostowanych poza programem IIS, można również skonfigurować do używania protokołu bezpiecznym transportem.</span><span class="sxs-lookup"><span data-stu-id="fada0-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="fada0-331">Co ważniejsze, aplikacji WCF można również skonfigurować do zabezpieczenia komunikatów przed ich transportu, przy użyciu protokołu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="fada0-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="fada0-332">Zabezpieczanie po prostu treść komunikatu przy użyciu usługi WS-Security umożliwia mu się jako poufne przesyłane przez rolę pośredników przed dotarciem do ostatecznego miejsca przeznaczenia.</span><span class="sxs-lookup"><span data-stu-id="fada0-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="fada0-333">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="fada0-333">Globalization</span></span>

<span data-ttu-id="fada0-334">Język konfiguracji platformy ASP.NET można określić kulturę dla poszczególnych usług.</span><span class="sxs-lookup"><span data-stu-id="fada0-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="fada0-335">WCF nie obsługuje tego ustawienia konfiguracji, z wyjątkiem w trybie zgodności w programie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fada0-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="fada0-336">Aby zlokalizować usługi WCF, która nie korzysta z trybu zgodności programu ASP.NET, skompilować typ usługi do zestawów specyficzne dla kultury i mają oddzielne specyficzne dla kultury punktów końcowych dla każdego zestawu specyficzne dla kultury.</span><span class="sxs-lookup"><span data-stu-id="fada0-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="fada0-337">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fada0-337">See also</span></span>

- [<span data-ttu-id="fada0-338">Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów</span><span class="sxs-lookup"><span data-stu-id="fada0-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
