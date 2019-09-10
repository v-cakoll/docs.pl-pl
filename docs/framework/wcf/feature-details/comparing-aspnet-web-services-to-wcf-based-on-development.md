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
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a>Porównywanie usług sieci Web na platformie ASP.NET z programem WCF na podstawie procesów programistycznych

Windows Communication Foundation (WCF) ma opcję trybu zgodności ASP.NET, aby umożliwić aplikacjom WCF zaprogramowane i skonfigurowane, takie jak ASP.NET usługi sieci Web, i naśladowanie zachowania. W poniższych sekcjach porównano usługi sieci Web ASP.NET i WCF na podstawie tego, co jest wymagane do opracowania aplikacji przy użyciu obu technologii.

## <a name="data-representation"></a>Reprezentacja danych

Opracowywanie usługi sieci Web za pomocą ASP.NET zwykle zaczyna się od definiowania złożonych typów danych, których usługa ma używać. ASP.NET opiera się na usłudze <xref:System.Xml.Serialization.XmlSerializer> , aby przetłumaczyć dane reprezentowane przez .NET Framework typy na XML na potrzeby przesyłania danych do lub z usługi oraz do translacji danych odebranych jako XML do obiektów .NET Framework. Definiowanie złożonych typów danych, których usługa ASP.net ma używać, wymaga definicji klas .NET Framework, które <xref:System.Xml.Serialization.XmlSerializer> mogą serializować do i z XML. Takie klasy mogą być zapisywane ręcznie lub generowane na podstawie definicji typów w schemacie XML przy użyciu schematów XML wiersza polecenia/typów danych narzędzia, XSD. exe.

Poniżej przedstawiono listę najważniejszych zagadnień, które należy znać podczas definiowania klas .NET Framework, które <xref:System.Xml.Serialization.XmlSerializer> mogą serializować do i z XML:

- Tylko pola publiczne i właściwości obiektów .NET Framework są tłumaczone na XML.

- Wystąpienia klas kolekcji można serializować do kodu XML tylko wtedy, gdy klasy implementują <xref:System.Collections.IEnumerable> interfejs lub. <xref:System.Collections.ICollection>

- Klasy implementujące <xref:System.Collections.IDictionary> interfejs, takie jak <xref:System.Collections.Hashtable>, nie mogą być serializowane do kodu XML.

- Wiele typów atrybutów w <xref:System.Xml.Serialization> przestrzeni nazw można dodać do klasy .NET Framework i jej elementów członkowskich, aby kontrolować sposób, w jaki wystąpienia klasy są reprezentowane w kodzie XML.

Projektowanie aplikacji WCF zwykle zaczyna się także od definicji typów złożonych. W programie WCF można używać tych samych .NET Framework typów co ASP.NET Web Services.

Funkcję WCF<xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> można dodać do typów .NET Framework, aby wskazać, że wystąpienia typu mają być serializowane do kodu XML, a określone pola lub właściwości typu mają być serializowane, jak pokazano w poniższym przykładowym kodzie.

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

Oznacza <xref:System.Runtime.Serialization.DataContractAttribute> to, że co najmniej zero pól lub właściwości typu jest serializowany, <xref:System.Runtime.Serialization.DataMemberAttribute> podczas gdy wskazuje, że określone pole lub właściwość ma być serializowana. <xref:System.Runtime.Serialization.DataContractAttribute> Można zastosować do klasy lub struktury. <xref:System.Runtime.Serialization.DataMemberAttribute> Można zastosować do pola lub właściwości, a pola i właściwości, do których zastosowano atrybut, mogą być publiczne lub prywatne. Wystąpienia typów, które mają <xref:System.Runtime.Serialization.DataContractAttribute> zastosowane do nich, są określane jako Kontrakty danych w programie WCF. Są one serializowane do kodu <xref:System.Runtime.Serialization.DataContractSerializer>XML przy użyciu.

Poniżej znajduje się lista ważnych różnic między użyciem <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> i różnymi atrybutami <xref:System.Xml.Serialization> przestrzeni nazw.

- <xref:System.Xml.Serialization.XmlSerializer> I atrybuty<xref:System.Xml.Serialization> przestrzeni nazw zostały zaprojektowane tak, aby umożliwiały Mapowanie typów .NET Framework do dowolnego prawidłowego typu zdefiniowanego w schemacie XML i dlatego zapewniają bardzo precyzyjne sterowanie sposobem, w jaki typ jest reprezentowany w kodzie XML. <xref:System.Runtime.Serialization.DataContractSerializer> Izapewniająbardzoniewielkąkontrolęnadsposobemreprezentowania<xref:System.Runtime.Serialization.DataMemberAttribute> typu w kodzie XML. <xref:System.Runtime.Serialization.DataContractAttribute> Można określić tylko obszary nazw i nazwy używane do reprezentowania typu i jego pól lub właściwości w kodzie XML oraz sekwencję, w której pola i właściwości są wyświetlane w kodzie XML:

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

  Wszystkie inne informacje o strukturze kodu XML użytego do reprezentowania typu .NET są określane przez <xref:System.Runtime.Serialization.DataContractSerializer>.

- Przez nieumożliwienie kontroli nad sposobem reprezentowania typu w kodzie XML, proces serializacji jest wysoce przewidywalny dla <xref:System.Runtime.Serialization.DataContractSerializer>, i, w tym celu, łatwiej zoptymalizować. Praktyczną zaletą projektowania <xref:System.Runtime.Serialization.DataContractSerializer> jest lepsza wydajność, około dziesięciu procent lepszej wydajności.

- Atrybuty do użycia z <xref:System.Xml.Serialization.XmlSerializer> nie wskazują, które pola lub właściwości typu są serializowane do kodu XML, <xref:System.Runtime.Serialization.DataMemberAttribute> natomiast do użycia z <xref:System.Runtime.Serialization.DataContractSerializer> pokazuje jawnie, które pola lub właściwości są serializowane. W związku z tym Kontrakty danych są jawnymi umowami dotyczącymi struktury danych wysyłanych i odbieranych przez aplikację.

- Może przetłumaczyć tylko publiczne elementy członkowskie obiektu platformy .NET na XML <xref:System.Runtime.Serialization.DataContractSerializer> , może przetłumaczyć elementy członkowskie obiektów na XML, niezależnie od modyfikatorów dostępu tych elementów członkowskich. <xref:System.Xml.Serialization.XmlSerializer>

- W związku z tym <xref:System.Runtime.Serialization.DataContractSerializer> , że można serializować niepubliczne składowe typów do XML, ma mniejszą liczbę ograniczeń dla różnych typów .NET, które mogą serializować w kodzie XML. W szczególności można przetłumaczyć na typy XML, <xref:System.Collections.Hashtable> takie jak <xref:System.Collections.IDictionary> implementujący interfejs. <xref:System.Runtime.Serialization.DataContractSerializer> Jest to znacznie bardziej możliwe, aby można było serializować wystąpienia dowolnego istniejącego typu .NET do XML bez konieczności modyfikowania definicji typu lub tworzenia otoki dla niej.

- Kolejną konsekwencją <xref:System.Runtime.Serialization.DataContractSerializer> uzyskiwania dostępu do niepublicznych składowych typu jest to, że wymaga pełnego zaufania, a w <xref:System.Xml.Serialization.XmlSerializer> przeciwnym razie nie. Uprawnienie dostępu do kodu pełnego zaufania zapewnia pełny dostęp do wszystkich zasobów na komputerze, do którego można uzyskać dostęp przy użyciu poświadczeń, w których wykonywany jest kod. Tej opcji należy używać w przypadku, gdy w pełni zaufany kod uzyskuje dostęp do wszystkich zasobów na komputerze.

- <xref:System.Runtime.Serialization.DataContractSerializer> Firma obejmuje niektóre wsparcie dla wersji:

  - <xref:System.Runtime.Serialization.DataMemberAttribute> Mawłaściwość,którejmożnaprzypisaćwartośćfalsedlaelementówczłonkowskich,któresądodawanedonowychwersjikontraktudanych,któreniebyłyobecnewewcześniejszychwersjach,atymsamymZezwalanienaaplikacjez<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> nowszą wersją kontraktu możliwość przetworzenia wcześniejszych wersji.

  - Jeśli kontrakt danych implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejs, jeden z nich może <xref:System.Runtime.Serialization.DataContractSerializer> umożliwić przekazanie elementów członkowskich zdefiniowanych w nowszych wersjach kontraktu danych za pomocą aplikacji ze starszymi wersjami kontraktu.

Pomimo wszystkich różnic, kod XML, do którego <xref:System.Xml.Serialization.XmlSerializer> domyślnie serializowane serializacji typu jest semantycznie identyczny z XML, do <xref:System.Runtime.Serialization.DataContractSerializer> którego jest serializowany typ, pod warunkiem, że przestrzeń nazw XML jest jawnie zdefiniowana. Poniższa klasa, która ma atrybuty do użycia z obu serializatorów, jest przetłumaczona na semantycznie identyczne XML przez <xref:System.Xml.Serialization.XmlSerializer>: <xref:System.Runtime.Serialization.DataContractAttribute>

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

Zestaw Windows Software Development Kit (SDK) zawiera narzędzie wiersza polecenia o nazwie Narzędzie do [przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Podobnie jak narzędzie XSD. exe używane z usługami sieci Web ASP.NET, Svcutil. exe może generować definicje typów danych .NET ze schematu XML. Typy są kontraktami danych, jeśli <xref:System.Runtime.Serialization.DataContractSerializer> mogą emitować kod XML w formacie zdefiniowanym przez schemat XML; w przeciwnym razie są one przeznaczone do serializacji <xref:System.Xml.Serialization.XmlSerializer>przy użyciu. Svcutil. exe może również generować schemat XML z kontraktów danych przy użyciu jego `dataContractOnly` przełącznika.

> [!NOTE]
> Mimo że usługi sieci Web ASP.NET <xref:System.Xml.Serialization.XmlSerializer>korzystają z programu, a tryb zgodności WCF ASP.NET sprawia, że usługi WCF zaśladią zachowanie usług sieci Web ASP.NET, opcja zgodności ASP.NET nie ogranicza <xref:System.Xml.Serialization.XmlSerializer>do użycia. Może nadal korzystać <xref:System.Runtime.Serialization.DataContractSerializer> z usług z usługami uruchomionymi w trybie zgodności ASP.NET.

## <a name="service-development"></a>Opracowywanie usług

Aby opracować usługę przy użyciu ASP.NET, jest ona niestandardowa, aby dodać <xref:System.Web.Services.WebService> atrybut do klasy, <xref:System.Web.Services.WebMethodAttribute> oraz do dowolnej metody klasy, które mają być operacją usługi:

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

W ASP.NET 2,0 wprowadzono opcję dodania atrybutu <xref:System.Web.Services.WebService> i <xref:System.Web.Services.WebMethodAttribute> do interfejsu, a nie do klasy, i zapisanie klasy w celu zaimplementowania interfejsu:

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

Użycie tej opcji jest preferowane, ponieważ interfejs z <xref:System.Web.Services.WebService> atrybutem stanowi kontrakt dla operacji wykonywanych przez usługę, które mogą być ponownie używane z różnymi klasami, które mogą implementować ten sam kontrakt na różne sposoby.

Usługa WCF jest świadczona przez zdefiniowanie jednego lub większej liczby punktów końcowych WCF. Punkt końcowy jest definiowany przy użyciu adresu, powiązania i kontraktu usługi. Adres definiuje lokalizację usługi. Powiązanie określa sposób komunikacji z usługą. Kontrakt usługi definiuje operacje, które mogą być wykonywane przez usługę.

Kontrakt usługi jest zwykle definiowany jako pierwszy, przez dodanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> do interfejsu:

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

Określa, że interfejs definiuje kontrakt usługi WCF <xref:System.ServiceModel.OperationContractAttribute> i wskazuje, które z metod interfejsu definiują operacje kontraktu usługi. <xref:System.ServiceModel.ServiceContractAttribute>

Po zdefiniowaniu kontraktu usługi jest on implementowany w klasie, przez posiadanie klasy implementującej interfejs, w którym jest zdefiniowany kontrakt usługi:

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

Klasa implementująca kontrakt usługi jest określana jako typ usługi w programie WCF.

Następnym krokiem jest skojarzenie adresu i powiązania z typem usługi. Zwykle jest to wykonywane w pliku konfiguracji, edytując plik bezpośrednio lub korzystając z edytora konfiguracji dostarczonego z WCF. Oto przykład pliku konfiguracji.

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

Powiązanie określa zestaw protokołów do komunikacji z aplikacją. Poniższa tabela zawiera listę powiązań dostarczonych przez system, które reprezentują typowe opcje.

|Nazwa|Cel|
|----------|-------------|
|BasicHttpBinding|Współdziałanie z usługami sieci Web i klientami obsługującymi protokół WS-BasicProfile 1,1 i podstawowy profil zabezpieczeń 1,0.|
|WSHttpBinding|Współdziałanie z usługami sieci Web i klientami, które obsługują protokoły WS-* za pośrednictwem protokołu HTTP.|
|WSDualHttpBinding|Bezstronna komunikacja HTTP, przez którą odbiorca wiadomości początkowej nie odpowiada bezpośrednio nadawcy inicjującemu, ale może przesłać dowolną liczbę odpowiedzi w danym okresie, używając protokołu HTTP zgodnego z protokołami WS-*.|
|WSFederationBinding|Komunikacja HTTP, w której dostęp do zasobów usługi może być kontrolowany na podstawie poświadczeń wystawionych przez jawnie określonego dostawcę poświadczeń.|
|NetTcpBinding|Bezpieczna, niezawodna i wysoce wydajna komunikacja między jednostkami oprogramowania WCF w sieci.|
|NetNamedPipeBinding|Bezpieczna, niezawodna i wysoce wydajna komunikacja między jednostkami oprogramowania WCF na tym samym komputerze.|
|NetMsmqBinding|Komunikacja między jednostkami oprogramowania WCF przy użyciu usługi MSMQ.|
|MsmqIntegrationBinding|Komunikacja między jednostką oprogramowania WCF i inną jednostką oprogramowania przy użyciu usługi MSMQ.|
|NetPeerTcpBinding|Komunikacja między jednostkami oprogramowania WCF przy użyciu sieci równorzędnej systemu Windows.|

Powiązanie <xref:System.ServiceModel.BasicHttpBinding>dostarczone z systemem, zawiera zestaw protokołów obsługiwanych przez usługi sieci Web ASP.NET.

Niestandardowe powiązania dla aplikacji WCF są łatwo zdefiniowane jako kolekcje klas elementów powiązania używanych przez program WCF do implementowania poszczególnych protokołów. Nowe elementy powiązania można napisać, aby reprezentować dodatkowe protokoły.

Wewnętrzne zachowanie typów usług można dostosować przy użyciu właściwości rodziny klas o nazwie Behaviors. W tym miejscu Klasa jest używana do określenia, czy typ usługi ma być wielowątkowy. <xref:System.ServiceModel.ServiceBehaviorAttribute>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

Niektóre zachowania, takie <xref:System.ServiceModel.ServiceBehaviorAttribute>jak, są atrybutami. Inne osoby, które mają właściwości, które Administratorzy chcą ustawić, mogą być modyfikowane w konfiguracji aplikacji.

W przypadku typów usług programistycznych należy wykonać <xref:System.ServiceModel.OperationContext> częste użycie klasy. Jej właściwość <xref:System.ServiceModel.OperationContext.Current%2A> statyczna zapewnia dostęp do informacji dotyczących kontekstu, w którym jest uruchomiona operacja. <xref:System.ServiceModel.OperationContext>jest podobna do <xref:System.Web.HttpContext> klas i <xref:System.EnterpriseServices.ContextUtil> .

## <a name="hosting"></a>Hosting

Usługi sieci Web ASP.NET są kompilowane do zestawu biblioteki klas. Plik o nazwie plik usługi jest dostarczany z rozszerzeniem ASMX i zawiera `@ WebService` dyrektywę identyfikującą klasę, która zawiera kod dla usługi i zestaw, w którym znajduje się.

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

Plik usługi jest kopiowany do katalogu głównego aplikacji ASP.NET w programie Internet Information Services (IIS), a zestaw jest kopiowany do podkatalogu \Bin tego katalogu głównego aplikacji. Aplikacja jest następnie dostępna przy użyciu adresu URL (Uniform Resource Locator) pliku usługi w katalogu głównym aplikacji.

Usługi WCF mogą być łatwo hostowane w usługach IIS 5,1 lub 6,0, w ramach usługi aktywacji procesów systemu Windows (WAS), która jest dostępna jako część usług IIS 7,0 i w ramach dowolnej aplikacji .NET. Aby hostować usługę w usługach IIS 5,1 lub 6,0, usługa musi używać protokołu HTTP jako protokołu transportowego komunikacji.

Aby hostować usługę w usługach IIS 5,1, 6,0 lub w ramach programu, wykonaj następujące czynności:

1. Kompiluj typ usługi do zestawu biblioteki klas.

2. Utwórz plik usługi z rozszerzeniem SVC z `@ ServiceHost` dyrektywą w celu zidentyfikowania typu usługi:

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. Skopiuj plik usługi do katalogu wirtualnego, a następnie zestaw do podkatalogu \Bin tego katalogu wirtualnego.

4. Skopiuj plik konfiguracji do katalogu wirtualnego, a następnie nadaj mu nazwę Web. config.

Następnie aplikacja jest dostępna przy użyciu adresu URL pliku usługi w katalogu głównym aplikacji.

Aby hostować usługę WCF w ramach aplikacji .NET, skompiluj typ usługi do zestawu biblioteki klas, do którego odwołuje się aplikacja, i zaprogramowanie aplikacji do hostowania usługi <xref:System.ServiceModel.ServiceHost> przy użyciu klasy. Poniżej znajduje się przykład wymaganego programowania podstawowego:

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

Ten przykład pokazuje, jak adresy dla co najmniej jednego protokołu transportowego są określone w konstrukcji <xref:System.ServiceModel.ServiceHost>a. Te adresy są określane jako adresy podstawowe.

Adres podany dla dowolnego punktu końcowego usługi WCF jest adresem względem adresu podstawowego hosta punktu końcowego. Host może mieć jeden adres podstawowy dla każdego protokołu transportu komunikacji. W przykładowej konfiguracji w poprzednim pliku <xref:System.ServiceModel.BasicHttpBinding> konfiguracyjnym wybrane dla punktu końcowego używa protokołu HTTP jako protokołu transportowego, więc adres `EchoService`punktu końcowego jest określany względem adresu podstawowego http hosta. W przypadku hosta w poprzednim przykładzie adres podstawowy HTTP to `http://www.contoso.com:8000/`. W przypadku usługi hostowanej w ramach usług IIS lub jako adres podstawowy to adres URL pliku usługi usługi.

Tylko usługi hostowane w usługach IIS lub były skonfigurowane z użyciem protokołu HTTP jako protokołu transportowego, można użyć opcji Tryb zgodności programu WCF ASP.NET. Włączenie tej opcji wymaga wykonania następujących czynności.

1. Programista musi dodać <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atrybut do typu usługi i określić, że tryb zgodności ASP.NET jest dozwolony lub wymagany.

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. Administrator musi skonfigurować aplikację tak, aby korzystała z trybu zgodności ASP.NET.

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

    Aplikacje WCF można także skonfigurować do używania. asmx jako rozszerzenia dla plików usługi, a nie SVC.

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

    Ta opcja umożliwia modyfikację klientów skonfigurowanych do korzystania z adresów URL plików usługi asmx podczas modyfikowania usługi do korzystania z programu WCF.

## <a name="client-development"></a>Tworzenie aplikacji klienckich

Klienci dla usług sieci Web ASP.NET są generowane przy użyciu narzędzia wiersza polecenia, WSDL. exe, który udostępnia adres URL pliku. asmx jako dane wejściowe. Odpowiednie narzędzie dostarczone przez funkcję WCF to [Narzędzie do przesyłania metadanych programu ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Generuje moduł kodu z definicją kontraktu usługi i definicją klasy klienta WCF. Generuje również plik konfiguracji z adresem i powiązaniem usługi.

W programowaniu klienta usługi zdalnej ogólnie zaleca się, aby program był zgodny ze wzorcem asynchronicznym. Kod wygenerowany przez narzędzie WSDL. exe zawsze zapewnia domyślnie zarówno wzorzec synchroniczny, jak i asynchroniczny. Kod wygenerowany przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może zapewnić dla obu wzorców. Domyślnie oferuje wzorzec synchroniczny. Jeśli narzędzie jest wykonywane z `/async` przełącznikiem, wygenerowany kod zapewnia wzorzec asynchroniczny.

Nie ma gwarancji, że nazwy w klasach klienta WCF generowane przez ASP. Narzędzie NET. exe języka WSDL domyślnie dopasowuje nazwy w klasach klienta WCF generowanych przez narzędzie Svcutil. exe. W szczególności nazwy właściwości klas, które mają być serializowane przy użyciu <xref:System.Xml.Serialization.XmlSerializer> , domyślnie mają właściwość sufiks w kodzie wygenerowanym przez narzędzie Svcutil. exe, które nie jest przypadkiem narzędzia WSDL. exe.

## <a name="message-representation"></a>Reprezentacja komunikatów

Nagłówki komunikatów protokołu SOAP wysyłane i odbierane przez usługi sieci Web ASP.NET można dostosować. Klasa pochodzi od <xref:System.Web.Services.Protocols.SoapHeader> , aby zdefiniować strukturę nagłówka, a <xref:System.Web.Services.Protocols.SoapHeaderAttribute> następnie służy do wskazywania obecności nagłówka.

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

WCF udostępnia atrybuty, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute>, i <xref:System.ServiceModel.MessageBodyMemberAttribute> opisują strukturę komunikatów protokołu SOAP wysyłanych i odbieranych przez usługę.

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

Ta składnia daje jawną reprezentację struktury komunikatów, podczas gdy struktura komunikatów jest implikowana przez kod usługi sieci Web ASP.NET. Ponadto w składni ASP.NET nagłówki wiadomości są reprezentowane jako właściwości usługi, takie jak `ProtocolHeader` właściwość w poprzednim przykładzie, natomiast w składni programu WCF są one bardziej dokładnie reprezentowane jako właściwości komunikatów. Ponadto WCF zezwala na Dodawanie nagłówków wiadomości do konfiguracji punktów końcowych.

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

Ta opcja pozwala uniknąć dowolnych odwołań do nagłówków protokołu infrastruktury w kodzie dla klienta lub usługi: nagłówki są dodawane do komunikatów ze względu na sposób konfiguracji punktu końcowego.

## <a name="service-description"></a>Opis usługi

Wydawanie żądania HTTP GET dla pliku. asmx usługi sieci Web ASP.NET za pomocą języka WSDL zapytania powoduje, że ASP.NET do wygenerowania kodu WSDL w celu opisania usługi. Zwraca ten plik WSDL jako odpowiedź do żądania.

ASP.NET 2,0 może sprawdzić, czy usługa jest zgodna z profilem Basic 1,1 w organizacji usługi sieci Web — współdziałanie (WS-I), a następnie wstawić do niej zastrzeżenie, że usługa jest zgodna ze specyfikacją WSDL. Jest to wykonywane przy użyciu `ConformsTo` parametrów `EmitConformanceClaims` <xref:System.Web.Services.WebServiceBindingAttribute> i atrybutu.

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

WSDL, który ASP.NET generuje dla usługi, można dostosować. Dostosowania są wykonywane przez utworzenie klasy <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pochodnej, aby dodać elementy do WSDL.

Wydawanie żądania HTTP GET za pomocą języka WSDL zapytania dla pliku SVC usługi WCF za pomocą punktu końcowego HTTP hostowanego w usługach IIS 51, 6,0 lub zostało spowodowane przez program WCF w celu opisywania usługi. Wygenerowanie żądania HTTP GET przy użyciu zapytania WSDL dla adresu podstawowego HTTP usługi hostowanej w aplikacji .NET ma ten sam efekt, jeśli httpGetEnabled jest ustawiona na wartość true.

Jednak funkcja WCF reaguje na żądania WS-MetadataExchange za pomocą języka WSDL, który generuje do opisywania usługi. Usługi sieci Web ASP.NET nie mają wbudowanej obsługi żądań WS-MetadataExchange.

Język WSDL generowany przez funkcję WCF może być szeroko dostosowany. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Klasa zawiera niektóre obiekty do dostosowania WSDL. Program WCF można również skonfigurować tak, aby nie generował WSDL, ale zamiast tego użyć statycznego pliku WSDL pod podanym adresem URL.

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

W usługach sieci Web ASP.NET Nieobsłużone wyjątki są zwracane do klientów jako błędy SOAP. Można również jawnie zgłosić wystąpienia <xref:System.Web.Services.Protocols.SoapException> klasy i mieć większą kontrolę nad zawartością błędu protokołu SOAP, który jest przesyłany do klienta.

W usługach WCF Nieobsłużone wyjątki nie są zwracane klientom jako błędy protokołu SOAP, aby zapobiec przypadkowemu ujawnieniu poufnych informacji przez wyjątki. Ustawienie konfiguracji zapewnia Nieobsłużone wyjątki zwracane klientom na potrzeby debugowania.

Aby zwrócić do klientów błędy SOAP, można zgłosić wystąpienia typu ogólnego, <xref:System.ServiceModel.FaultException%601>przy użyciu typu kontraktu danych jako typu ogólnego. Możesz również dodać <xref:System.ServiceModel.FaultContractAttribute> atrybuty do operacji, aby określić błędy, które może przynieść operacja.

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

Powoduje to, że potencjalne błędy są anonsowane w języku WSDL dla usługi, dzięki czemu programiści mogą przewidzieć, które błędy może wynikać z operacji, i napisać odpowiednie instrukcje catch.

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

Klasa użyta do zaimplementowania usługi sieci Web ASP.NET może być <xref:System.Web.Services.WebService>pochodną.

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

W takim przypadku Klasa może być zaprogramowany, aby użyć <xref:System.Web.Services.WebService> właściwości kontekstu klasy podstawowej w celu <xref:System.Web.HttpContext> uzyskania dostępu do obiektu. <xref:System.Web.HttpContext> Obiekt może służyć do aktualizowania i pobierania informacji o stanie aplikacji przy użyciu właściwości aplikacji i może służyć do aktualizowania i pobierania informacji o stanie sesji przy użyciu właściwości sesji.

ASP.NET zapewnia znaczącą kontrolę nad tym, gdzie informacje o stanie sesji, do których uzyskuje <xref:System.Web.HttpContext> się dostęp przy użyciu właściwości Session w rzeczywistości, są przechowywane. Mogą być przechowywane w plikach cookie, w bazie danych, w pamięci bieżącego serwera lub w pamięci określonego serwera. Wybór jest dokonywany w pliku konfiguracji usługi.

Funkcja WCF zapewnia Rozszerzalne obiekty do zarządzania stanem. Rozszerzalne obiekty to obiekty, <xref:System.ServiceModel.IExtensibleObject%601>które implementują. Najważniejsze Rozszerzalne obiekty to <xref:System.ServiceModel.ServiceHostBase> i. <xref:System.ServiceModel.InstanceContext> `ServiceHostBase`pozwala zachować stan, w którym wszystkie wystąpienia wszystkich typów usług na tym samym hoście mogą uzyskać dostęp, a jednocześnie `InstanceContext` pozwala zachować stan, do którego można uzyskać dostęp za pomocą dowolnego kodu uruchomionego w ramach tego samego wystąpienia typu usługi.

W tym miejscu typ usługi, `TradingSystem`,,, <xref:System.ServiceModel.ServiceBehaviorAttribute> określa, że wszystkie wywołania z tego samego wystąpienia klienta programu WCF są kierowane do tego samego wystąpienia typu usługi.

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

Klasa, `DealData`, definiuje stan, do którego można uzyskać dostęp za pomocą dowolnego kodu uruchomionego w tym samym wystąpieniu typu usługi.

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

W kodzie typu usługi, który implementuje jedną z operacji kontraktu usługi, `DealData` obiekt stanu jest dodawany do stanu bieżącego wystąpienia typu usługi.

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

Ten obiekt stanu może następnie zostać pobrany i zmodyfikowany przez kod implementujący inny element operacji kontraktu usługi.

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

Program ASP.NET zapewnia kontrolę nad tym, gdzie w rzeczywistości <xref:System.Web.HttpContext> są przechowywane informacje o stanie w klasie, WCF, co najmniej w wersji wstępnej, nie zapewnia kontroli nad tym, gdzie są przechowywane Rozszerzalne obiekty. Stanowi to bardzo najlepszy powód wyboru ASP.NET tryb zgodności dla usługi WCF. Jeśli konfigurowalne zarządzanie stanem jest bezwzględne, to w trybie zgodności ASP.NET można używać obiektów <xref:System.Web.HttpContext> klasy dokładnie tak, jak są one używane w ASP.NET, a także do konfigurowania informacji o stanie zarządzanych przy użyciu <xref:System.Web.HttpContext> Klasa jest przechowywana.

## <a name="security"></a>Zabezpieczenia

Opcje zabezpieczania usług sieci Web ASP.NET są tymi, które służą do zabezpieczania dowolnej aplikacji usług IIS. Ponieważ aplikacje WCF mogą być hostowane nie tylko w ramach usług IIS, ale również w ramach dowolnego pliku wykonywalnego platformy .NET, opcje zabezpieczania aplikacji WCF muszą być niezależne od obiektów usług IIS. Dostępne są jednak funkcje usługi sieci Web ASP.NET dla usług WCF działających w trybie zgodności ASP.NET.

### <a name="security-authentication"></a>Bezpieczeństw Uwierzytelnianie

Usługi IIS zapewniają funkcje do kontrolowania dostępu do aplikacji, w których można wybrać dostęp anonimowy lub wiele różnych trybów uwierzytelniania: Uwierzytelnianie systemu Windows, uwierzytelnianie szyfrowane, uwierzytelnianie podstawowe i uwierzytelnianie .NET Passport. Opcji uwierzytelniania systemu Windows można użyć do kontrolowania dostępu do usług sieci Web ASP.NET. Jeśli jednak aplikacje WCF są hostowane w usługach IIS, usługi IIS muszą być skonfigurowane tak, aby zezwalały na dostęp anonimowy do aplikacji, dzięki czemu uwierzytelnianie może być zarządzane przez usługę WCF, która obsługuje uwierzytelnianie systemu Windows między różnymi innymi opcjami. Inne opcje, które są wbudowane, obejmują tokeny username, certyfikaty X. 509, tokeny SAML i karty CardSpace, ale można również zdefiniować niestandardowe mechanizmy uwierzytelniania.

### <a name="security-impersonation"></a>Bezpieczeństw Personifikacja

ASP.NET udostępnia element tożsamości, za pomocą którego można przeprowadzić usługę sieci Web ASP.NET w celu personifikacji określonego użytkownika lub poświadczeń użytkownika, które są dostarczane z bieżącym żądaniem. Tego elementu można użyć do skonfigurowania personifikacji w aplikacjach WCF działających w trybie zgodności ASP.NET.

System konfiguracji WCF udostępnia swój własny element tożsamości służący do wyznaczania określonego użytkownika do personifikacji. Ponadto klienci i usługi WCF mogą być skonfigurowane niezależnie do personifikacji. Klientów można skonfigurować do personifikacji bieżącego użytkownika podczas przesyłania żądań.

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

Operacje usługi można skonfigurować w taki sposób, aby personifikowanie poświadczeń użytkownika zostało zapewnione przy użyciu bieżącego żądania.

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a>Bezpieczeństw Autoryzacja za pomocą list Access Control

Listy Access Control (ACL) mogą służyć do ograniczania dostępu do plików. asmx. Listy ACL plików programu WCF. svc są jednak ignorowane, z wyjątkiem trybu zgodności ASP.NET.

### <a name="security-role-based-authorization"></a>Bezpieczeństw Autoryzacja oparta na rolach

Opcji uwierzytelniania systemu Windows w usługach IIS można używać w połączeniu z elementem autoryzacji udostępnianym przez język konfiguracji ASP.NET, aby ułatwić autoryzację opartą na rolach dla usług sieci Web ASP.NET w oparciu o grupy systemu Windows, do których są przypisani użytkownicy . W ASP.NET 2,0 wprowadzono bardziej ogólny mechanizm autoryzacji oparty na rolach: dostawcy ról.

Dostawcy ról to klasy, które implementują podstawowy interfejs do uzyskiwania informacji o rolach przypisanych do użytkownika, ale każdy dostawca roli wie, jak pobrać te informacje z innego źródła. ASP.NET 2,0 zapewnia dostawcę roli, który może pobierać przypisania ról z bazy danych Microsoft SQL Server, a druga, która może pobierać przypisania ról z Menedżera autoryzacji systemu Windows Server 2003.

Mechanizm dostawcy roli można faktycznie używać niezależnie od ASP.NET w dowolnej aplikacji platformy .NET, w tym aplikacji WCF. Poniższa Konfiguracja przykładowa aplikacji WCF pokazuje, jak używać dostawcy roli ASP.NET jest opcją wybraną za <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>pomocą.

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

### <a name="security-claims-based-authorization"></a>Bezpieczeństw Autoryzacja oparta na oświadczeniach

Jednym z najważniejszych innowacji usługi WCF jest kompleksowa obsługa autoryzacji dostępu do chronionych zasobów w oparciu o oświadczenia. Oświadczenia składają się z typu, praw i wartości, na przykład licencji na sterowniki. Tworzy zestaw oświadczeń dotyczących okaziciela, z których jedna jest datą urodzenia okaziciela. Typ tego zgłoszenia to data urodzenia, podczas gdy wartość żądania jest datą urodzenia sterownika. Prawo, że w odniesieniu do osoby korzystającej z roszczeń określa, co może zrobić, z wartością żądania. W przypadku roszczeń dotyczących daty urodzenia sterownika, prawo jest posiadanie: kierowca ma tę datę urodzenia, ale nie może na przykład zmienić. Autoryzacja oparta na oświadczeniach obejmuje autoryzację opartą na rolach, ponieważ role są typem oświadczenia.

Autoryzacja oparta na oświadczeniach jest realizowana poprzez porównanie zestawu oświadczeń z wymaganiami dostępu operacji i, w zależności od wyniku porównania, przyznanie lub odmowa dostępu do operacji. W programie WCF można określić klasę, która ma być używana do uruchamiania autoryzacji opartej na oświadczeniach, przez przypisanie wartości do `ServiceAuthorizationManager` <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>właściwości.

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

Klasy służące do uruchamiania autoryzacji opartej na oświadczeniach <xref:System.ServiceModel.ServiceAuthorizationManager>muszą pochodzić od `AccessCheck()`elementu, który ma tylko jedną metodę przesłonięcia. Funkcja WCF wywołuje tę metodę za każdym razem, gdy zostanie wywołana operacja usługi i <xref:System.ServiceModel.OperationContext> udostępnia obiekt, który ma oświadczenia dla użytkownika w jego `ServiceSecurityContext.AuthorizationContext` właściwości. Program WCF wykonuje zadania składania oświadczeń dotyczących użytkownika z dowolnego tokenu zabezpieczającego, który użytkownik dostarczył do uwierzytelniania, co pozostawia zadanie oceny, czy te oświadczenia są wystarczające dla danej operacji.

Usługa WCF automatycznie łączy oświadczenia z dowolnego rodzaju tokenów zabezpieczających, ponieważ sprawia, że kod autoryzacji jest oparty na oświadczeniach całkowicie niezależnie od mechanizmu uwierzytelniania. Z kolei autoryzacja przy użyciu list ACL lub ról w ASP.NET jest ściśle związana z uwierzytelnianiem systemu Windows.

### <a name="security-confidentiality"></a>Bezpieczeństw Poufne

Poufność komunikatów wymienianych z usługami sieci Web ASP.NET można zapewnić na poziomie transportu przez skonfigurowanie aplikacji w usługach IIS do korzystania z protokołu HTTPS (Secure Hypertext Transfer Protocol). Tę samą funkcję można wykonać w przypadku aplikacji WCF hostowanych w usługach IIS. Jednak aplikacje WCF hostowane poza usługami IIS można także skonfigurować do korzystania z protokołu Secure Transport Protocol. Ważniejsze aplikacje usług WCF można także skonfigurować w celu zabezpieczenia komunikatów przed ich transportem przy użyciu protokołu WS-Security. Zabezpieczenie tylko treści wiadomości za pomocą usługi WS-Security pozwala na ich przekazanie poufne w ramach pośredników przed osiągnięciem ostatecznego miejsca docelowego.

## <a name="globalization"></a>Globalizacja

Język konfiguracji ASP.NET umożliwia określenie kultury dla poszczególnych usług. Funkcja WCF nie obsługuje tego ustawienia konfiguracji, z wyjątkiem trybu zgodności ASP.NET. Aby zlokalizować usługę WCF, która nie korzysta z trybu zgodności ASP.NET, skompiluj typ usługi do zestawów specyficznych dla kultury i mają oddzielne punkty końcowe specyficzne dla kultury dla każdego zestawu specyficznego dla kultury.

## <a name="see-also"></a>Zobacz także

- [Porównanie usług internetowych platformy ASP.NET i architektury WCF na podstawie przeznaczenia oraz stosowanych standardów](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
