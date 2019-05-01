---
title: Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: e5d249514ecad7507235bb8bd354c80bdc17c5dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857593"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych

Windows Communication Foundation (WCF) znajduje się opcja Tryb zgodności ASP.NET umożliwiają aplikacjom WCF zaprogramowane i skonfigurowane, takich jak usługi sieci Web platformy ASP.NET i naśladować ich zachowania. W poniższych sekcjach porównano usługi sieci Web platformy ASP.NET i WCF oparte na co jest wymagane do tworzenia aplikacji przy użyciu obu technologii.

## <a name="data-representation"></a>Reprezentacja danych

Tworzenie usługi sieci Web programu ASP.NET zwykle zaczyna się od definiowania wszystkich typów złożonych danych, które jest użycie usługi. ASP.NET opiera się na <xref:System.Xml.Serialization.XmlSerializer> do translacji dane reprezentowane przez typów programu .NET Framework do pliku XML w celu przesłania go do lub z usługi i translację dane odebrane w formacie XML do obiektów platformy .NET Framework. Definiowanie typów złożonych danych, które jest użycie usługi ASP.NET wymaga definicji programu .NET Framework klas <xref:System.Xml.Serialization.XmlSerializer> może wykonywać serializację do i z pliku XML. Takich klas mogą być zapisywane ręcznie lub generowany na podstawie definicje typów w schemacie XML przy użyciu wiersza polecenia XML schematów/danych typów obsługę narzędzia, xsd.exe.

Oto lista kluczowych problemów, aby dowiedzieć się, gdy Definiowanie .NET Framework klas <xref:System.Xml.Serialization.XmlSerializer> może wykonywać serializację do i z pliku XML:

- Tylko pola publiczne i właściwości obiektów .NET Framework są tłumaczone na XML.

- Wystąpienia klas kolekcji może być Zserializowany w formacie XML, tylko wtedy, gdy klasy implementuje albo <xref:System.Collections.IEnumerable> lub <xref:System.Collections.ICollection> interfejsu.

- Klasy, które implementują <xref:System.Collections.IDictionary> interfejsu, takich jak <xref:System.Collections.Hashtable>, nie może być serializowany do XML.

- Świetnie atrybutu wiele typów w <xref:System.Xml.Serialization> przestrzeni nazw mogą być dodawane do klasy .NET Framework i jej elementów członkowskich, aby kontrolować sposób wystąpienia klasy są reprezentowane w formacie XML.

Tworzenie aplikacji WCF zwykle także rozpoczyna się od definicji typów złożonych. Usługi WCF może również używać tych samych typów programu .NET Framework jako usług sieci Web platformy ASP.NET.

WCF<xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> mogą być dodawane do typów programu .NET Framework, aby wskazać, że wystąpień typu mają być serializowany do XML i które pola lub właściwości typu mają być Zserializowany, jak pokazano w poniższym przykładowym kodzie.

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

<xref:System.Runtime.Serialization.DataContractAttribute> Oznacza, że zero lub więcej z typu pola lub właściwości mają być Zserializowany, podczas gdy <xref:System.Runtime.Serialization.DataMemberAttribute> wskazuje, że określonego pola lub właściwości jest serializacji. <xref:System.Runtime.Serialization.DataContractAttribute> Można zastosować do klasy lub struktury. <xref:System.Runtime.Serialization.DataMemberAttribute> Mogą być stosowane do pola lub właściwości i pola i właściwości, do których zastosowano ten atrybut może być publicznym lub prywatnym. Wystąpień typów, które mają <xref:System.Runtime.Serialization.DataContractAttribute> stosowane do ich są określane jako dane zamówień w programie WCF. Są one serializacji do formatu XML przy użyciu <xref:System.Runtime.Serialization.DataContractSerializer>.

Poniżej przedstawiono listę istotne różnice między <xref:System.Runtime.Serialization.DataContractSerializer> i przy użyciu <xref:System.Xml.Serialization.XmlSerializer> i różne atrybuty <xref:System.Xml.Serialization> przestrzeni nazw.

- <xref:System.Xml.Serialization.XmlSerializer> i atrybutów <xref:System.Xml.Serialization> przestrzeni nazw są zaprojektowane, aby umożliwić do mapowania typów programu .NET Framework na dowolny prawidłowy typ zdefiniowanej w schemacie XML, a więc zapewniają dla bardzo precyzyjną kontrolę nad tym, jak typ są reprezentowane w formacie XML. <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> zapewniają bardzo mało kontrolę nad jak typ są reprezentowane w formacie XML. Można określić tylko obszary nazw i nazwy, używana do reprezentowania typu i jego pól lub właściwości w pliku XML i kolejność, w jakiej pola i właściwości są wyświetlane w pliku XML:

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

    Wszystkie inne informacje o strukturze XML używany do reprezentowania typ architektury .NET jest określana przez <xref:System.Runtime.Serialization.DataContractSerializer>.

- Przez nie pozwala na znacznie kontrolę nad jak typ ma być reprezentowane w formacie XML, procesem serializacji staje się bardzo przewidywalny dla <xref:System.Runtime.Serialization.DataContractSerializer>i dzięki temu łatwiej optymalizacji. Praktyczne zaletą projektowania <xref:System.Runtime.Serialization.DataContractSerializer> jest lepszą wydajność, około dziesięciu procent lepszą wydajność.

- Atrybuty do użycia z usługą <xref:System.Xml.Serialization.XmlSerializer> nie wskazują pola lub właściwości typu są serializowane w formacie XML, natomiast <xref:System.Runtime.Serialization.DataMemberAttribute> do użytku z programem <xref:System.Runtime.Serialization.DataContractSerializer> pokazuje jawnie, właściwości lub pól, które są serializowane. Dlatego kontraktów danych są jawne kontraktach struktury danych, która aplikacja ma być wysyłania i odbierania.

- <xref:System.Xml.Serialization.XmlSerializer> Można tłumaczyć tylko publiczne elementy członkowskie obiektu platformy .NET do formatu XML, <xref:System.Runtime.Serialization.DataContractSerializer> może dokonywać translacji elementy członkowskie obiektów do formatu XML niezależnie od tego, modyfikatory dostępu dla tych członków.

- W wyniku jest możliwe do serializacji elementów członkowskich niepublicznych typy w formacie XML, <xref:System.Runtime.Serialization.DataContractSerializer> ma mniej ograniczeń różnych typów .NET, które mogą zserializować do formatu XML. W szczególności można tłumaczyć na typy XML, takich jak <xref:System.Collections.Hashtable> które implementują <xref:System.Collections.IDictionary> interfejsu. <xref:System.Runtime.Serialization.DataContractSerializer> Jest znacznie bardziej prawdopodobne można było serializować wystąpień wszelkie istniejące typ architektury .NET do formatu XML bez konieczności tworzenia otoki dla niego lub zmodyfikuj definicję typu.

- Inny konsekwencją <xref:System.Runtime.Serialization.DataContractSerializer> możliwość uzyskania dostępu do elementów członkowskich niepublicznych typu jest wymaga pełnego zaufania, natomiast <xref:System.Xml.Serialization.XmlSerializer> nie. Uprawnienie Full Trust dostępu kodu zapewnia pełny dostęp do wszystkich zasobów na komputerze, który jest możliwy przy użyciu poświadczeń, w których kod jest wykonywany. Ta opcja powinna być używana z rozwagą, zgodnie z w pełni zaufany kod uzyskuje dostęp do wszystkich zasobów na komputerze.

- <xref:System.Runtime.Serialization.DataContractSerializer> Zawiera niektóre obsługę wersji:

    - <xref:System.Runtime.Serialization.DataMemberAttribute> Ma <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwość, którą można przypisać wartość false dla elementów członkowskich, które są dodawane do nowych wersji kontraktu danych, które nie były obecne w starszych wersjach, umożliwiając aplikacji z nowszą wersją kontraktu jako Umożliwia przetwarzanie wcześniejszych wersji.

    - Dzięki implementacji kontraktu danych <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu, jeden Zezwalaj <xref:System.Runtime.Serialization.DataContractSerializer> do przekazania składowych zdefiniowanych w nowszych wersjach kontraktu danych za pomocą aplikacji ze starszymi wersjami kontraktu.

Pomimo wszystkich różnic, XML, do którego <xref:System.Xml.Serialization.XmlSerializer> serializuje semantycznie taka sama jak XML, do którego jest typem domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typem parametru przestrzeni nazw XML jest jawnie zdefiniowany. Następujące klasy, która zawiera atrybuty do używania z programem serializatory, jest tłumaczony na semantycznie identyczne XML przez <xref:System.Xml.Serialization.XmlSerializer> i <xref:System.Runtime.Serialization.DataContractAttribute>:

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

Zestaw Windows software development kit (SDK) zawiera narzędzia wiersza polecenia o nazwie [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Narzędzia xsd.exe używać z usługami sieci Web platformy ASP.NET, takich jak Svcutil.exe może generować definicje typów danych .NET ze schematu XML. Istnieją typy kontraktów danych, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> może emitować XML w formacie definiowana przez schemat XML; w przeciwnym razie są przeznaczone do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Svcutil.exe można również wygenerować schematu XML z kontraktów danych przy użyciu jego `dataContractOnly` przełącznika.

> [!NOTE]
> Mimo że użycia usług sieci Web platformy ASP.NET <xref:System.Xml.Serialization.XmlSerializer>, a tryb zgodności WCF ASP.NET sprawia, że usługi WCF, które naśladują zachowanie usług sieci Web platformy ASP.NET, opcję zgodności ASP.NET nie ogranicza do przy użyciu <xref:System.Xml.Serialization.XmlSerializer>. Jeden można nadal używać <xref:System.Runtime.Serialization.DataContractSerializer> za pomocą usług działających w trybie zgodności platformy ASP.NET.

## <a name="service-development"></a>Tworzenie usługi

Tworzenie usługi przy użyciu platformy ASP.NET, był zwyczajowego, aby dodać <xref:System.Web.Services.WebService> atrybutu dla klasy i <xref:System.Web.Services.WebMethodAttribute> do dowolnej metody tej klasy, które mają być operacje usługi:

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

Program ASP.NET 2.0 wprowadzono możliwość dodania atrybutu <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> do interfejsu, a nie klasę w celu zapisywania klasy do zaimplementowania interfejsu:

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

Użycie tej opcji zaleca się, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybut definiuje kontrakt dla operacji wykonywanych przez usługę, która może być ponownie używane z różnymi klasami, które mogą implementować tej samej umowy na różne sposoby.

Usługa WCF jest zapewniana przez definiowanie punktami końcowymi programu WCF. Punkt końcowy jest definiowany przez adres i powiązanie kontraktu usługi. Adres Określa, gdzie usługa się znajduje. Powiązanie określa sposób komunikowania się z usługą. Kontrakt usługi określa operacje, które można wykonać usługi.

Kontrakt usługi jest zwykle definiowana jako pierwsza, dodając <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> do interfejsu:

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<xref:System.ServiceModel.ServiceContractAttribute> Określa, że interfejs definiuje kontrakt usługi WCF i <xref:System.ServiceModel.OperationContractAttribute> wskazuje, ile, metod interfejsu definiującą operacji kontraktu usługi.

Po zdefiniowaniu kontraktu usługi jest zaimplementowana w klasie, konfigurując klasy implementuj interfejs za pomocą którego zdefiniowano kontraktu usługi:

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

Klasa, która implementuje kontraktu usługi jest określany jako usługę, wpisz w programie WCF.

Następnym krokiem jest, aby skojarzyć adres i powiązanie z typem usługi. Który odbywa się zwykle w pliku konfiguracji, edytując plik bezpośrednio lub za pomocą edytora konfiguracji dostarczane z programem WCF. Oto przykładowy plik konfiguracji.

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

Powiązanie określa zestaw protokołów do komunikacji z aplikacją. W poniższej tabeli wymieniono powiązania dostarczane przez system, które reprezentują typowe opcje.

|Nazwa|Cel|
|----------|-------------|
|BasicHttpBinding|Współdziałanie z usługami sieci Web i klientów obsługi protokołu WS-BasicProfile 1.1 i podstawowe 1.0 profilu zabezpieczeń.|
|WSHttpBinding|Współdziałanie z usługami sieci Web i klientów, którzy obsługują WS-* protokołów za pośrednictwem protokołu HTTP.|
|WSDualHttpBinding|Komunikację dupleksową HTTP za pomocą którego odbiorca pierwszy komunikat odpowiadaj bezpośrednio na początkowej nadawcy, ale może przekazać dowolną liczbę odpowiedzi w określonym czasie przy użyciu protokołu HTTP, zgodnie z WS-* protokołów.|
|WSFederationBinding|Protokołu HTTP do komunikacji, w którym można kontrolować dostęp do zasobów usługi oparte na poświadczeniach wystawione przez dostawcę jawnie określone poświadczenie.|
|NetTcpBinding|Bezpieczne, niezawodne i wysoko wydajnych komunikację między jednostkami oprogramowania WCF, sieciach.|
|NetNamedPipeBinding|Bezpieczne, niezawodne i wysoko wydajnych komunikację między jednostkami oprogramowania WCF na tym samym komputerze.|
|NetMsmqBinding|Komunikacja między jednostkami oprogramowania WCF za pomocą usługi MSMQ.|
|MsmqIntegrationBinding|Komunikacja między jednostką oprogramowania WCF i innej jednostki oprogramowania za pomocą usługi MSMQ.|
|NetPeerTcpBinding|Komunikacja między jednostkami oprogramowania WCF za pomocą sieci Peer-to-Peer Windows.|

Powiązania dostarczane przez system <xref:System.ServiceModel.BasicHttpBinding>, zawiera zestaw protokołów obsługiwanych przez usługi sieci Web platformy ASP.NET.

Powiązań niestandardowych dla aplikacji WCF łatwo są definiowane jako kolekcje klas element powiązania, które korzysta z usługi WCF do zaimplementowania poszczególnych protokołów. Nowe elementy powiązania można zapisać do reprezentowania dodatkowych protokołów.

Wewnętrzne zachowanie typu usługi można dostosować za pomocą właściwości rodzina klasy o nazwie zachowania. W tym miejscu <xref:System.ServiceModel.ServiceBehaviorAttribute> klasa jest używana do określenia, że typ usługi ma być wielowątkowych.

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

Niektórych zachowań, takich jak <xref:System.ServiceModel.ServiceBehaviorAttribute>, atrybutów. Inne, te z właściwościami, które Administratorzy, będzie chciała ustawić, można zmodyfikować w konfiguracji aplikacji.

W programowaniu typów usług, często stosuje się <xref:System.ServiceModel.OperationContext> klasy. Jego statyczny <xref:System.ServiceModel.OperationContext.Current%2A> właściwości zapewnia dostęp do informacji o kontekście, w którym jest uruchomiona operacja. <xref:System.ServiceModel.OperationContext> jest podobny do obu <xref:System.Web.HttpContext> i <xref:System.EnterpriseServices.ContextUtil> klasy.

## <a name="hosting"></a>Hosting

Usługi sieci Web platformy ASP.NET są kompilowane w zestawie biblioteki klas. Plik o nazwie pliku usługi jest warunkiem, że .asmx rozszerzenie, a następnie zawiera `@ WebService` dyrektywę, który identyfikuje klasę, która zawiera kod dla usługi i zestawu, w którym znajduje się.

```
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>
```

Plik usługi jest kopiowana do katalog główny aplikacji ASP.NET w Internet Information Services (IIS), a zestaw jest kopiowana do podkatalogu \bin ten katalog główny aplikacji. Aplikacja będzie dostępna przy użyciu uniwersalnego lokatora zasobów (URL) pliku usługi w katalogu głównym aplikacji.

Łatwo można hostować usługi WCF, usługi IIS 5.1 i 6.0, Windows Process Activation Service (WAS), który znajduje się w ramach usług IIS 7.0 i w ramach dowolnej aplikacji .NET. Do hostowania w usługach IIS 5.1 i 6.0, jako protokół transportowy komunikacji usługi należy użyć protokołu HTTP.

Aby hostować usługi w ramach usługi IIS 5.1 w wersji 6.0 lub WAS, wykonaj kroki poniżej:

1. Skompiluj typ usługi, w zestawie biblioteki klas.

2. Utwórz plik usługi z rozszerzeniem .svc z `@ ServiceHost` dyrektywy do identyfikowania typ usługi:

    ```
    <%@ServiceHost language="c#" Service="MyService" %>
    ```

3. Skopiuj plik usługi do katalogu wirtualnego, a zestaw w podkatalogu \bin tego katalogu wirtualnego.

4. Skopiuj plik konfiguracji do katalogu wirtualnego, a następnie nadaj mu nazwę pliku Web.config.

 Aplikacja będzie dostępna przy użyciu adresu URL pliku usługi w katalogu głównym aplikacji.

 Hostowanie usługi WCF w ramach aplikacji .NET, skompilować typ usługi, w zestawie biblioteki klas przywoływany przez aplikację i ją do hosta usługi przy użyciu programu <xref:System.ServiceModel.ServiceHost> klasy. Oto przykład podstawy programowania wymagane:

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

Ten przykład przedstawia, jak podano adresy dla co najmniej jeden protokoły transportowe będące w konstrukcji <xref:System.ServiceModel.ServiceHost>. Te adresy są określane jako adres podstawowy.

Określony dla dowolnego punktu końcowego usługi WCF adres jest określany względem adresu podstawowego hosta punktu końcowego. Host może mieć jeden adres podstawowy dla każdego protokołu transportu komunikacji. W przykładowej konfiguracji w poprzednim pliku konfiguracji <xref:System.ServiceModel.BasicHttpBinding> wybrane do używany przez punkt końcowy HTTP jako protokołu transportowego, więc adres punktu końcowego, `EchoService`, jest określana względem podstawowy adres HTTP hosta. W przypadku hostów w poprzednim przykładzie, jest podstawowy adres HTTP `http://www.contoso.com:8000/`. W przypadku usługi hostowane w usługach IIS i WAS adres podstawowy jest adres URL usługi Usługa pliku.

Tylko usługi hostowane w usługach IIS i WAS i które są konfigurowane za pośrednictwem protokołu HTTP jako protokołu transportowego wyłącznie, będzie możliwe użycie opcji Tryb zgodności WCF ASP.NET. Włączenie tej opcji wymaga wykonania następujących czynności.

1. Należy dodać programistę <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atrybutu typu usługi i określ, czy tryb zgodności ASP.NET jest dozwolona lub wymagana.

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. Administrator musi skonfigurować aplikację do korzystania z trybu zgodności programu ASP.NET.

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

    Aplikacje usług WCF można skonfigurować w taki sposób, na potrzeby .asmx jako rozszerzenie swoich plików usługi zamiast .svc.

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

    Tej opcji można zapisać się z konieczności modyfikowania klientów, które są skonfigurowane do używania adresów URL plików usługi .asmx podczas modyfikowania usługi do użycia usług WCF.

## <a name="client-development"></a>Tworzenie aplikacji klienckich

Klienci usługi sieci Web platformy ASP.NET są generowane przy użyciu narzędzia wiersza polecenia WSDL.exe, który zawiera adres URL pliku .asmx jako dane wejściowe. Odpowiedniego narzędzia, które są dostarczane przez architekturę WCF jest [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Generuje moduł kodu o definicję kontraktu usługi, jak i definicja klasy klienta programu WCF. Generuje plik konfiguracji przy użyciu adresu i powiązania usługi.

W kliencie usługi zdalnej programowania jest na ogół program zgodnie z wzorca asynchronicznego. Kod wygenerowany przez narzędzie WSDL.exe zawsze zawiera zarówno przez synchroniczny i asynchroniczny wzorzec domyślnie. Kod wygenerowany przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może spowodować uzyskanie albo wzorzec. Oferuje ona synchroniczne wzorzec domyślnie. Jeśli narzędzie jest wykonywane przy użyciu `/async` przełączyć, a następnie wygenerowany kod przewiduje wzorca asynchronicznego.

Nie ma żadnej gwarancji, że nazwy w klasach klienta WCF, które są generowane przez program ASP. Narzędzie WSDL.exe firmy NET, domyślnie zgodne z nazwami w generowanych przez narzędzia Svcutil.exe klasy klienta programu WCF. W szczególności, nazwy właściwości klas, trzeba być Zserializowany za pomocą <xref:System.Xml.Serialization.XmlSerializer> domyślnie otrzymują sufiks właściwość, która znajduje się w kod wygenerowany przez narzędzie Svcutil.exe, które nie jest to za pomocą narzędzia WSDL.exe.

## <a name="message-representation"></a>Reprezentacja komunikatu

Można dostosować nagłówków protokołu SOAP komunikatów wysyłanych i odbieranych przez usługi sieci Web platformy ASP.NET. Klasa jest pochodną <xref:System.Web.Services.Protocols.SoapHeader> do definiowania struktury nagłówka, a następnie <xref:System.Web.Services.Protocols.SoapHeaderAttribute> służy do wskazywania obecność nagłówka.

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

WCF zawiera atrybuty, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, i <xref:System.ServiceModel.MessageBodyMemberAttribute> do opisania struktury komunikaty protokołu SOAP wysłanych i odebranych przez usługę.

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

Ta składnia daje reprezentację w postaci jawnej struktury wiadomości, natomiast struktury wiadomości jest implikowany przez kod z usługi sieci Web platformy ASP.NET. Ponadto w składni ASP.NET nagłówków wiadomości są reprezentowane jako właściwości usługi, takie jak `ProtocolHeader` właściwości w poprzednim przykładzie, w składni WCF są bardziej precyzyjne reprezentowana jako właściwości wiadomości. Ponadto WCF umożliwia nagłówków wiadomości, które mają zostać dodane do konfiguracji punktów końcowych.

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

Czy opcja umożliwia uniknięcie każde odwołanie do nagłówków protokołu infrastrukturalnych w kodzie klienta lub usługi: nagłówki są dodawane do komunikatów z powodu konfiguracji punktu końcowego.

## <a name="service-description"></a>Opis usługi

Wystawianie żądanie HTTP GET dla plików .asmx usługi sieci Web platformy ASP.NET z zapytaniem WSDL powoduje, że ASP.NET wygeneruje WSDL usługi. Zwraca wartość, która WSDL jako odpowiedź na żądanie.

ASP.NET 2.0 możliwe sprawdzenie, czy usługa jest zgodne z Basic Profile 1.1 organizacji współdziałania usług sieci Web (WS-I) oraz do wstawienia oświadczenia, że usługa jest zgodne w jego WSDL. Oznacza to gotowe przy użyciu `ConformsTo` i `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atrybutu.

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

Można dostosować języka WSDL, który ASP.NET generuje dla usługi. Dostosowania zostały wprowadzone, tworząc klasę pochodną z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> do dodawania elementów do pliku WSDL.

Wydania żądania HTTP GET z zapytaniem WSDL pliku .svc usługi WCF z punktu końcowego HTTP, hostowane w usługach IIS 51, 6.0 lub WAS powoduje, że usługi WCF na odpowiedź z WSDL usługi. Wystawianie żądanie HTTP GET z zapytaniem WSDL podstawowy adres HTTP usług hostowanych na platformie aplikacji platformy .NET ma taki sam skutek, jeśli httpGetEnabled jest ustawiona na wartość true.

Jednak WCF także odpowiada na żądania usługi WS-MetadataExchange za pomocą języka WSDL, który generuje do opisu usługi. Usług sieci Web programu ASP.NET nie ma wbudowaną obsługę protokołu WS-MetadataExchange żądań.

Często można dostosować języka WSDL, który generuje WCF. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Klasa udostępnia niektóre funkcje służące do dostosowywania pliku WSDL. WCF można również skonfigurować nie generowania języka WSDL, lecz raczej przy użyciu statycznych pliku WSDL pod danym adresem URL.

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

W usługach sieci Web platformy ASP.NET nieobsłużone wyjątki są zwracane do klientów jako błędach SOAP. Można także jawnie generować wystąpień <xref:System.Web.Services.Protocols.SoapException> klasy i mieć większą kontrolę nad zawartością błąd protokołu SOAP, która pobiera przesłana do klienta.

W usługach WCF nieobsługiwanych wyjątków nie są zwracane do klientów jako błędach SOAP, aby zapobiec przypadkowo są udostępniane za pośrednictwem wyjątki informacji poufnych. Ustawienie konfiguracji znajduje się na ma nieobsługiwane wyjątki zwracane do klientów na potrzeby debugowania.

Aby przywrócić błędach SOAP dla klientów, może zgłosić wystąpień typu ogólnego <xref:System.ServiceModel.FaultException%601>za pomocą ogólnego typu kontraktu danych. Można również dodać <xref:System.ServiceModel.FaultContractAttribute> atrybuty do obsługi operacji do określenia błędy, które może prowadzić operacji.

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

Robi skutkuje możliwych błędów anonsowane w języku WSDL usługi, umożliwiając klienckim ekspertów w programowaniu w celu przewidywania usterek, które można wynika z operacji i zapisu czy odpowiednie catch, instrukcje.

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

## <a name="state-management"></a>Zarządzanie stanem

Klasa używany do implementowania usługi sieci Web ASP.NET może pochodzić od <xref:System.Web.Services.WebService>.

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

W takim przypadku klasa może być zaprogramowane w taki sposób, aby użyć <xref:System.Web.Services.WebService> podstawowej klasy właściwości kontekstu, aby uzyskać dostęp do <xref:System.Web.HttpContext> obiektu. <xref:System.Web.HttpContext> Obiekt może być używany do aktualizowania i pobierania informacji o stanie aplikacji za pomocą jego właściwości aplikacji i może służyć do aktualizowania i pobierania informacji o stanie sesji przy użyciu jego właściwość sesji.

Platforma ASP.NET zapewnia znaczną kontrolę nad którym sesja stanu informacje dostępne przy użyciu właściwości sesji <xref:System.Web.HttpContext> rzeczywiście jest przechowywana. Mogą być przechowywane, w plikach cookie, w bazie danych, w pamięci bieżącego serwera lub w pamięci wyznaczonym serwerze. Wybór zostanie przeprowadzona w pliku konfiguracji usługi.

WCF zawiera obiekty Rozszerzalne zarządzanie stanem. Obiekty rozszerzalne to obiekty, które implementują <xref:System.ServiceModel.IExtensibleObject%601>. Są najważniejsze obiekty rozszerzalne <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.InstanceContext>. `ServiceHostBase` pozwala zachować dostęp do stanu, że typy wszystkich wystąpień wszystkie usługi na tym samym hoście, podczas gdy `InstanceContext` pozwala zachować stan, który może zostać oceniony przez każdy kod uruchomiony w ramach tego samego wystąpienia typu usługi.

Tutaj, typ usługi `TradingSystem`, ma <xref:System.ServiceModel.ServiceBehaviorAttribute> określający, że wszystkie wywołania z tego samego wystąpienia klienta WCF, są kierowane do tego samego wystąpienia typu usługi.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

Klasa `DealData`, definiuje stan, który może zostać oceniony przez każdy kod uruchomiony w tym samym wystąpieniu typu usługi.

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

W kodzie typ usługi, który implementuje jednej z operacji kontraktu usługi `DealData` stan obiektu jest dodawany do stanu bieżącego wystąpienia typu usługi.

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

Ten obiekt stanu następnie można je pobrać i zmodyfikowane przez kod, który implementuje innej operacji kontraktu usługi.

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

Program ASP.NET zapewnia kontrolę nad, gdzie stan informacje zawarte w <xref:System.Web.HttpContext> klasy rzeczywiście jest przechowywana, WCF, co najmniej w wersji początkowej zapewnia kontrolę przechowywania obiekty rozszerzalne. Który stanowi najlepsze Przyczyna wybierając tryb zgodności ASP.NET dla usługi WCF. Jeśli jest rozwiązaniem do zarządzania stanem można skonfigurować, a następnie włączenie trybu zgodności programu ASP.NET pozwala na używanie funkcji <xref:System.Web.HttpContext> klasy dokładnie tak, jak są one używane w programie ASP.NET, a także skonfigurować gdzie informacje stanie zarządzany przy użyciu <xref:System.Web.HttpContext> klasy są przechowywane.

## <a name="security"></a>Zabezpieczenia

Opcje dotyczące zabezpieczania usług sieci Web platformy ASP.NET są do zabezpieczania dowolnej aplikacji usług IIS. Ponieważ może być hostowana aplikacji WCF, nie tylko w ramach usług IIS, ale także w dowolnych plików wykonywalnych platformy .NET, opcje zabezpieczania aplikacji WCF muszą być wykonane niezależna od funkcji programu IIS. Jednak urządzenia podane dla usług sieci Web platformy ASP.NET są również dostępne dla usługi WCF, uruchomiony w trybie zgodności w programie ASP.NET.

### <a name="security-authentication"></a>Zabezpieczenia: Uwierzytelnianie

IIS oferuje funkcje służące do kontrolowania dostępu do aplikacji za pomocą których można wybrać dostęp anonimowy lub różne tryby uwierzytelniania: Uwierzytelnianie Windows, uwierzytelniania szyfrowanego, uwierzytelnianie podstawowe i uwierzytelnianie na platformie .NET usługi Passport. Opcja uwierzytelniania Windows może służyć do kontrolowania dostępu do usług sieci Web platformy ASP.NET. Jednak podczas aplikacji WCF hostowanych w ramach usług IIS, usługi IIS muszą być skonfigurowane, aby zezwolić na anonimowy dostęp do aplikacji, aby można było zarządzać uwierzytelniania przez architekturę WCF, która obsługuje uwierzytelnianie Windows między różnymi inne opcje. Inne opcje, które są wbudowane obejmują username tokeny, certyfikaty X.509, tokeny SAML i CardSpace karty, ale można także definiować niestandardowych mechanizmów uwierzytelniania.

### <a name="security-impersonation"></a>Zabezpieczenia: Personifikacja

Program ASP.NET zapewnia elementu tożsamości przez usługi sieci Web platformy ASP.NET można wprowadzić personifikować określonego użytkownika lub niezależnie od użytkownika poświadczeń są dostarczane z bieżącego żądania. Ten element może służyć do konfigurowania personifikacji aplikacji WCF uruchomionych w trybie zgodności platformy ASP.NET.

System konfiguracji usługi WCF zawiera element tożsamości wyznaczania dać określonemu użytkownikowi personifikacji. Ponadto klienci WCF i usługi można niezależnie skonfigurować personifikacji. Klientów można skonfigurować w taki sposób, aby Personifikuj bieżącego użytkownika, gdy są przez nie przesyłane żądania.

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

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a>Zabezpieczenia: Autoryzacja przy użyciu list kontroli dostępu

List kontroli dostępu (ACL) może służyć do ograniczania dostępu do plików .asmx. Jednak list kontroli dostępu do plików .svc WCF są ignorowane z wyjątkiem w trybie zgodności w programie ASP.NET.

### <a name="security-role-based-authorization"></a>Zabezpieczenia: Autoryzacja oparta na rolach

Opcja uwierzytelniania Windows usług IIS może służyć w połączeniu z elementem autoryzacji dostarczonych przez język konfiguracji platformy ASP.NET do ułatwienia autoryzacji opartej na rolach dla usług sieci Web platformy ASP.NET opartych na grupach Windows, do których użytkownicy są przypisani . Program ASP.NET 2.0 wprowadzono bardziej ogólnych mechanizmu autoryzacji opartej na rolach: dostawców ról.

Dostawców ról są klasami, które implementują podstawowy interfejs dla badające o rolach, do których użytkownik jest przypisany, że każdy dostawca ról wie, jak pobrać te informacje z innego źródła. Program ASP.NET 2.0 zawiera rolę dostawcę, który można pobrać przypisań ról z bazy danych programu Microsoft SQL Server i drugą do pobrania przypisań ról z Menedżer autoryzacji systemu Windows Server 2003.

Mechanizm dostawcy roli faktycznie można niezależnie od platformy ASP.NET w dowolnej aplikacji platformy .NET, w tym aplikacji WCF. Następujące Przykładowa konfiguracja dla aplikacji WCF pokazuje, jak używanie dostawcy ról ASP.NET jest opcja wybrana przez <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.

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

### <a name="security-claims-based-authorization"></a>Zabezpieczenia: Autoryzacja oparta na oświadczeniach

Jedną z najważniejszych innowacyjnych możliwościach programu WCF jest dokładne Obsługa Autoryzowanie dostępu do chronionych zasobów na podstawie oświadczeń. Oświadczenia składają się z typem, prawa i wartości, sterowniki licencji, na przykład. To sprawia, że zestaw oświadczeń o elementu nośnego, z których jedna jest okaziciela datę urodzenia. Typ tego oświadczenia jest data urodzenia, gdy wartość oświadczenia jest data urodzenia sterownika. Po prawej stronie, która przyznaje oświadczenie okaziciela określa okaziciela czynności przy użyciu wartości oświadczenia. W przypadku oświadczeń sterownika Data urodzenia, po prawej stronie jest posiadanie: sterownik posiada, których data urodzenia ale nie może, na przykład, zmienienia go. Autoryzacja oparta na oświadczeniach otacza autoryzacji opartej na rolach, ponieważ typ oświadczenia są role.

Autoryzacja na podstawie oświadczeń odbywa się przez porównanie zestaw oświadczeń do wymagań dostępu do operacji i, w zależności od tego, w wyniku tego porównania, udzielanie lub odmawianie dostępu do operacji. W programie WCF, można określić klasa używana do uruchamiania autoryzacji opartej na oświadczeniach, ponownie przypisując wartość `ServiceAuthorizationManager` właściwość <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

Klasy używane do uruchamiania autoryzacji opartej na oświadczeniach muszą pochodzić od <xref:System.ServiceModel.ServiceAuthorizationManager>, który ma tylko jedną metodę, aby zastąpić, `AccessCheck()`. Usługi WCF wywołuje tę metodę, za każdym razem jest wywoływana operacji usługi i udostępnia <xref:System.ServiceModel.OperationContext> obiektu, który ma oświadczenia dla użytkownika w jego `ServiceSecurityContext.AuthorizationContext` właściwości. Usługi WCF wykonuje pracę złożenia oświadczenia dotyczące użytkownika z tokenem zabezpieczającym, niezależnie od użytkownika podany na potrzeby uwierzytelniania, co pozostawia zadania oceny, czy te oświadczenia są wystarczające dla danego działania.

Czy WCF automatycznie składa oświadczeń z dowolnego rodzaju zabezpieczenia tokenu jest bardzo istotne innowacji, ponieważ dzięki niej kod autoryzacji na podstawie oświadczeń, które są całkowicie niezależne mechanizmu uwierzytelniania. Z drugiej strony autoryzację przy użyciu list kontroli dostępu lub role w programie ASP.NET jest ściśle powiązany uwierzytelniania Windows.

### <a name="security-confidentiality"></a>Zabezpieczenia: Poufność

Poufność komunikatów wymienianych z usługami sieci Web platformy ASP.NET można zapewnić na poziomie transportu przez skonfigurowanie aplikacji w ramach usług IIS do korzystania z Secure Hypertext Transfer Protocol (HTTPS). Taki sam zarówno WCF hostowanych w ramach usług IIS. Jednak WCF hostowanych poza programem IIS, można również skonfigurować do używania protokołu bezpiecznym transportem. Co ważniejsze, aplikacji WCF można również skonfigurować do zabezpieczenia komunikatów przed ich transportu, przy użyciu protokołu WS-Security. Zabezpieczanie po prostu treść komunikatu przy użyciu usługi WS-Security umożliwia mu się jako poufne przesyłane przez rolę pośredników przed dotarciem do ostatecznego miejsca przeznaczenia.

## <a name="globalization"></a>Globalizacja

Język konfiguracji platformy ASP.NET można określić kulturę dla poszczególnych usług. WCF nie obsługuje tego ustawienia konfiguracji, z wyjątkiem w trybie zgodności w programie ASP.NET. Aby zlokalizować usługi WCF, która nie korzysta z trybu zgodności programu ASP.NET, skompilować typ usługi do zestawów specyficzne dla kultury i mają oddzielne specyficzne dla kultury punktów końcowych dla każdego zestawu specyficzne dla kultury.

## <a name="see-also"></a>Zobacz także

- [Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
