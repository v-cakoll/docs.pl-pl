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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 82fb1848fc329db2921b626a894b9f91e766cd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]jest dostępna opcja Tryb zgodności ASP.NET umożliwiające [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji zaprogramowane i skonfigurować usługi sieci Web ASP.NET, takich jak i naśladować ich zachowanie. Poniższe sekcje Porównanie usług sieci Web ASP.NET i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oparte na co jest wymagane do tworzenia aplikacji za pomocą obu tych technologii.  
  
## <a name="data-representation"></a>Reprezentacja wartości danych  
 Rozwój usługi sieci Web ASP.NET zazwyczaj rozpoczyna się od zdefiniowania wszystkich typów złożonych danych, które usługa ma używać. Program ASP.NET korzysta z <xref:System.Xml.Serialization.XmlSerializer> tłumaczenie dane reprezentowane przez typy .NET Framework do pliku XML do przesłania do lub z usługą i translację danych otrzymanych w formacie XML na obiekty .NET Framework. Definiowanie typów złożonych danych, które jest użycie usługi ASP.NET wymaga definicji programu .NET Framework klasy, która <xref:System.Xml.Serialization.XmlSerializer> można serializować do i z pliku XML. Takich klas mogą być zapisywane ręcznie lub generowane na podstawie definicji typu w schemacie XML przy użyciu wiersza polecenia XML schematy/danych typów obsługę narzędzia, xsd.exe.  
  
 Poniżej przedstawiono listę kluczowych problemów dotyczących znać podczas definiowania .NET Framework klasy który <xref:System.Xml.Serialization.XmlSerializer> można serializować do i z pliku XML:  
  
-   Tylko publiczne pola i właściwości obiektów .NET Framework są tłumaczone na XML.  
  
-   Wystąpienia klas kolekcji może być Zserializowany w formacie XML, tylko wtedy, gdy klasy implementować albo <xref:System.Collections.IEnumerable> lub <xref:System.Collections.ICollection> interfejsu.  
  
-   Klasy, które implementują <xref:System.Collections.IDictionary> interfejsu, takich jak <xref:System.Collections.Hashtable>, nie może być serializowany w formacie XML.  
  
-   Świetnie typy w wielu atrybutów <xref:System.Xml.Serialization> przestrzeni nazw można dodać do klasy .NET Framework i jej elementów członkowskich, aby kontrolować sposób wystąpień klasy są reprezentowane w formacie XML.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Projektowanie aplikacji zwykle również rozpoczyna się od definicji typów złożonych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]możliwe do używania takich samych typach .NET Framework jako usługi sieci Web ASP.NET.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> mogą być dodawane do typów .NET Framework do wskazania, że wystąpienie typu zserializowana XML i określonego pola lub właściwości typu mają być serializowane, jak pokazano w następującym przykładowym Kod.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractAttribute> Oznacza, że zero lub więcej pól lub właściwości typu mają być serializowana, podczas gdy <xref:System.Runtime.Serialization.DataMemberAttribute> oznacza określonego pola lub właściwości do serializacji. <xref:System.Runtime.Serialization.DataContractAttribute> Można zastosować do klasy lub struktury. <xref:System.Runtime.Serialization.DataMemberAttribute> Może odnosić się do pola lub właściwości i pola i właściwości, do których zastosowano atrybut może być publicznych lub prywatnych. Wystąpienia typów, które mają <xref:System.Runtime.Serialization.DataContractAttribute> zastosować do nich są określane jako kontraktów danych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Są one serializowane w formacie XML przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Poniżej przedstawiono listę istotnych różnic między <xref:System.Runtime.Serialization.DataContractSerializer> i przy użyciu <xref:System.Xml.Serialization.XmlSerializer> i różnych atrybutów <xref:System.Xml.Serialization> przestrzeni nazw.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> i atrybuty <xref:System.Xml.Serialization> przestrzeni nazw zostały zaprojektowane do umożliwiają mapowania typów .NET Framework dowolnego prawidłowego typu zdefiniowanej w schemacie XML, a więc stanowią bardzo precyzyjną kontrolę nad jak typu są reprezentowane w formacie XML. <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> zapewniają bardzo mało kontrolę nad jak typu są reprezentowane w formacie XML. Można określić tylko obszary nazw i nazwy używany do reprezentowania typu i jego pól lub właściwości w pliku XML i sekwencji, w którym pola i właściwości są wyświetlane w pliku XML:  
  
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
  
     Wszystkie inne informacje o strukturze XML używany do reprezentowania typ architektury .NET jest określany przez <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   Przez nie pozwala na znacznie kontrolę nad jak typ ma być reprezentowane w formacie XML, procesu serializacji staje się bardzo przewidywalną dla <xref:System.Runtime.Serialization.DataContractSerializer>i, w tym samym łatwiejsze do optymalizacji. Praktyczne zaletą projekt <xref:System.Runtime.Serialization.DataContractSerializer> jest lepszą wydajność, około 10 procent lepszą wydajność.  
  
-   Atrybuty do użycia z <xref:System.Xml.Serialization.XmlSerializer> nie wskazują pola lub właściwości typu są serializowane w formacie XML, podczas gdy <xref:System.Runtime.Serialization.DataMemberAttribute> do użytku z <xref:System.Runtime.Serialization.DataContractSerializer> jawnie zawiera pola lub właściwości są serializowane. W związku z tym kontraktów danych są jawne umów dotyczących struktury danych, która aplikacja ma być wysyłania i odbierania.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Można przetworzyć tylko publiczne elementy członkowskie obiektu .NET. w formacie XML, <xref:System.Runtime.Serialization.DataContractSerializer> można przetworzyć elementów członkowskich obiektów w formacie XML niezależnie od modyfikatorów dostępu do tych elementów członkowskich.  
  
-   W wyniku było serializować niepublicznych elementów członkowskich typów w formacie XML, <xref:System.Runtime.Serialization.DataContractSerializer> ma mniej ograniczeń różnych typów .NET, które mogą zserializować w formacie XML. W szczególności może przełożyć na typy XML, takich jak <xref:System.Collections.Hashtable> które implementują <xref:System.Collections.IDictionary> interfejsu. <xref:System.Runtime.Serialization.DataContractSerializer> Jest znacznie bardziej prawdopodobne można było serializować wystąpień dowolnego istniejącego typu .NET w formacie XML bez konieczności albo zmodyfikuj definicję typu, lub opracowanie otokę dla niego.  
  
-   Inny konsekwencją <xref:System.Runtime.Serialization.DataContractSerializer> dostępowi do elementów członkowskich niepublicznego typu jest wymaga pełnego zaufania, podczas gdy <xref:System.Xml.Serialization.XmlSerializer> nie. Pełne zaufanie uprawnienie dostępu kodu zapewnić pełny dostęp do wszystkich zasobów na komputerze, który może być przy użyciu poświadczeń, w których jest wykonywany kod dostępu. Tej opcji należy używać ostrożnie jako w pełni zaufany kod uzyskuje dostęp do wszystkich zasobów na tym komputerze.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Zawiera niektóre pomocy technicznej dla wersji:  
  
    -   <xref:System.Runtime.Serialization.DataMemberAttribute> Ma <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości, któremu można przypisać wartość false dla elementów członkowskich, które są dodawane do nowych wersji kontraktu danych, które nie były obecne w starszych wersjach, umożliwiając aplikacji przy użyciu nowszej wersji kontraktu jako może przetworzyć starszych wersji.  
  
    -   Dzięki użyciu kontraktu danych implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu, co umożliwia <xref:System.Runtime.Serialization.DataContractSerializer> do przekazania elementów członkowskich zdefiniowanych w nowszych wersji kontraktu danych za pomocą aplikacji ze starszymi wersjami kontraktu.  
  
 Mimo wszystko różnice, XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje typu domyślnie jest semantycznie identyczne z pliku XML, do którego <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podana przestrzeni nazw XML jest jawnie zdefiniowany. Poniższe klasy, która ma atrybuty do używania z programem serializatorów, są przetłumaczyć semantycznie identyczne XML przez <xref:System.Xml.Serialization.XmlSerializer> oraz <xref:System.Runtime.Serialization.DataContractAttribute>:  
  
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
  
 Zestaw Windows software development kit (SDK) zawiera narzędzie wiersza polecenia o nazwie [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Narzędzie xsd.exe używane z usługami sieci Web ASP.NET, takich jak Svcutil.exe wygenerować definicje typów danych .NET na podstawie schematu XML. Typy są kontraktów danych, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> może emitować XML w formacie zdefiniowane przez schemat XML; w przeciwnym razie są one przeznaczone do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Narzędzia Svcutil.exe, można również do generowania schematu XML z kontraktów danych przy użyciu jego `/dataContractOnly` przełącznika.  
  
> [!NOTE]
>  Mimo że użycia usług sieci Web ASP.NET <xref:System.Xml.Serialization.XmlSerializer>, i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sprawia, że tryb zgodności ASP.NET [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług naśladować zachowanie usług sieci Web ASP.NET, opcji zgodności ASP.NET nie ogranicza jedną przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Co można nadal używać <xref:System.Runtime.Serialization.DataContractSerializer> z usługi są uruchomione w trybie zgodności ASP.NET.  
  
## <a name="service-development"></a>Projektowanie usługi  
 Aby opracować usługi przy użyciu platformy ASP.NET, został zwyczajowe, aby dodać <xref:System.Web.Services.WebService> atrybutu do klasy i <xref:System.Web.Services.WebMethodAttribute> do dowolnej z metod tej klasy, które mają być operacje usługi:  
  
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
  
 Platforma ASP.NET 2.0 wprowadzono możliwość dodania atrybutu <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> do interfejsu, a nie na klasę i zapisywania klasy do zaimplementowania interfejsu:  
  
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
  
 Użycie tej opcji zaleca się, ponieważ interfejs <xref:System.Web.Services.WebService> atrybutu stanowi kontraktu dla operacji wykonywanych przez usługę mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest udostępniona przez zdefiniowanie co najmniej jednego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych. Punkt końcowy jest określony przez adres i powiązanie kontraktu usługi. Adres Określa, gdzie usługa się znajduje. Powiązanie określa sposób komunikowania się z usługą. Kontrakt usługi określa operacje, które można wykonać usługi.  
  
 Kontrakt usługi są zazwyczaj zdefiniowane, dodając <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> do interfejsu:  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <xref:System.ServiceModel.ServiceContractAttribute> Określa, że interfejs definiuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt usługi i <xref:System.ServiceModel.OperationContractAttribute> wskazuje, jeśli taki występuje, metod interfejsu definiującą operacji kontraktu usługi.  
  
 Po zdefiniowaniu kontraktu usługi jest zaimplementowana w klasie, konfigurując klasa implementuje interfejs, za pomocą której zdefiniowano kontraktu usługi:  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 Klasa, która implementuje kontraktu usługi jest określany jako typ usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Następnym krokiem jest można skojarzyć adres i powiązanie z typem usługi. Które zwykle odbywa się w pliku konfiguracji, edytując plik bezpośrednio lub za pomocą edytora konfiguracji wyposażone [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Oto przykładowy plik konfiguracji.  
  
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
  
 Powiązanie określa zestaw protokołów służący do komunikacji z aplikacją. W poniższej tabeli wymieniono powiązania dostarczane przez system, które reprezentują typowe opcje.  
  
|Nazwa|Cel|  
|----------|-------------|  
|BasicHttpBinding|Współdziałanie z usługami sieci Web i klientami obsługi protokołu WS-BasicProfile 1.1 i podstawowych zabezpieczeń profilu 1.0.|  
|WSHttpBinding|Współdziałanie z usługami sieci Web i klientów, które obsługuje WS-* protokołów za pośrednictwem protokołu HTTP.|  
|WSDualHttpBinding|Komunikację dupleksową HTTP za pomocą którego nie odpowiedzieć bezpośrednio początkowej nadawcy odbiorcy wiadomości początkowej, ale może przekazać dowolną liczbę odpowiedzi przez pewien czas za pośrednictwem protokołu HTTP, zgodnie z WS-* protokołów.|  
|WSFederationBinding|Komunikacji HTTP, w którym można kontrolować dostęp do zasobów usługi na podstawie poświadczeń wystawiony przez dostawcę jawnie określone poświadczenie.|  
|NetTcpBinding|Zabezpieczenia, niezawodne i wysoko wydajnych komunikacji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] oprogramowania jednostek w sieci.|  
|NetNamedPipeBinding|Zabezpieczenia, niezawodne i wysoko wydajnych komunikacji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostek oprogramowania na tym samym komputerze.|  
|NetMsmqBinding|Komunikacja między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostek oprogramowania przy użyciu usługi MSMQ.|  
|MsmqIntegrationBinding|Komunikacja między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostki oprogramowania i inną jednostkę oprogramowania przy użyciu usługi MSMQ.|  
|NetPeerTcpBinding|Komunikacja między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jednostek oprogramowania przy użyciu sieci Peer-to-Peer systemu Windows.|  
  
 Powiązania dostarczane przez system <xref:System.ServiceModel.BasicHttpBinding>, zawiera zestaw protokołów obsługiwanych przez usługi sieci Web ASP.NET.  
  
 Powiązania niestandardowe dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji łatwo są zdefiniowane zgodnie z kolekcji element powiązania klas, które [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa do implementacji poszczególnych protokołów. Nowe elementy powiązania można pisać do reprezentowania dodatkowych protokołów.  
  
 Wewnętrzne zachowanie typu usługi można dostosować za pomocą właściwości rodzina klasy o nazwie zachowania. W tym miejscu <xref:System.ServiceModel.ServiceBehaviorAttribute> klasa jest używana do określenia, czy typ usługi ma być wielowątkowych.  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 Niektóre zachowania, takie jak <xref:System.ServiceModel.ServiceBehaviorAttribute>, atrybutów. Inne, te właściwości, które Administratorzy czy chcesz ustawić, może być modyfikowany w konfiguracji aplikacji.  
  
 W kontekście programowania typów usług częste wykorzystania <xref:System.ServiceModel.OperationContext> klasy. Jego static <xref:System.ServiceModel.OperationContext.Current%2A> właściwości zapewnia dostęp do informacji o kontekście, w którym jest uruchomiona operacja. <xref:System.ServiceModel.OperationContext>jest podobny do obu <xref:System.Web.HttpContext> i <xref:System.EnterpriseServices.ContextUtil> klasy.  
  
## <a name="hosting"></a>Hosting  
 Usługi sieci Web ASP.NET są kompilowane do zestawu biblioteki klas. Plik o nazwie pliku usługi jest warunkiem, że ma rozszerzenie .asmx i zawiera `@ WebService` dyrektywy identyfikujący klasę, która zawiera kod dla usług i zestawu, w którym znajduje się.  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 Pliku usługi jest kopiowana do katalog główny aplikacji ASP.NET w Internet Information Services (IIS) i zestaw jest kopiowana do podkatalogu \bin tego katalogu głównego aplikacji. Aplikacja jest dostępna za pomocą adres URL (adres URL) usługi pliku w katalogu głównym aplikacji.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]łatwo mogą być hostowane usługi, usługi IIS 5.1 i 6.0, Windows Process Activation Service (WAS), który w ramach usług IIS 7.0 i w ramach dowolnej aplikacji .NET. Do hostowania w usługach IIS 5.1 i 6.0, usługa musi używać protokołu HTTP jako protokołu transportowego komunikacji.  
  
 Aby obsługiwać usługę w ramach usługi IIS 5.1 w wersji 6.0 lub WAS, wykonaj kroki następujące:  
  
1.  Kompiluj typ usługi do zestawu biblioteki klas.  
  
2.  Utwórz plik usługi z rozszerzeniem .svc z `@ ServiceHost` dyrektywy do identyfikowania typ usługi:  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  Skopiuj plik usługi do katalogu wirtualnego, a zestaw w podkatalogu \bin tego katalogu wirtualnego.  
  
4.  Skopiuj plik konfiguracji do katalogu wirtualnego i nadaj jej nazwę pliku Web.config.  
  
 Aplikacja jest dostępna przy użyciu adresu URL usługi pliku w katalogu głównym aplikacji.  
  
 Na hoście [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi aplikacji .NET, skompiluj typ usługi, w ramach zestawu biblioteki klasy odwołuje się aplikacji i programów aplikacji do hosta przy użyciu usługi <xref:System.ServiceModel.ServiceHost> klasy. Poniżej przedstawiono przykład podstawy programowania wymagane:  
  
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
  
 W tym przykładzie pokazano, jak adresy dla jednego lub więcej protokołów transportu są określone w konstrukcji <xref:System.ServiceModel.ServiceHost>. Te adresy są określane jako adres podstawowy.  
  
 Podany adres dla dowolnego punktu końcowego z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi jest adresem określany względem adresu podstawowego hosta punktu końcowego. Host może mieć jeden adres podstawowy dla każdego protokołu transportu komunikacji. W konfiguracji próbki w pliku konfiguracyjnym poprzedniego <xref:System.ServiceModel.BasicHttpBinding> wybrane do używany przez punkt końcowy HTTP jako protokół transportu, dlatego adres punktu końcowego, `EchoService`, jest określany względem adresu podstawowego HTTP hosta. W przypadku hostów w poprzednim przykładzie, podstawowy adres HTTP jest http://www.contoso.com:8000 /. Usługi hostowane w usługach IIS lub WAS podstawowy adres jest adresem URL usługi pliku usługi.  
  
 Tylko usługi hostowanej w usługach IIS lub WAS i które korzystają z protokołu HTTP jako protokołu transportowego wyłącznie, może również użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opcja Tryb zgodności ASP.NET. Włączenie tej opcji wymaga wykonania następujących czynności.  
  
1.  Należy dodać programistę <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atrybutu typu usługi i określ, czy tryb zgodności ASP.NET jest dozwolona lub wymagana.  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  Administrator musi skonfigurować aplikację do używania trybu zgodności ASP.NET.  
  
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
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]aplikacje można również skonfigurować do używania .asmx jako rozszerzenie ich pliki usługi zamiast .svc.  
  
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
  
     Czy opcja może zaoszczędzić z konieczności modyfikowania klientów, które są skonfigurowane do używania adresów URL plików usługi .asmx podczas modyfikowania usługi do użycia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="client-development"></a>Programowanie klienta  
 Klienci dla usług sieci Web ASP.NET są generowane przy użyciu narzędzia wiersza polecenia WSDL.exe, który zawiera adres URL pliku .asmx jako dane wejściowe. Narzędzia udostępniane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Generuje kod moduł o definicję kontraktu usługi, jak i definicja [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta. Generuje plik konfiguracji z adres i powiązanie usługi.  
  
 W programowanie klienta usługi zdalnej jest ogólnie zaleca się do programu zgodnie z wzorca asynchronicznego. Kod wygenerowany przez narzędzie WSDL.exe zawsze zawiera dla synchroniczne i asynchroniczne domyślnie. Kod wygenerowany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) można zapewnić albo wzorzec. Zapewnia on synchroniczne wzorzec domyślnie. Jeśli narzędzie jest wykonywane z `/async` przełącznika, a następnie udostępnia wygenerowany kod dla wzorca asynchronicznego.  
  
 Nie ma żadnej gwarancji, że nazwy w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klasy klienta generowane przez program ASP. Narzędzie WSDL.exe w sieci, domyślnie odpowiadają nazwom w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wygenerowany przez narzędzie Svcutil.exe klasy klienta. W szczególności nazwy właściwości klasy zawierających serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> domyślnie podano sufiks właściwości w kod wygenerowany przez narzędzie Svcutil.exe, które nie jest to za pomocą narzędzia WSDL.exe.  
  
## <a name="message-representation"></a>Reprezentacja komunikatu  
 Nagłówki SOAP komunikatów wysyłanych i odbieranych przez usługi sieci Web platformy ASP.NET można dostosować. Klasa pochodzi od <xref:System.Web.Services.Protocols.SoapHeader> do definiowania struktury nagłówek, a następnie <xref:System.Web.Services.Protocols.SoapHeaderAttribute> służy do wskazania obecności nagłówka.  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Zawiera atrybuty, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, i <xref:System.ServiceModel.MessageBodyMemberAttribute> do opisania struktury SOAP komunikatów wysyłanych i odbieranych przez usługę.  
  
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
  
 Ta składnia daje jawne reprezentację struktury komunikatów, natomiast struktury wiadomości jest implikowana przez kod usługi sieci Web ASP.NET. Ponadto w składni ASP.NET nagłówki komunikatów są reprezentowane jako właściwości usługi, takie jak `ProtocolHeader` właściwości w poprzednim przykładzie, natomiast w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składni, są one dokładniej reprezentowana jako właściwości wiadomości. Ponadto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umożliwia nagłówków komunikatów, które mają zostać dodane do konfiguracji punktów końcowych.  
  
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
  
 Czy opcja pozwala uniknąć wszystkich odwołań do nagłówków protokołu infrastrukturalne w kodzie dla klienta lub usługę: nagłówki są dodawane do komunikatów z powodu konfiguracji punktu końcowego.  
  
## <a name="service-description"></a>Opis usługi  
 Wystawienie żądania HTTP GET dla pliku .asmx usługi sieci Web platformy ASP.NET z zapytaniem WSDL powoduje, że ASP.NET wygeneruje WSDL usługi. Zwraca wartość, która WSDL jako odpowiedzi na żądanie.  
  
 ASP.NET 2.0 możliwe do zweryfikowania, że usługa jest zgodne z Basic Profile 1.1 organizacji współdziałanie usług sieci Web (WS-I) oraz do wstawienia oświadczenie, że usługa jest zgodny z do WSDL. Oznacza to gotowe za pomocą `ConformsTo` i `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atrybutu.  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 Można dostosować WSDL, generujący ASP.NET dla usługi. Dostosowania są wprowadzane przy tworzeniu klasy pochodnej z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> do dodawania elementów WSDL.  
  
 Wystawienie żądania HTTP GET z zapytaniem WSDL dla pliku svc z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z punktu końcowego HTTP hostowany w 51 usług IIS 6.0 lub przyczyny WAS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] z WSDL usługi. Wystawiania żądania HTTP GET z zapytaniem WSDL podstawowy adres HTTP z usługą hostowaną w aplikacji platformy .NET ma ten sam efekt, jeśli httpGetEnabled jest ustawiona na true.  
  
 Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] również odpowiada na żądania WS-MetadataExchange z WSDL, który generuje do opisu usługi. Usługi sieci Web programu ASP.NET nie ma wbudowaną obsługę protokołu WS-MetadataExchange żądań.  
  
 WSDL który [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje można dostosować, często. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Klasa udostępnia niektóre urządzenia do dostosowywania WSDL. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Można również skonfigurować nie Generowanie języka WSDL, ale raczej przy użyciu statycznego pliku WSDL pod danym adresem URL.  
  
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
  
## <a name="exception-handling"></a>Obsługa wyjątków  
 W usługach sieci Web ASP.NET nieobsługiwanych wyjątków są jako błędach SOAP zwracanych do klientów. Można również jawnie throw wystąpienia <xref:System.Web.Services.Protocols.SoapException> klasy i większą kontrolę nad zawartością błędu protokołu SOAP, który pobiera przesłanych do klienta.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, nieobsługiwanych wyjątków nie są zwracane do klientów jako błędach SOAP, aby zapobiec przypadkowym przypadkowo za pośrednictwem wyjątki informacji poufnych. Ustawienie konfiguracji zapewnia ma nieobsługiwane wyjątki zwracanych do klientów na potrzeby debugowania.  
  
 Aby przywrócić błędach SOAP klientów, może zgłosić wystąpienia typu ogólnego <xref:System.ServiceModel.FaultException%601>za pomocą ogólnego typu kontraktu danych. Można również dodać <xref:System.ServiceModel.FaultContractAttribute> atrybuty do operacji, aby określić błędów, które może dać operacji.  
  
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
  
 Grozi to wyniki możliwych błędów anonsowany w języku WSDL dla usługi, umożliwiając klienckim programistom przewidywać usterek, które można wyniku operacji i zapisu catch odpowiednie instrukcje.  
  
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
  
## <a name="state-management"></a>Stan zarządzania  
 Klasa służy do implementacji usługi sieci Web ASP.NET może pochodzić od <xref:System.Web.Services.WebService>.  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 W takim przypadku klasa mogą być programowane w taki sposób, aby użyć <xref:System.Web.Services.WebService> właściwości kontekstu klasy dostęp do podstawowych <xref:System.Web.HttpContext> obiektu. <xref:System.Web.HttpContext> Obiekt może być używane do aktualizowania i pobierania informacji o stanie aplikacji przy użyciu jego właściwości aplikacji i może służyć do aktualizowania i pobierania informacji o stanie sesji przy użyciu jego właściwość sesji.  
  
 Program ASP.NET zapewnia znaczną kontrolę nad którym sesja stanu informacje dostępne za pośrednictwem właściwości sesji <xref:System.Web.HttpContext> są przechowywane. Może ona przechowywana w plikach cookie, w bazie danych, w pamięci bieżącego serwera lub w pamięci wyznaczonym serwerze. Wybór jest przeprowadzane w pliku konfiguracji usługi.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Udostępnia obiekty rozszerzalne dla zarządzania stanem. Obiekty rozszerzalne są obiektów implementujących <xref:System.ServiceModel.IExtensibleObject%601>. Obiekty rozszerzalne najważniejsze są <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase`pozwala zachować dostęp do stanu, że typy wszystkich wystąpień wszystkich usługi na tym samym hoście, podczas gdy `InstanceContext` służy do zarządzania stanem, który można uzyskać, sprawdzając dowolny kod uruchomiony w ramach tego samego wystąpienia typu usługi.  
  
 Tutaj, typ usługi `TradingSystem`, ma <xref:System.ServiceModel.ServiceBehaviorAttribute> Określa, że wszystkie wywołania z tej samej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpienie klienta są kierowane do tego samego wystąpienia typu usługi.  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 Klasa, `DealData`, definiuje stan, który można uzyskać, sprawdzając dowolny kod działa w tym samym wystąpieniu typu usługi.  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 W kodzie typ usługi, który implementuje jednej z operacji kontraktu usługi `DealData` stan obiektu jest dodawane do stanu bieżącego wystąpienia typu usługi.  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 Ten obiekt stanu następnie można je pobrać i zmodyfikowany przez kod, który implementuje innej operacji kontraktu usługi.  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 ASP.NET zapewnia kontrolę nad, gdy stan informacji w <xref:System.Web.HttpContext> przechowywane klasy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], co najmniej w wersji początkowej sterowanie nie jest dostępne za pośrednictwem przechowywania obiekty rozszerzalne. Który stanowi bardzo najważniejsze przyczyny wybierając tryb zgodności ASP.NET dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. Jeśli konieczne jest zarządzanie stanem można skonfigurować, a następnie umożliwia wybór tryb zgodności ASP.NET, przy użyciu urządzeń z <xref:System.Web.HttpContext> klasy dokładnie tak, jak są one używane w programie ASP.NET, a także skonfigurować gdzie stan informacje zarządzane za pomocą <xref:System.Web.HttpContext> klasy jest przechowywany.  
  
## <a name="security"></a>Zabezpieczenia  
 Opcje dotyczące zabezpieczania usługi sieci Web platformy ASP.NET to zabezpieczanie dowolnej aplikacji usług IIS. Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje mogą być przechowywane na nie jedynie w ramach usług IIS, ale także w dowolnym pliku wykonywalnego, .NET opcje ochrony [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje muszą być wprowadzane niezależne od funkcji usług IIS. Jednak urządzenia podana dla usług sieci Web ASP.NET są także dostępne dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi działające w trybie zgodności ASP.NET.  
  
### <a name="security-authentication"></a>Zabezpieczenia: uwierzytelnianie  
 Usługi IIS oferują urządzenia do kontrolowania dostępu do aplikacji za pomocą których można wybrać dostęp anonimowy lub różne tryby uwierzytelniania: uwierzytelnianie systemu Windows, uwierzytelniania szyfrowanego, uwierzytelnianie podstawowe i uwierzytelnianie usługi .NET Passport. Opcja uwierzytelniania systemu Windows może służyć do kontrolowania dostępu do usług sieci Web ASP.NET. Jednakże, gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji są obsługiwane w ramach usług IIS, usługi IIS muszą być skonfigurowane do zezwolenie na dostęp anonimowy do aplikacji, więc uwierzytelniania mogą być zarządzane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] siebie, które obsługują uwierzytelnianie systemu Windows między różnymi innych Opcje. Inne opcje, które są wbudowane obejmują username tokeny, certyfikaty X.509 tokeny SAML i CardSpace karty, ale może być także definiowane niestandardowych mechanizmów uwierzytelniania.  
  
### <a name="security-impersonation"></a>Zabezpieczenia: personifikacji  
 Program ASP.NET udostępnia element tożsamości przez usługę sieci Web ASP.NET może się personifikować określonego użytkownika lub poświadczenia innego użytkownika są dostarczane z bieżącego żądania. Ten element służy do konfigurowania personifikacji w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji działających w trybie zgodności ASP.NET.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System konfiguracji udostępnia własnego elementu tożsamości wyznaczania personifikować określonego użytkownika. Ponadto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów i usług można niezależnie skonfigurowane dla personifikacji. Klientów można skonfigurować do personifikacji bieżącego użytkownika podczas ich przesyłania żądań.  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 Operacje usługi można skonfigurować do personifikacji, niezależnie od użytkownika poświadczeń są dostarczane z bieżącego żądania.  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a>Zabezpieczeń: Przy użyciu list kontroli dostępu autoryzacji  
 Listy kontroli dostępu (ACL) może służyć do ograniczania dostępu do plików .asmx. Jednak listy ACL na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pliki SVC są ignorowane, z wyjątkiem w trybie zgodności ASP.NET.  
  
### <a name="security-role-based-authorization"></a>Zabezpieczeń: Autoryzacji opartej na rolach  
 Opcję Uwierzytelnianie systemu Windows usług IIS umożliwia w połączeniu z elementem autoryzacji udostępniane przez język konfiguracji ASP.NET ułatwienia autoryzacji opartej na rolach dla usługi sieci Web programu ASP.NET na podstawie grup systemu Windows, do których użytkownicy nie są przypisani . Platforma ASP.NET 2.0 wprowadzono bardziej ogólne mechanizmu autoryzacji opartej na rolach: dostawców ról.  
  
 Dostawcy roli są klasy wszystkie wdrożenia podstawowy interfejs dla badające o rolach, do których użytkownik jest przypisany, że każdy dostawca roli potrafi można pobrać informacji z innego źródła. Program ASP.NET 2.0 zapewnia dostawcy roli, który można pobrać przypisania roli z bazy danych programu Microsoft SQL Server, a inny, który można pobrać przypisania roli z Menedżera autoryzacji systemu Windows Server 2003.  
  
 Mechanizm dostawcy roli faktycznie mogą być używane niezależnie od platformy ASP.NET, w dowolnej aplikacji .NET, w tym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji. Następujące przykładowe konfiguracji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji pokazuje, jak używanie dostawcy ról ASP.NET to opcja wybrana za pomocą klasy <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
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
  
### <a name="security-claims-based-authorization"></a>Zabezpieczeń: Autoryzacji opartej na oświadczeniach  
 Jedną z najważniejszych innowacji z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest jego obsługę szczegółowej autoryzacji dostępu do chronionych zasobów na podstawie oświadczeń. Oświadczeń składa się z typem, prawo i wartość licencji sterowników, na przykład. Powoduje to dodanie zestaw oświadczeń o elementu nośnego, z których jeden jest elementu nośnego datę urodzenia. Typ tego oświadczenia jest data urodzenia, gdy wartość oświadczenia jest data urodzenia sterownika. Uprawnienia, który przyznaje oświadczenie przenoszącej Określa, co można zrobić elementu nośnego z wartości oświadczenia. W przypadku oświadczeń sterownika daty urodzenia, prawo jest posiadanie: posiada sterownika, że data urodzenia ale nie można na przykład, zmienienia go. Autoryzacji opartej na oświadczeniach umieszcza autoryzacji opartej na rolach, ponieważ role są typu oświadczenia.  
  
 Na podstawie oświadczeń autoryzacji odbywa się przez porównanie zestaw oświadczeń uzyskiwania operacji i, w zależności od wyniku tego porównania, przyznawanie lub odbieranie praw dostępu do operacji. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], można określić klasę ma być używana do uruchamiania autoryzacji opartej na oświadczeniach, ponownie przez przypisanie wartości do `ServiceAuthorizationManager` właściwość <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 Klasy służące do uruchamiania autoryzacji opartej na oświadczeniach muszą pochodzić od <xref:System.ServiceModel.ServiceAuthorizationManager>, która zawiera tylko jedną metodę do zastąpienia, `AccessCheck()`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wywołuje tę metodę, za każdym razem operacja usługi jest wywoływany i udostępnia <xref:System.ServiceModel.OperationContext> obiektu, który ma oświadczenia dla użytkownika w jego `ServiceSecurityContext.AuthorizationContext` właściwości. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]wykonuje pracę składania roszczeń o użytkowniku z tokenu zabezpieczeń, niezależnie od użytkownika podane dla uwierzytelniania, co pozostawia zadania oceny, czy te oświadczenia są wystarczające dla danej operacji.  
  
 Czy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie składana oświadczeń z dowolnego rodzaju zabezpieczeń token jest bardzo istotne innowacji, ponieważ sprawia, że kod autoryzacji na podstawie oświadczeń całkowicie niezależna od mechanizmu uwierzytelniania. Z kolei autoryzację za pomocą listy kontroli dostępu lub ról w programie ASP.NET jest ściśle związany z uwierzytelnianiem systemu Windows.  
  
### <a name="security-confidentiality"></a>Zabezpieczenia: poufności  
 Poufność wiadomości wymieniane z usługami sieci Web platformy ASP.NET można zapewnić na poziomie transportu przez skonfigurowanie aplikacji w ramach usług IIS do używania Secure Hypertext Transfer Protocol (HTTPS). Można to zrobić dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje hostowane w usługach IIS. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacje hostowane poza usług IIS można również skonfigurować do używania protokołu bezpiecznego transportu. Większe znaczenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji można również skonfigurować do zabezpieczania komunikatów przed ich transportu, za pomocą protokołu WS-Security. Zabezpieczanie po prostu treść wiadomości przy użyciu WS-Security umożliwi się jako poufne przesyłane przez pośredników przed dotarciem do ostatecznego miejsca przeznaczenia.  
  
## <a name="globalization"></a>Globalizacja  
 Język konfiguracji ASP.NET umożliwia określenie kultury dla poszczególnych usług. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Nie obsługuje tego ustawienia konfiguracji, z wyjątkiem w trybie zgodności ASP.NET. Aby zlokalizować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która nie używa tryb zgodności ASP.NET, skompilować typ usługi do zestawów specyficzne dla kultury i ma oddzielne punkty końcowe specyficzne dla kultury dla każdego zestawu specyficzne dla kultury.  
  
## <a name="see-also"></a>Zobacz też  
 [Porównanie usług sieci Web ASP.NET i WCF na podstawie przeznaczenia oraz stosowanych standardów](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
