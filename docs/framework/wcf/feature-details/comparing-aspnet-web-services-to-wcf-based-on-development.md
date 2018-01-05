---
title: "Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c12bd11cee62cd769f7dffc142806fa5ab1b0137
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="156fd-102">Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych</span><span class="sxs-lookup"><span data-stu-id="156fd-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="156fd-103">jest dostępna opcja Tryb zgodności ASP.NET umożliwiające [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji zaprogramowane i skonfigurować usługi sieci Web ASP.NET, takich jak i naśladować ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="156fd-103"> has an ASP.NET compatibility mode option to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="156fd-104">Poniższe sekcje Porównanie usług sieci Web ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oparte na co jest wymagane do tworzenia aplikacji za pomocą obu tych technologii.</span><span class="sxs-lookup"><span data-stu-id="156fd-104">The following sections compare ASP.NET Web services and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="156fd-105">Reprezentacja wartości danych</span><span class="sxs-lookup"><span data-stu-id="156fd-105">Data Representation</span></span>  
 <span data-ttu-id="156fd-106">Rozwój usługi sieci Web ASP.NET zazwyczaj rozpoczyna się od zdefiniowania wszystkich typów złożonych danych, które usługa ma używać.</span><span class="sxs-lookup"><span data-stu-id="156fd-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="156fd-107">Program ASP.NET korzysta z <xref:System.Xml.Serialization.XmlSerializer> tłumaczenie dane reprezentowane przez typy .NET Framework do pliku XML do przesłania do lub z usługą i translację danych otrzymanych w formacie XML na obiekty .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="156fd-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="156fd-108">Definiowanie typów złożonych danych, które jest użycie usługi ASP.NET wymaga definicji programu .NET Framework klasy, która <xref:System.Xml.Serialization.XmlSerializer> można serializować do i z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="156fd-109">Takich klas mogą być zapisywane ręcznie lub generowane na podstawie definicji typu w schemacie XML przy użyciu wiersza polecenia XML schematy/danych typów obsługę narzędzia, xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="156fd-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="156fd-110">Poniżej przedstawiono listę kluczowych problemów dotyczących znać podczas definiowania .NET Framework klasy który <xref:System.Xml.Serialization.XmlSerializer> można serializować do i z pliku XML:</span><span class="sxs-lookup"><span data-stu-id="156fd-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="156fd-111">Tylko publiczne pola i właściwości obiektów .NET Framework są tłumaczone na XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="156fd-112">Wystąpienia klas kolekcji może być Zserializowany w formacie XML, tylko wtedy, gdy klasy implementować albo <xref:System.Collections.IEnumerable> lub <xref:System.Collections.ICollection> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="156fd-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="156fd-113">Klasy, które implementują <xref:System.Collections.IDictionary> interfejsu, takich jak <xref:System.Collections.Hashtable>, nie może być serializowany w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="156fd-114">Świetnie typy w wielu atrybutów <xref:System.Xml.Serialization> przestrzeni nazw można dodać do klasy .NET Framework i jej elementów członkowskich, aby kontrolować sposób wystąpień klasy są reprezentowane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="156fd-115">Projektowanie aplikacji zwykle również rozpoczyna się od definicji typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="156fd-115"> application development usually also begins with the definition of complex types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="156fd-116">możliwe do używania takich samych typach .NET Framework jako usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-116"> can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="156fd-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> mogą być dodawane do typów .NET Framework do wskazania, że wystąpienie typu zserializowana XML i określonego pola lub właściwości typu mają być serializowane, jak pokazano w następującym przykładowym Kod.</span><span class="sxs-lookup"><span data-stu-id="156fd-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="156fd-118"><xref:System.Runtime.Serialization.DataContractAttribute> Oznacza, że zero lub więcej pól lub właściwości typu mają być serializowana, podczas gdy <xref:System.Runtime.Serialization.DataMemberAttribute> oznacza określonego pola lub właściwości do serializacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="156fd-119"><xref:System.Runtime.Serialization.DataContractAttribute> Można zastosować do klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="156fd-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="156fd-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Może odnosić się do pola lub właściwości i pola i właściwości, do których zastosowano atrybut może być publicznych lub prywatnych.</span><span class="sxs-lookup"><span data-stu-id="156fd-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="156fd-121">Wystąpienia typów, które mają <xref:System.Runtime.Serialization.DataContractAttribute> zastosować do nich są określane jako kontraktów danych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="156fd-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="156fd-122">Są one serializowane w formacie XML przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="156fd-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="156fd-123">Poniżej przedstawiono listę istotnych różnic między <xref:System.Runtime.Serialization.DataContractSerializer> i przy użyciu <xref:System.Xml.Serialization.XmlSerializer> i różnych atrybutów <xref:System.Xml.Serialization> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="156fd-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="156fd-124"><xref:System.Xml.Serialization.XmlSerializer> i atrybuty <xref:System.Xml.Serialization> przestrzeni nazw zostały zaprojektowane do umożliwiają mapowania typów .NET Framework dowolnego prawidłowego typu zdefiniowanej w schemacie XML, a więc stanowią bardzo precyzyjną kontrolę nad jak typu są reprezentowane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="156fd-125"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> zapewniają bardzo mało kontrolę nad jak typu są reprezentowane w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="156fd-126">Można określić tylko obszary nazw i nazwy używany do reprezentowania typu i jego pól lub właściwości w pliku XML i sekwencji, w którym pola i właściwości są wyświetlane w pliku XML:</span><span class="sxs-lookup"><span data-stu-id="156fd-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="156fd-127">Wszystkie inne informacje o strukturze XML używany do reprezentowania typ architektury .NET jest określany przez <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="156fd-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="156fd-128">Przez nie pozwala na znacznie kontrolę nad jak typ ma być reprezentowane w formacie XML, procesu serializacji staje się bardzo przewidywalną dla <xref:System.Runtime.Serialization.DataContractSerializer>i, w tym samym łatwiejsze do optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="156fd-129">Praktyczne zaletą projekt <xref:System.Runtime.Serialization.DataContractSerializer> jest lepszą wydajność, około 10 procent lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="156fd-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="156fd-130">Atrybuty do użycia z <xref:System.Xml.Serialization.XmlSerializer> nie wskazują pola lub właściwości typu są serializowane w formacie XML, podczas gdy <xref:System.Runtime.Serialization.DataMemberAttribute> do użytku z <xref:System.Runtime.Serialization.DataContractSerializer> jawnie zawiera pola lub właściwości są serializowane.</span><span class="sxs-lookup"><span data-stu-id="156fd-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="156fd-131">W związku z tym kontraktów danych są jawne umów dotyczących struktury danych, która aplikacja ma być wysyłania i odbierania.</span><span class="sxs-lookup"><span data-stu-id="156fd-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="156fd-132"><xref:System.Xml.Serialization.XmlSerializer> Można przetworzyć tylko publiczne elementy członkowskie obiektu .NET. w formacie XML, <xref:System.Runtime.Serialization.DataContractSerializer> można przetworzyć elementów członkowskich obiektów w formacie XML niezależnie od modyfikatorów dostępu do tych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="156fd-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="156fd-133">W wyniku było serializować niepublicznych elementów członkowskich typów w formacie XML, <xref:System.Runtime.Serialization.DataContractSerializer> ma mniej ograniczeń różnych typów .NET, które mogą zserializować w formacie XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="156fd-134">W szczególności może przełożyć na typy XML, takich jak <xref:System.Collections.Hashtable> które implementują <xref:System.Collections.IDictionary> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="156fd-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="156fd-135"><xref:System.Runtime.Serialization.DataContractSerializer> Jest znacznie bardziej prawdopodobne można było serializować wystąpień dowolnego istniejącego typu .NET w formacie XML bez konieczności albo zmodyfikuj definicję typu, lub opracowanie otokę dla niego.</span><span class="sxs-lookup"><span data-stu-id="156fd-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="156fd-136">Inny konsekwencją <xref:System.Runtime.Serialization.DataContractSerializer> dostępowi do elementów członkowskich niepublicznego typu jest wymaga pełnego zaufania, podczas gdy <xref:System.Xml.Serialization.XmlSerializer> nie.</span><span class="sxs-lookup"><span data-stu-id="156fd-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="156fd-137">Pełne zaufanie uprawnienie dostępu kodu zapewnić pełny dostęp do wszystkich zasobów na komputerze, który może być przy użyciu poświadczeń, w których jest wykonywany kod dostępu.</span><span class="sxs-lookup"><span data-stu-id="156fd-137">The Full Trust code access permission give complete access to all resources on a machine that can be access using the credentials under which the code is executing.</span></span> <span data-ttu-id="156fd-138">Tej opcji należy używać ostrożnie jako w pełni zaufany kod uzyskuje dostęp do wszystkich zasobów na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="156fd-138">This options should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="156fd-139"><xref:System.Runtime.Serialization.DataContractSerializer> Zawiera niektóre pomocy technicznej dla wersji:</span><span class="sxs-lookup"><span data-stu-id="156fd-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="156fd-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Ma <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości, któremu można przypisać wartość false dla elementów członkowskich, które są dodawane do nowych wersji kontraktu danych, które nie były obecne w starszych wersjach, umożliwiając aplikacji przy użyciu nowszej wersji kontraktu jako może przetworzyć starszych wersji.</span><span class="sxs-lookup"><span data-stu-id="156fd-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="156fd-141">Dzięki użyciu kontraktu danych implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu, co umożliwia <xref:System.Runtime.Serialization.DataContractSerializer> do przekazania elementów członkowskich zdefiniowanych w nowszych wersji kontraktu danych za pomocą aplikacji ze starszymi wersjami kontraktu.</span><span class="sxs-lookup"><span data-stu-id="156fd-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="156fd-142">Mimo wszystko różnice, XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="156fd-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="156fd-143">Poniższe klasy, która ma atrybuty do używania z programem serializatorów, są przetłumaczyć semantycznie identyczne XML przez <xref:System.Xml.Serialization.XmlSerializer> oraz <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="156fd-143">The following class, which has attributes for use with both of the serializers, are translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
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
  
 <span data-ttu-id="156fd-144">Zestaw Windows software development kit (SDK) zawiera narzędzie wiersza polecenia o nazwie [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Narzędzie xsd.exe używane z usługami sieci Web ASP.NET, takich jak Svcutil.exe wygenerować definicje typów danych .NET na podstawie schematu XML.</span><span class="sxs-lookup"><span data-stu-id="156fd-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="156fd-145">Typy są kontraktów danych, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> może emitować XML w formacie zdefiniowane przez schemat XML; w przeciwnym razie są one przeznaczone do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="156fd-145">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="156fd-146">Narzędzia Svcutil.exe, można również do generowania schematu XML z kontraktów danych przy użyciu jego `/dataContractOnly` przełącznika.</span><span class="sxs-lookup"><span data-stu-id="156fd-146">The tool, Svcutil.exe, can also be made to generate XML Schema from data contracts using its `/dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="156fd-147">Mimo że użycia usług sieci Web ASP.NET <xref:System.Xml.Serialization.XmlSerializer>, i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sprawia, że tryb zgodności ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług naśladować zachowanie usług sieci Web ASP.NET, opcji zgodności ASP.NET nie ogranicza jedną przy użyciu <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="156fd-147">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode makes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="156fd-148">Co można nadal używać <xref:System.Runtime.Serialization.DataContractSerializer> z usługi są uruchomione w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-148">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="156fd-149">Projektowanie usługi</span><span class="sxs-lookup"><span data-stu-id="156fd-149">Service Development</span></span>  
 <span data-ttu-id="156fd-150">Aby opracować usługi przy użyciu platformy ASP.NET, został zwyczajowe, aby dodać <xref:System.Web.Services.WebService> atrybutu do klasy i <xref:System.Web.Services.WebMethodAttribute> do dowolnej z metod tej klasy, które mają być operacje usługi:</span><span class="sxs-lookup"><span data-stu-id="156fd-150">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
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
  
 <span data-ttu-id="156fd-151">Platforma ASP.NET 2.0 wprowadzono możliwość dodania atrybutu <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> do interfejsu, a nie na klasę i zapisywania klasy do zaimplementowania interfejsu:</span><span class="sxs-lookup"><span data-stu-id="156fd-151">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
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
  
 <span data-ttu-id="156fd-152">Użycie tej opcji zaleca się, ponieważ interfejs <xref:System.Web.Services.WebService> atrybutu stanowi kontraktu dla operacji wykonywanych przez usługę mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="156fd-152">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="156fd-153">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest udostępniona przez zdefiniowanie co najmniej jednego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="156fd-153">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is provided by defining one or more [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints.</span></span> <span data-ttu-id="156fd-154">Punkt końcowy jest określony przez adres i powiązanie kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-154">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="156fd-155">Adres Określa, gdzie usługa się znajduje.</span><span class="sxs-lookup"><span data-stu-id="156fd-155">The address defines where the service is located.</span></span> <span data-ttu-id="156fd-156">Powiązanie określa sposób komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="156fd-156">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="156fd-157">Kontrakt usługi określa operacje, które można wykonać usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-157">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="156fd-158">Kontrakt usługi są zazwyczaj zdefiniowane, dodając <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> do interfejsu:</span><span class="sxs-lookup"><span data-stu-id="156fd-158">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="156fd-159"><xref:System.ServiceModel.ServiceContractAttribute> Określa, że interfejs definiuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt usługi i <xref:System.ServiceModel.OperationContractAttribute> wskazuje, jeśli taki występuje, metod interfejsu definiującą operacji kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-159">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="156fd-160">Po zdefiniowaniu kontraktu usługi jest zaimplementowana w klasie, konfigurując klasa implementuje interfejs, za pomocą której zdefiniowano kontraktu usługi:</span><span class="sxs-lookup"><span data-stu-id="156fd-160">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="156fd-161">Klasa, która implementuje kontraktu usługi jest określany jako typ usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="156fd-161">A class that implements a service contract is referred to as a service type in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="156fd-162">Następnym krokiem jest można skojarzyć adres i powiązanie z typem usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-162">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="156fd-163">Które zwykle odbywa się w pliku konfiguracji, edytując plik bezpośrednio lub za pomocą edytora konfiguracji wyposażone [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="156fd-163">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="156fd-164">Oto przykładowy plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="156fd-164">Here is an example of a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="156fd-165">Powiązanie określa zestaw protokołów służący do komunikacji z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="156fd-165">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="156fd-166">W poniższej tabeli wymieniono powiązania dostarczane przez system, które reprezentują typowe opcje.</span><span class="sxs-lookup"><span data-stu-id="156fd-166">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="156fd-167">Nazwa</span><span class="sxs-lookup"><span data-stu-id="156fd-167">Name</span></span>|<span data-ttu-id="156fd-168">Cel</span><span class="sxs-lookup"><span data-stu-id="156fd-168">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="156fd-169">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-169">BasicHttpBinding</span></span>|<span data-ttu-id="156fd-170">Współdziałanie z usługami sieci Web i klientami obsługi protokołu WS-BasicProfile 1.1 i podstawowych zabezpieczeń profilu 1.0.</span><span class="sxs-lookup"><span data-stu-id="156fd-170">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="156fd-171">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-171">WSHttpBinding</span></span>|<span data-ttu-id="156fd-172">Współdziałanie z usługami sieci Web i klientów, które obsługuje WS-* protokołów za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="156fd-172">Interoperability with Web services and clients that support the WS-* protocols over HTTP.</span></span>|  
|<span data-ttu-id="156fd-173">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-173">WSDualHttpBinding</span></span>|<span data-ttu-id="156fd-174">Komunikację dupleksową HTTP za pomocą którego nie odpowiedzieć bezpośrednio początkowej nadawcy odbiorcy wiadomości początkowej, ale może przekazać dowolną liczbę odpowiedzi przez pewien czas za pośrednictwem protokołu HTTP, zgodnie z WS-* protokołów.</span><span class="sxs-lookup"><span data-stu-id="156fd-174">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-* protocols.</span></span>|  
|<span data-ttu-id="156fd-175">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-175">WSFederationBinding</span></span>|<span data-ttu-id="156fd-176">Komunikacji HTTP, w którym można kontrolować dostęp do zasobów usługi na podstawie poświadczeń wystawiony przez dostawcę jawnie określone poświadczenie.</span><span class="sxs-lookup"><span data-stu-id="156fd-176">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="156fd-177">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-177">NetTcpBinding</span></span>|<span data-ttu-id="156fd-178">Zabezpieczenia, niezawodne i wysoko wydajnych komunikacji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oprogramowania jednostek w sieci.</span><span class="sxs-lookup"><span data-stu-id="156fd-178">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities across a network.</span></span>|  
|<span data-ttu-id="156fd-179">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-179">NetNamedPipeBinding</span></span>|<span data-ttu-id="156fd-180">Zabezpieczenia, niezawodne i wysoko wydajnych komunikacji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostek oprogramowania na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="156fd-180">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities on the same machine.</span></span>|  
|<span data-ttu-id="156fd-181">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-181">NetMsmqBinding</span></span>|<span data-ttu-id="156fd-182">Komunikacja między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostek oprogramowania przy użyciu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="156fd-182">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="156fd-183">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-183">MsmqIntegrationBinding</span></span>|<span data-ttu-id="156fd-184">Komunikacja między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostki oprogramowania i inną jednostkę oprogramowania przy użyciu usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="156fd-184">Communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="156fd-185">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="156fd-185">NetPeerTcpBinding</span></span>|<span data-ttu-id="156fd-186">Komunikacja między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostek oprogramowania przy użyciu sieci Peer-to-Peer systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="156fd-186">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="156fd-187">Powiązania dostarczane przez system <xref:System.ServiceModel.BasicHttpBinding>, zawiera zestaw protokołów obsługiwanych przez usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-187">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="156fd-188">Powiązania niestandardowe dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji łatwo są zdefiniowane zgodnie z kolekcji element powiązania klas, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa do implementacji poszczególnych protokołów.</span><span class="sxs-lookup"><span data-stu-id="156fd-188">Custom bindings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are easily defined as collections of the binding element classes that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses to implement individual protocols.</span></span> <span data-ttu-id="156fd-189">Nowe elementy powiązania można pisać do reprezentowania dodatkowych protokołów.</span><span class="sxs-lookup"><span data-stu-id="156fd-189">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="156fd-190">Wewnętrzne zachowanie typu usługi można dostosować za pomocą właściwości rodzina klasy o nazwie zachowania.</span><span class="sxs-lookup"><span data-stu-id="156fd-190">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="156fd-191">W tym miejscu <xref:System.ServiceModel.ServiceBehaviorAttribute> klasa jest używana do określenia, czy typ usługi ma być wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="156fd-191">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="156fd-192">Niektóre zachowania, takie jak <xref:System.ServiceModel.ServiceBehaviorAttribute>, atrybutów.</span><span class="sxs-lookup"><span data-stu-id="156fd-192">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="156fd-193">Inne, te właściwości, które Administratorzy czy chcesz ustawić, może być modyfikowany w konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-193">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="156fd-194">W kontekście programowania typów usług częste wykorzystania <xref:System.ServiceModel.OperationContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="156fd-194">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="156fd-195">Jego static <xref:System.ServiceModel.OperationContext.Current%2A> właściwości zapewnia dostęp do informacji o kontekście, w którym jest uruchomiona operacja.</span><span class="sxs-lookup"><span data-stu-id="156fd-195">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="156fd-196"><xref:System.ServiceModel.OperationContext>jest podobny do obu <xref:System.Web.HttpContext> i <xref:System.EnterpriseServices.ContextUtil> klasy.</span><span class="sxs-lookup"><span data-stu-id="156fd-196"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="156fd-197">Hosting</span><span class="sxs-lookup"><span data-stu-id="156fd-197">Hosting</span></span>  
 <span data-ttu-id="156fd-198">Usługi sieci Web ASP.NET są kompilowane do zestawu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="156fd-198">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="156fd-199">Plik o nazwie pliku usługi jest warunkiem, że ma rozszerzenie .asmx i zawiera `@ WebService` dyrektywy identyfikujący klasę, która zawiera kod dla usług i zestawu, w którym znajduje się.</span><span class="sxs-lookup"><span data-stu-id="156fd-199">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="156fd-200">Pliku usługi jest kopiowana do katalog główny aplikacji ASP.NET w Internet Information Services (IIS) i zestaw jest kopiowana do podkatalogu \bin tego katalogu głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-200">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="156fd-201">Aplikacja jest dostępna za pomocą adres URL (adres URL) usługi pliku w katalogu głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-201">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="156fd-202">łatwo mogą być hostowane usługi, usługi IIS 5.1 i 6.0, Windows Process Activation Service (WAS), który w ramach usług IIS 7.0 i w ramach dowolnej aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-202"> services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="156fd-203">Do hostowania w usługach IIS 5.1 i 6.0, usługa musi używać protokołu HTTP jako protokołu transportowego komunikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-203">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="156fd-204">Aby obsługiwać usługę w ramach usługi IIS 5.1 w wersji 6.0 lub WAS, wykonaj kroki następujące:</span><span class="sxs-lookup"><span data-stu-id="156fd-204">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="156fd-205">Kompiluj typ usługi do zestawu biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="156fd-205">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="156fd-206">Utwórz plik usługi z rozszerzeniem .svc z `@ ServiceHost` dyrektywy do identyfikowania typ usługi:</span><span class="sxs-lookup"><span data-stu-id="156fd-206">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="156fd-207">Skopiuj plik usługi do katalogu wirtualnego, a zestaw w podkatalogu \bin tego katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="156fd-207">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="156fd-208">Skopiuj plik konfiguracji do katalogu wirtualnego i nadaj jej nazwę pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="156fd-208">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="156fd-209">Aplikacja jest dostępna przy użyciu adresu URL usługi pliku w katalogu głównym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-209">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="156fd-210">Na hoście [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi aplikacji .NET, skompiluj typ usługi, w ramach zestawu biblioteki klasy odwołuje się aplikacji i programów aplikacji do hosta przy użyciu usługi <xref:System.ServiceModel.ServiceHost> klasy.</span><span class="sxs-lookup"><span data-stu-id="156fd-210">To host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="156fd-211">Poniżej przedstawiono przykład podstawy programowania wymagane:</span><span class="sxs-lookup"><span data-stu-id="156fd-211">The following is an example of the basic programming required:</span></span>  
  
```  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="156fd-212">W tym przykładzie pokazano, jak adresy dla jednego lub więcej protokołów transportu są określone w konstrukcji <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="156fd-212">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="156fd-213">Te adresy są określane jako adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="156fd-213">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="156fd-214">Podany adres dla dowolnego punktu końcowego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi jest adresem określany względem adresu podstawowego hosta punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="156fd-214">The address provided for any endpoint of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="156fd-215">Host może mieć jeden adres podstawowy dla każdego protokołu transportu komunikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-215">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="156fd-216">W konfiguracji próbki w pliku konfiguracyjnym poprzedniego <xref:System.ServiceModel.BasicHttpBinding> wybrane do używany przez punkt końcowy HTTP jako protokół transportu, dlatego adres punktu końcowego, `EchoService`, jest określany względem adresu podstawowego HTTP hosta.</span><span class="sxs-lookup"><span data-stu-id="156fd-216">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="156fd-217">W przypadku hostów w poprzednim przykładzie, podstawowy adres HTTP jest http://www.contoso.com:8000 /.</span><span class="sxs-lookup"><span data-stu-id="156fd-217">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="156fd-218">Usługi hostowane w usługach IIS lub WAS podstawowy adres jest adresem URL usługi pliku usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-218">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="156fd-219">Tylko usługi hostowanej w usługach IIS lub WAS i które korzystają z protokołu HTTP jako protokołu transportowego wyłącznie, może również użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opcja Tryb zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-219">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode option.</span></span> <span data-ttu-id="156fd-220">Włączenie tej opcji wymaga wykonania następujących czynności.</span><span class="sxs-lookup"><span data-stu-id="156fd-220">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="156fd-221">Należy dodać programistę <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atrybutu typu usługi i określ, czy tryb zgodności ASP.NET jest dozwolona lub wymagana.</span><span class="sxs-lookup"><span data-stu-id="156fd-221">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="156fd-222">Administrator musi skonfigurować aplikację do używania trybu zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-222">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
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
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="156fd-223">aplikacje można również skonfigurować do używania .asmx jako rozszerzenie ich pliki usługi zamiast .svc.</span><span class="sxs-lookup"><span data-stu-id="156fd-223"> applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="156fd-224">Czy opcja może zaoszczędzić z konieczności modyfikowania klientów, które są skonfigurowane do używania adresów URL plików usługi .asmx podczas modyfikowania usługi do użycia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="156fd-224">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="156fd-225">Programowanie klienta</span><span class="sxs-lookup"><span data-stu-id="156fd-225">Client Development</span></span>  
 <span data-ttu-id="156fd-226">Klienci dla usług sieci Web ASP.NET są generowane przy użyciu narzędzia wiersza polecenia WSDL.exe, który zawiera adres URL pliku .asmx jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="156fd-226">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="156fd-227">Narzędzia udostępniane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="156fd-227">The corresponding tool provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="156fd-228">Generuje kod moduł o definicję kontraktu usługi, jak i definicja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta.</span><span class="sxs-lookup"><span data-stu-id="156fd-228">It generates a code module with the definition of the service contract and the definition of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="156fd-229">Generuje plik konfiguracji z adres i powiązanie usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-229">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="156fd-230">W programowanie klienta usługi zdalnej jest ogólnie zaleca się do programu zgodnie z wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="156fd-230">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="156fd-231">Kod wygenerowany przez narzędzie WSDL.exe zawsze zawiera dla synchroniczne i asynchroniczne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="156fd-231">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="156fd-232">Kod wygenerowany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można zapewnić albo wzorzec.</span><span class="sxs-lookup"><span data-stu-id="156fd-232">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="156fd-233">Zapewnia on synchroniczne wzorzec domyślnie.</span><span class="sxs-lookup"><span data-stu-id="156fd-233">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="156fd-234">Jeśli narzędzie jest wykonywane z `/async` przełącznika, a następnie udostępnia wygenerowany kod dla wzorca asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="156fd-234">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="156fd-235">Nie ma żadnej gwarancji, że nazwy w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta generowane przez program ASP. Narzędzie WSDL.exe w sieci, domyślnie odpowiadają nazwom w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wygenerowany przez narzędzie Svcutil.exe klasy klienta.</span><span class="sxs-lookup"><span data-stu-id="156fd-235">There is no guarantee that names in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="156fd-236">W szczególności nazwy właściwości klasy zawierających serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> domyślnie podano sufiks właściwości w kod wygenerowany przez narzędzie Svcutil.exe, które nie jest to za pomocą narzędzia WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="156fd-236">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="156fd-237">Reprezentacja komunikatu</span><span class="sxs-lookup"><span data-stu-id="156fd-237">Message Representation</span></span>  
 <span data-ttu-id="156fd-238">Nagłówki SOAP komunikatów wysyłanych i odbieranych przez usługi sieci Web platformy ASP.NET można dostosować.</span><span class="sxs-lookup"><span data-stu-id="156fd-238">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="156fd-239">Klasa pochodzi od <xref:System.Web.Services.Protocols.SoapHeader> do definiowania struktury nagłówek, a następnie <xref:System.Web.Services.Protocols.SoapHeaderAttribute> służy do wskazania obecności nagłówka.</span><span class="sxs-lookup"><span data-stu-id="156fd-239">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
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
  
 <span data-ttu-id="156fd-240">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zawiera atrybuty, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, i <xref:System.ServiceModel.MessageBodyMemberAttribute> do opisania struktury SOAP komunikatów wysyłanych i odbieranych przez usługę.</span><span class="sxs-lookup"><span data-stu-id="156fd-240">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
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
public class ItemMesage  
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
  
 <span data-ttu-id="156fd-241">Ta składnia daje jawne reprezentację struktury komunikatów, natomiast struktury wiadomości jest implikowana przez kod usługi sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-241">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="156fd-242">Ponadto w składni ASP.NET nagłówki komunikatów są reprezentowane jako właściwości usługi, takie jak `ProtocolHeader` właściwości w poprzednim przykładzie, natomiast w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składni, są one dokładniej reprezentowana jako właściwości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="156fd-242">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="156fd-243">Ponadto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umożliwia nagłówków komunikatów, które mają zostać dodane do konfiguracji punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="156fd-243">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows message headers to be added to the configuration of endpoints.</span></span>  
  
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
  
 <span data-ttu-id="156fd-244">Czy opcja pozwala uniknąć wszystkich odwołań do nagłówków protokołu infrastrukturalne w kodzie dla klienta lub usługę: nagłówki są dodawane do komunikatów z powodu konfiguracji punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="156fd-244">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="156fd-245">Opis usługi</span><span class="sxs-lookup"><span data-stu-id="156fd-245">Service Description</span></span>  
 <span data-ttu-id="156fd-246">Wystawienie żądania HTTP GET dla pliku .asmx usługi sieci Web platformy ASP.NET z zapytaniem WSDL powoduje, że ASP.NET wygeneruje WSDL usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-246">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="156fd-247">Zwraca wartość, która WSDL jako odpowiedzi na żądanie.</span><span class="sxs-lookup"><span data-stu-id="156fd-247">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="156fd-248">ASP.NET 2.0 możliwe do zweryfikowania, że usługa jest zgodne z Basic Profile 1.1 organizacji współdziałanie usług sieci Web (WS-I) oraz do wstawienia oświadczenie, że usługa jest zgodny z do WSDL.</span><span class="sxs-lookup"><span data-stu-id="156fd-248">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="156fd-249">Oznacza to gotowe za pomocą `ConformsTo` i `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="156fd-249">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="156fd-250">Można dostosować WSDL, generujący ASP.NET dla usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-250">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="156fd-251">Dostosowania są wprowadzane przy tworzeniu klasy pochodnej z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> do dodawania elementów WSDL.</span><span class="sxs-lookup"><span data-stu-id="156fd-251">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="156fd-252">Wystawienie żądania HTTP GET z zapytaniem WSDL dla pliku svc z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z punktu końcowego HTTP hostowany w 51 usług IIS 6.0 lub przyczyny WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z WSDL usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-252">Issuing an HTTP GET request with the query WSDL for the .svc file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to respond with WSDL to describe the service.</span></span> <span data-ttu-id="156fd-253">Wystawiania żądania HTTP GET z zapytaniem WSDL podstawowy adres HTTP z usługą hostowaną w aplikacji platformy .NET ma ten sam efekt, jeśli httpGetEnabled jest ustawiona na true.</span><span class="sxs-lookup"><span data-stu-id="156fd-253">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="156fd-254">Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] również odpowiada na żądania WS-MetadataExchange z WSDL, który generuje do opisu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-254">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="156fd-255">Usługi sieci Web programu ASP.NET nie ma wbudowaną obsługę protokołu WS-MetadataExchange żądań.</span><span class="sxs-lookup"><span data-stu-id="156fd-255">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="156fd-256">WSDL który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje można dostosować, często.</span><span class="sxs-lookup"><span data-stu-id="156fd-256">The WSDL that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates can be extensively customized.</span></span> <span data-ttu-id="156fd-257"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Klasa udostępnia niektóre urządzenia do dostosowywania WSDL.</span><span class="sxs-lookup"><span data-stu-id="156fd-257">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="156fd-258">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Można również skonfigurować nie Generowanie języka WSDL, ale raczej przy użyciu statycznego pliku WSDL pod danym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="156fd-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
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
  
## <a name="exception-handling"></a><span data-ttu-id="156fd-259">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="156fd-259">Exception Handling</span></span>  
 <span data-ttu-id="156fd-260">W usługach sieci Web ASP.NET nieobsługiwanych wyjątków są jako błędach SOAP zwracanych do klientów.</span><span class="sxs-lookup"><span data-stu-id="156fd-260">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="156fd-261">Można również jawnie throw wystąpienia <xref:System.Web.Services.Protocols.SoapException> klasy i większą kontrolę nad zawartością błędu protokołu SOAP, który pobiera przesłanych do klienta.</span><span class="sxs-lookup"><span data-stu-id="156fd-261">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="156fd-262">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, nieobsługiwanych wyjątków nie są zwracane do klientów jako błędach SOAP, aby zapobiec przypadkowym przypadkowo za pośrednictwem wyjątki informacji poufnych.</span><span class="sxs-lookup"><span data-stu-id="156fd-262">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="156fd-263">Ustawienie konfiguracji zapewnia ma nieobsługiwane wyjątki zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="156fd-263">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="156fd-264">Aby przywrócić błędach SOAP klientów, może zgłosić wystąpienia typu ogólnego <xref:System.ServiceModel.FaultException%601>za pomocą ogólnego typu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="156fd-264">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="156fd-265">Można również dodać <xref:System.ServiceModel.FaultContractAttribute> atrybuty do operacji, aby określić błędów, które może dać operacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-265">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
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
  
 <span data-ttu-id="156fd-266">Grozi to wyniki możliwych błędów anonsowany w języku WSDL dla usługi, umożliwiając klienckim programistom przewidywać usterek, które można wyniku operacji i zapisu catch odpowiednie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="156fd-266">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
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
  
## <a name="state-management"></a><span data-ttu-id="156fd-267">Stan zarządzania</span><span class="sxs-lookup"><span data-stu-id="156fd-267">State Management</span></span>  
 <span data-ttu-id="156fd-268">Klasa służy do implementacji usługi sieci Web ASP.NET może pochodzić od <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="156fd-268">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="156fd-269">W takim przypadku klasa mogą być programowane w taki sposób, aby użyć <xref:System.Web.Services.WebService> właściwości kontekstu klasy dostęp do podstawowych <xref:System.Web.HttpContext> obiektu.</span><span class="sxs-lookup"><span data-stu-id="156fd-269">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="156fd-270"><xref:System.Web.HttpContext> Obiekt może być używane do aktualizowania i pobierania informacji o stanie aplikacji przy użyciu jego właściwości aplikacji i może służyć do aktualizowania i pobierania informacji o stanie sesji przy użyciu jego właściwość sesji.</span><span class="sxs-lookup"><span data-stu-id="156fd-270">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="156fd-271">Program ASP.NET zapewnia znaczną kontrolę nad którym sesja stanu informacje dostępne za pośrednictwem właściwości sesji <xref:System.Web.HttpContext> są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="156fd-271">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="156fd-272">Może ona przechowywana w plikach cookie, w bazie danych, w pamięci bieżącego serwera lub w pamięci wyznaczonym serwerze.</span><span class="sxs-lookup"><span data-stu-id="156fd-272">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="156fd-273">Wybór jest przeprowadzane w pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-273">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="156fd-274">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Udostępnia obiekty rozszerzalne dla zarządzania stanem.</span><span class="sxs-lookup"><span data-stu-id="156fd-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides extensible objects for state management.</span></span> <span data-ttu-id="156fd-275">Obiekty rozszerzalne są obiektów implementujących <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="156fd-275">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="156fd-276">Obiekty rozszerzalne najważniejsze są <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="156fd-276">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="156fd-277">`ServiceHostBase`pozwala zachować dostęp do stanu, że typy wszystkich wystąpień wszystkich usługi na tym samym hoście, podczas gdy `InstanceContext` służy do zarządzania stanem, który można uzyskać, sprawdzając dowolny kod uruchomiony w ramach tego samego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-277">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="156fd-278">Tutaj, typ usługi `TradingSystem`, ma <xref:System.ServiceModel.ServiceBehaviorAttribute> Określa, że wszystkie wywołania z tej samej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpienie klienta są kierowane do tego samego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-278">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="156fd-279">Klasa, `DealData`, definiuje stan, który można uzyskać, sprawdzając dowolny kod działa w tym samym wystąpieniu typu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-279">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="156fd-280">W kodzie typ usługi, który implementuje jednej z operacji kontraktu usługi `DealData` stan obiektu jest dodawane do stanu bieżącego wystąpienia typu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-280">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="156fd-281">Ten obiekt stanu następnie można je pobrać i zmodyfikowany przez kod, który implementuje innej operacji kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-281">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="156fd-282">ASP.NET zapewnia kontrolę nad, gdy stan informacji w <xref:System.Web.HttpContext> przechowywane klasy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], co najmniej w wersji początkowej sterowanie nie jest dostępne za pośrednictwem przechowywania obiekty rozszerzalne.</span><span class="sxs-lookup"><span data-stu-id="156fd-282">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="156fd-283">Który stanowi bardzo najważniejsze przyczyny wybierając tryb zgodności ASP.NET dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="156fd-283">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="156fd-284">Jeśli konieczne jest zarządzanie stanem można skonfigurować, a następnie umożliwia wybór tryb zgodności ASP.NET, przy użyciu urządzeń z <xref:System.Web.HttpContext> klasy dokładnie tak, jak są one używane w programie ASP.NET, a także skonfigurować gdzie stan informacje zarządzane za pomocą <xref:System.Web.HttpContext> klasy jest przechowywany.</span><span class="sxs-lookup"><span data-stu-id="156fd-284">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="156fd-285">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="156fd-285">Security</span></span>  
 <span data-ttu-id="156fd-286">Opcje dotyczące zabezpieczania usługi sieci Web platformy ASP.NET to zabezpieczanie dowolnej aplikacji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="156fd-286">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="156fd-287">Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje mogą być przechowywane na nie jedynie w ramach usług IIS, ale także w dowolnym pliku wykonywalnego, .NET opcje ochrony [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje muszą być wprowadzane niezależne od funkcji usług IIS.</span><span class="sxs-lookup"><span data-stu-id="156fd-287">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can be hosted not only within IIS but also within any .NET executable, the options for securing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="156fd-288">Jednak urządzenia podana dla usług sieci Web ASP.NET są także dostępne dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-288">However, the facilities provided for ASP.NET Web services are also available for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="156fd-289">Zabezpieczenia: uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="156fd-289">Security: Authentication</span></span>  
 <span data-ttu-id="156fd-290">Usługi IIS oferują urządzenia do kontrolowania dostępu do aplikacji za pomocą których można wybrać dostęp anonimowy lub różne tryby uwierzytelniania: uwierzytelnianie systemu Windows, uwierzytelniania szyfrowanego, uwierzytelnianie podstawowe i uwierzytelnianie usługi .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="156fd-290">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="156fd-291">Opcja uwierzytelniania systemu Windows może służyć do kontrolowania dostępu do usług sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-291">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="156fd-292">Jednakże, gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji są obsługiwane w ramach usług IIS, usługi IIS muszą być skonfigurowane do zezwolenie na dostęp anonimowy do aplikacji, więc uwierzytelniania mogą być zarządzane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] siebie, które obsługują uwierzytelnianie systemu Windows między różnymi innych Opcje.</span><span class="sxs-lookup"><span data-stu-id="156fd-292">However, when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="156fd-293">Inne opcje, które są wbudowane obejmują username tokeny, certyfikaty X.509 tokeny SAML i CardSpace karty, ale może być także definiowane niestandardowych mechanizmów uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="156fd-293">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="156fd-294">Zabezpieczenia: personifikacji</span><span class="sxs-lookup"><span data-stu-id="156fd-294">Security: Impersonation</span></span>  
 <span data-ttu-id="156fd-295">Program ASP.NET udostępnia element tożsamości przez usługę sieci Web ASP.NET może się personifikować określonego użytkownika lub poświadczenia innego użytkownika są dostarczane z bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="156fd-295">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="156fd-296">Ten element służy do konfigurowania personifikacji w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji działających w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-296">That element can be used to configure impersonation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="156fd-297">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System konfiguracji udostępnia własnego elementu tożsamości wyznaczania personifikować określonego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="156fd-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="156fd-298">Ponadto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów i usług można niezależnie skonfigurowane dla personifikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-298">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="156fd-299">Klientów można skonfigurować do personifikacji bieżącego użytkownika podczas ich przesyłania żądań.</span><span class="sxs-lookup"><span data-stu-id="156fd-299">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="156fd-300">Operacje usługi można skonfigurować do personifikacji, niezależnie od użytkownika poświadczeń są dostarczane z bieżącego żądania.</span><span class="sxs-lookup"><span data-stu-id="156fd-300">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="156fd-301">Zabezpieczeń: Przy użyciu list kontroli dostępu autoryzacji</span><span class="sxs-lookup"><span data-stu-id="156fd-301">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="156fd-302">Listy kontroli dostępu (ACL) może służyć do ograniczania dostępu do plików .asmx.</span><span class="sxs-lookup"><span data-stu-id="156fd-302">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="156fd-303">Jednak listy ACL na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pliki SVC są ignorowane, z wyjątkiem w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-303">However, ACLs on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="156fd-304">Zabezpieczeń: Autoryzacji opartej na rolach</span><span class="sxs-lookup"><span data-stu-id="156fd-304">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="156fd-305">Opcję Uwierzytelnianie systemu Windows usług IIS umożliwia w połączeniu z elementem autoryzacji udostępniane przez język konfiguracji ASP.NET ułatwienia autoryzacji opartej na rolach dla usługi sieci Web programu ASP.NET na podstawie grup systemu Windows, do których użytkownicy nie są przypisani .</span><span class="sxs-lookup"><span data-stu-id="156fd-305">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="156fd-306">Platforma ASP.NET 2.0 wprowadzono bardziej ogólne mechanizmu autoryzacji opartej na rolach: dostawców ról.</span><span class="sxs-lookup"><span data-stu-id="156fd-306">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="156fd-307">Dostawcy roli są klasy wszystkie wdrożenia podstawowy interfejs dla badające o rolach, do których użytkownik jest przypisany, że każdy dostawca roli potrafi można pobrać informacji z innego źródła.</span><span class="sxs-lookup"><span data-stu-id="156fd-307">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="156fd-308">Program ASP.NET 2.0 zapewnia dostawcy roli, który można pobrać przypisania roli z bazy danych programu Microsoft SQL Server, a inny, który można pobrać przypisania roli z Menedżera autoryzacji systemu Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="156fd-308">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="156fd-309">Mechanizm dostawcy roli faktycznie mogą być używane niezależnie od platformy ASP.NET, w dowolnej aplikacji .NET, w tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-309">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="156fd-310">Następujące przykładowe konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji pokazuje, jak używanie dostawcy ról ASP.NET to opcja wybrana za pomocą klasy <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="156fd-310">The following sample configuration for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
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
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="156fd-311">Zabezpieczeń: Autoryzacji opartej na oświadczeniach</span><span class="sxs-lookup"><span data-stu-id="156fd-311">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="156fd-312">Jedną z najważniejszych innowacji z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest jego obsługę szczegółowej autoryzacji dostępu do chronionych zasobów na podstawie oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="156fd-312">One of the most important innovations of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="156fd-313">Oświadczeń składa się z typem, prawo i wartość licencji sterowników, na przykład.</span><span class="sxs-lookup"><span data-stu-id="156fd-313">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="156fd-314">Powoduje to dodanie zestaw oświadczeń o elementu nośnego, z których jeden jest elementu nośnego datę urodzenia.</span><span class="sxs-lookup"><span data-stu-id="156fd-314">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="156fd-315">Typ tego oświadczenia jest data urodzenia, gdy wartość oświadczenia jest data urodzenia sterownika.</span><span class="sxs-lookup"><span data-stu-id="156fd-315">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="156fd-316">Uprawnienia, który przyznaje oświadczenie przenoszącej Określa, co można zrobić elementu nośnego z wartości oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="156fd-316">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="156fd-317">W przypadku oświadczeń sterownika daty urodzenia, prawo jest posiadanie: posiada sterownika, że data urodzenia ale nie można na przykład, zmienienia go.</span><span class="sxs-lookup"><span data-stu-id="156fd-317">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="156fd-318">Autoryzacji opartej na oświadczeniach umieszcza autoryzacji opartej na rolach, ponieważ role są typu oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="156fd-318">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="156fd-319">Na podstawie oświadczeń autoryzacji odbywa się przez porównanie zestaw oświadczeń uzyskiwania operacji i, w zależności od wyniku tego porównania, przyznawanie lub odbieranie praw dostępu do operacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-319">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="156fd-320">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], można określić klasę ma być używana do uruchamiania autoryzacji opartej na oświadczeniach, ponownie przez przypisanie wartości do `ServiceAuthorizationManager` właściwość <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="156fd-320">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="156fd-321">Klasy służące do uruchamiania autoryzacji opartej na oświadczeniach muszą pochodzić od <xref:System.ServiceModel.ServiceAuthorizationManager>, która zawiera tylko jedną metodę do zastąpienia, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="156fd-321">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="156fd-322">wywołuje tę metodę, za każdym razem operacja usługi jest wywoływany i udostępnia <xref:System.ServiceModel.OperationContext> obiektu, który ma oświadczenia dla użytkownika w jego `ServiceSecurityContext.AuthorizationContext` właściwości.</span><span class="sxs-lookup"><span data-stu-id="156fd-322"> calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="156fd-323">wykonuje pracę składania roszczeń o użytkowniku z tokenu zabezpieczeń, niezależnie od użytkownika podane dla uwierzytelniania, co pozostawia zadania oceny, czy te oświadczenia są wystarczające dla danej operacji.</span><span class="sxs-lookup"><span data-stu-id="156fd-323"> does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="156fd-324">Czy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie składana oświadczeń z dowolnego rodzaju zabezpieczeń token jest bardzo istotne innowacji, ponieważ sprawia, że kod autoryzacji na podstawie oświadczeń całkowicie niezależna od mechanizmu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="156fd-324">That [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="156fd-325">Z kolei autoryzację za pomocą listy kontroli dostępu lub ról w programie ASP.NET jest ściśle związany z uwierzytelnianiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="156fd-325">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="156fd-326">Zabezpieczenia: poufności</span><span class="sxs-lookup"><span data-stu-id="156fd-326">Security: Confidentiality</span></span>  
 <span data-ttu-id="156fd-327">Poufność wiadomości wymieniane z usługami sieci Web platformy ASP.NET można zapewnić na poziomie transportu przez skonfigurowanie aplikacji w ramach usług IIS do używania Secure Hypertext Transfer Protocol (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="156fd-327">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="156fd-328">Można to zrobić dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje hostowane w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="156fd-328">The same can be done for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted within IIS.</span></span> <span data-ttu-id="156fd-329">Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje hostowane poza usług IIS można również skonfigurować do używania protokołu bezpiecznego transportu.</span><span class="sxs-lookup"><span data-stu-id="156fd-329">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="156fd-330">Większe znaczenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji można również skonfigurować do zabezpieczania komunikatów przed ich transportu, za pomocą protokołu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="156fd-330">More important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="156fd-331">Zabezpieczanie po prostu treść wiadomości przy użyciu WS-Security umożliwi się jako poufne przesyłane przez pośredników przed dotarciem do ostatecznego miejsca przeznaczenia.</span><span class="sxs-lookup"><span data-stu-id="156fd-331">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="156fd-332">Globalizacja</span><span class="sxs-lookup"><span data-stu-id="156fd-332">Globalization</span></span>  
 <span data-ttu-id="156fd-333">Język konfiguracji ASP.NET umożliwia określenie kultury dla poszczególnych usług.</span><span class="sxs-lookup"><span data-stu-id="156fd-333">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="156fd-334">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Nie obsługuje tego ustawienia konfiguracji, z wyjątkiem w trybie zgodności ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="156fd-334">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="156fd-335">Aby zlokalizować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która nie używa tryb zgodności ASP.NET, skompilować typ usługi do zestawów specyficzne dla kultury i ma oddzielne punkty końcowe specyficzne dla kultury dla każdego zestawu specyficzne dla kultury.</span><span class="sxs-lookup"><span data-stu-id="156fd-335">To localize a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="156fd-336">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="156fd-336">See Also</span></span>  
 [<span data-ttu-id="156fd-337">Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów</span><span class="sxs-lookup"><span data-stu-id="156fd-337">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
