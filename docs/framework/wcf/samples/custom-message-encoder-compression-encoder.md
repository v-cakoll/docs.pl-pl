---
title: 'Niestandardowy koder komunikatów: Koder kompresji'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: db20ec20579d6fcb0ec202920db0d7781b0676df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600623"
---
# <a name="custom-message-encoder-compression-encoder"></a>Niestandardowy koder komunikatów: Koder kompresji

Ten przykład ilustruje sposób implementacji kodera niestandardowego przy użyciu platformy Windows Communication Foundation (WCF).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`

## <a name="sample-details"></a>Przykładowe szczegóły

Ten przykład składa się z programu konsolowego klienta (exe), samodzielnego programu obsługi konsoli usług (exe) i biblioteki kodera komunikatów kompresji (. dll). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ISampleServer` interfejs, który ujawnia podstawowe operacje ECHA ciągów ( `Echo` i `BigEcho` ). Klient wykonuje synchroniczne żądania do danej operacji i odpowiedzi usługi przez powtarzanie komunikatu z powrotem do klienta. Działanie klienta i usługi jest widoczne w oknach konsoli. Celem tego przykładu jest pokazanie sposobu pisania kodera niestandardowego i zademonstrowanie wpływu kompresji wiadomości w sieci. Można dodać instrumentację do kodera komunikatu kompresji, aby obliczyć rozmiar wiadomości, czas przetwarzania lub oba te elementy.

> [!NOTE]
> W .NET Framework 4 funkcja automatycznej dekompresji została włączona na kliencie WCF, jeśli serwer wysyła skompresowaną odpowiedź (utworzono przy użyciu algorytmu, takiego jak GZip lub Wklęśnięcie). Jeśli usługa jest hostowana w sieci Web w programie Internet Information Server (IIS), można skonfigurować usługi IIS do wysyłania skompresowanej odpowiedzi. Tego przykładu można użyć, jeśli wymagane jest kompresowanie i dekompresja zarówno klienta, jak i usługi, albo jeśli usługa jest samodzielna.

W przykładzie pokazano, jak skompilować i zintegrować niestandardowy koder komunikatów z aplikacją WCF. Biblioteka GZipEncoder. dll jest wdrażana razem z klientem i usługą. Ten przykład ilustruje także wpływ kompresowania komunikatów. Kod w GZipEncoder. dll ilustruje następujące elementy:

- Kompilowanie kodera niestandardowego i fabryki kodera.

- Tworzenie elementu powiązania dla kodera niestandardowego.

- Używanie konfiguracji niestandardowego powiązania do integrowania niestandardowych elementów powiązania.

- Opracowywanie niestandardowego programu obsługi konfiguracji w celu zezwolenia na konfigurację pliku niestandardowego powiązania.

Jak wskazano wcześniej, istnieje kilka warstw, które są zaimplementowane w niestandardowym koderie. Aby lepiej zilustrować relacje między każdą z tych warstw, uproszczona kolejność zdarzeń dla uruchamiania usługi znajduje się na poniższej liście:

1. Serwer zostanie uruchomiony.

2. Informacje o konfiguracji są odczytywane.

    1. Konfiguracja usługi rejestruje procedurę obsługi konfiguracji niestandardowej.

    2. Host usługi został utworzony i otwarty.

    3. Niestandardowy element konfiguracji tworzy i zwraca niestandardowy element powiązania.

    4. Niestandardowy element powiązania tworzy i zwraca fabrykę kodera komunikatów.

3. Odebrano komunikat.

4. Fabryka kodera komunikatów zwraca koder komunikatów służący do odczytu w komunikacie i zapisywania odpowiedzi.

5. Warstwa kodera jest zaimplementowana jako fabryka klas. Tylko fabryka klas kodera musi być publicznie uwidoczniona dla kodera niestandardowego. Obiekt fabryki jest zwracany przez element powiązania po <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.ChannelFactory%601> utworzeniu obiektu lub. Kodery komunikatów mogą działać w trybie buforowanym lub przesyłania strumieniowego. Ten przykład pokazuje tryb buforowany i tryb przesyłania strumieniowego.

Dla każdego trybu istnieje przyłączona `ReadMessage` i `WriteMessage` metoda klasy abstrakcyjnej `MessageEncoder` . Większość pracy z kodowaniem odbywa się w tych metodach. Przykład otacza istniejący tekst i binarne kodery komunikatów. Pozwala to przykładowi na oddelegowanie odczytu i zapisu komunikacji przewodowej komunikatów do kodera wewnętrznego i umożliwia koderowi kompresji kompresowanie lub kompresowanie wyników. Ponieważ nie ma potoku do kodowania komunikatów, jest to jedyny model używany do korzystania z wielu koderów w programie WCF. Po przeprowadzeniu dekompresowania komunikatu wynikowy komunikat jest przesyłany do stosu dla stosu kanału do obsłużenia. Podczas kompresji uzyskany skompresowany komunikat jest zapisywana bezpośrednio do podanego strumienia.

W tym przykładzie użyto metod pomocnika ( `CompressBuffer` i `DecompressBuffer` ) do wykonania konwersji z buforów na strumienie, aby użyć `GZipStream` klasy.

Buforowane `ReadMessage` i `WriteMessage` klasy wykorzystują `BufferManager` klasę. Koder jest dostępny tylko za pomocą fabryki kodera. Klasa abstrakcyjna `MessageEncoderFactory` zawiera właściwość o nazwie `Encoder` do uzyskiwania dostępu do bieżącego kodera oraz metodę o nazwie `CreateSessionEncoder` do tworzenia kodera, który obsługuje sesje. Takiego kodera można użyć w scenariuszu, w którym kanał obsługuje sesje, jest uporządkowany i niezawodny. Ten scenariusz umożliwia optymalizację w każdej sesji danych zapisywana w sieci. Jeśli nie jest to potrzebne, metoda podstawowa nie powinna być przeciążona. `Encoder`Właściwość zapewnia mechanizm uzyskiwania dostępu do kodera bez sesji i domyślna implementacja `CreateSessionEncoder` metody zwraca wartość właściwości. Ponieważ przykład otacza istniejący koder w celu zapewnienia kompresji, `MessageEncoderFactory` implementacja przyjmuje, `MessageEncoderFactory` że reprezentuje wewnętrzną fabrykę kodera.

Teraz, gdy jest zdefiniowany koder i fabryka kodera, mogą one być używane z klientem i usługą WCF. Jednak te kodery muszą zostać dodane do stosu kanału. Można dziedziczyć klasy z <xref:System.ServiceModel.ServiceHost> klas i <xref:System.ServiceModel.ChannelFactory%601> i zastąpić metody, `OnInitialize` Aby ręcznie dodać tę fabrykę kodera. Możesz również uwidocznić fabrykę koderów za pomocą niestandardowego elementu powiązania.

Aby utworzyć nowy element powiązania niestandardowego, Utwórz klasę z <xref:System.ServiceModel.Channels.BindingElement> klasy. Istnieje jednak kilka typów elementów powiązania. Aby zapewnić, że element powiązania niestandardowego jest rozpoznawany jako element powiązania kodowania komunikatów, należy również zaimplementować <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> . <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>Uwidacznia metodę tworzenia nowej fabryki kodera komunikatów ( `CreateMessageEncoderFactory` ), która jest zaimplementowana w celu zwrócenia wystąpienia zgodnej fabryki kodera komunikatów. Ponadto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> ma właściwość, która wskazuje na wersję adresowania. Ponieważ ten przykład otacza istniejące kodery, implementacja przykładu otacza istniejące elementy powiązania kodera i przyjmuje wewnętrzny element powiązania kodera jako parametr do konstruktora i udostępnia go za pomocą właściwości. Poniższy przykładowy kod przedstawia implementację `GZipMessageEncodingBindingElement` klasy.

```csharp
public sealed class GZipMessageEncodingBindingElement
                        : MessageEncodingBindingElement //BindingElement
                        , IPolicyExportExtension
{

    //We use an inner binding element to store information
    //required for the inner encoder.
    MessageEncodingBindingElement innerBindingElement;

        //By default, use the default text encoder as the inner encoder.
        public GZipMessageEncodingBindingElement()
            : this(new TextMessageEncodingBindingElement()) { }

    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)
    {
        this.innerBindingElement = messageEncoderBindingElement;
    }

    public MessageEncodingBindingElement InnerMessageEncodingBindingElement
    {
        get { return innerBindingElement; }
        set { innerBindingElement = value; }
    }

    //Main entry point into the encoder binding element.
    // Called by WCF to get the factory that creates the
    //message encoder.
    public override MessageEncoderFactory CreateMessageEncoderFactory()
    {
        return new
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());
    }

    public override MessageVersion MessageVersion
    {
        get { return innerBindingElement.MessageVersion; }
        set { innerBindingElement.MessageVersion = value; }
    }

    public override BindingElement Clone()
    {
        return new
        GZipMessageEncodingBindingElement(this.innerBindingElement);
    }

    public override T GetProperty<T>(BindingContext context)
    {
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))
        {
            return innerBindingElement.GetProperty<T>(context);
        }
        else
        {
            return base.GetProperty<T>(context);
        }
    }

    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelFactory<TChannel>();
    }

    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.BuildInnerChannelListener<TChannel>();
    }

    public override bool CanBuildChannelListener<TChannel>(BindingContext context)
    {
        if (context == null)
            throw new ArgumentNullException("context");

        context.BindingParameters.Add(this);
        return context.CanBuildInnerChannelListener<TChannel>();
    }

    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)
    {
        if (policyContext == null)
        {
            throw new ArgumentNullException("policyContext");
        }
       XmlDocument document = new XmlDocument();
       policyContext.GetBindingAssertions().Add(document.CreateElement(
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,
            GZipMessageEncodingPolicyConstants.GZipEncodingName,
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));
    }
}
```

Należy zauważyć, że `GZipMessageEncodingBindingElement` Klasa implementuje `IPolicyExportExtension` interfejs, dzięki czemu ten element powiązania można wyeksportować jako zasady w metadanych, jak pokazano w poniższym przykładzie.

```xml
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">
    <wsp:ExactlyOne>
      <wsp:All>
        <gzip:text xmlns:gzip=
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />
       <wsaw:UsingAddressing />
     </wsp:All>
   </wsp:ExactlyOne>
</wsp:Policy>
```

`GZipMessageEncodingBindingElementImporter`Klasa implementuje `IPolicyImportExtension` interfejs, ta klasa importuje zasady dla `GZipMessageEncodingBindingElement` . Narzędzie Svcutil. exe może służyć do importowania zasad do pliku konfiguracji, aby obsłużyć `GZipMessageEncodingBindingElement` następujące czynności należy dodać do Svcutil. exe. config.

```xml
<configuration>
  <system.serviceModel>
    <extensions>
      <bindingElementExtensions>
        <add name="gzipMessageEncoding"
          type=
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
      </bindingElementExtensions>
    </extensions>
    <client>
      <metadata>
        <policyImporters>
          <remove type=
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
          <extension type=
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </policyImporters>
      </metadata>
    </client>
  </system.serviceModel>
</configuration>
```

Teraz, gdy istnieje pasujący element powiązania dla kodera kompresji, można go programowo podłączyć do usługi lub klienta przez zbudowanie nowego niestandardowego obiektu powiązania i dodanie do niego elementu niestandardowego powiązania, jak pokazano w poniższym przykładowym kodzie.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();
bindingElements.Add(compBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
binding.Name = "SampleBinding";
binding.Namespace = "http://tempuri.org/bindings";
```

Chociaż może to być wystarczające dla większości scenariuszy użytkowników, obsługa konfiguracji plików jest niezwykle ważna, jeśli usługa ma być hostowana w Internecie. Aby zapewnić obsługę scenariusza hostowanego w sieci Web, należy opracować procedurę obsługi konfiguracji niestandardowej, aby umożliwić konfigurację elementu niestandardowego powiązania w pliku.

Można utworzyć procedurę obsługi konfiguracji dla elementu Binding na górze systemu konfiguracyjnego. Program obsługi konfiguracji dla elementu Binding musi być pochodną <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.BindingElementType?displayProperty=nameWithType>Informuje system konfiguracji typu elementu powiązania, który ma zostać utworzony dla tej sekcji. Wszystkie aspekty `BindingElement` , które można ustawić, powinny być uwidocznione jako właściwości w <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasie pochodnej. <xref:System.Configuration.ConfigurationPropertyAttribute>Pomaga w mapowaniu atrybutów elementu konfiguracji do właściwości i ustawiania wartości domyślnych w przypadku braku atrybutów. Po załadowaniu wartości z konfiguracji i zastosowaniu ich do właściwości <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A?displayProperty=nameWithType> jest wywoływana metoda, która konwertuje właściwości na konkretne wystąpienie elementu powiązania. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A?displayProperty=nameWithType>Metoda służy do konwertowania właściwości <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy pochodnej na wartości, które mają być ustawiane dla nowo utworzonego elementu powiązania.

Poniższy przykładowy kod przedstawia implementację programu `GZipMessageEncodingElement` .

```csharp
public class GZipMessageEncodingElement : BindingElementExtensionElement
{
    public GZipMessageEncodingElement()
    {
    }

//Called by the WCF to discover the type of binding element this
//config section enables
    public override Type BindingElementType
    {
        get { return typeof(GZipMessageEncodingBindingElement); }
    }

    //The only property we need to configure for our binding element is
    //the type of inner encoder to use. Here, we support text and
    //binary.
    [ConfigurationProperty("innerMessageEncoding",
                         DefaultValue = "textMessageEncoding")]
    public string InnerMessageEncoding
    {
        get { return (string)base["innerMessageEncoding"]; }
        set { base["innerMessageEncoding"] = value; }
    }

    //Called by the WCF to apply the configuration settings (the
    //property above) to the binding element
    public override void ApplyConfiguration(BindingElement bindingElement)
    {
        GZipMessageEncodingBindingElement binding =
                (GZipMessageEncodingBindingElement)bindingElement;
        PropertyInformationCollection propertyInfo =
                    this.ElementInformation.Properties;
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=
                                     PropertyValueOrigin.Default)
        {
            switch (this.InnerMessageEncoding)
            {
                case "textMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                      new TextMessageEncodingBindingElement();
                    break;
                case "binaryMessageEncoding":
                    binding.InnerMessageEncodingBindingElement =
                         new BinaryMessageEncodingBindingElement();
                    break;
            }
        }
    }

    //Called by the WCF to create the binding element
    protected override BindingElement CreateBindingElement()
    {
        GZipMessageEncodingBindingElement bindingElement =
                new GZipMessageEncodingBindingElement();
        this.ApplyConfiguration(bindingElement);
        return bindingElement;
    }
}
```

Ta procedura obsługi konfiguracji mapuje do następującej reprezentacji w pliku App. config lub Web. config dla usługi lub klienta.

```xml
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />
```

Aby użyć tego programu obsługi konfiguracji, musi on być zarejestrowany w obrębie [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak pokazano w poniższej konfiguracji przykładowej.

```xml
<extensions>
    <bindingElementExtensions>
       <add
           name="gzipMessageEncoding"
           type=
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,
           GZipEncoder, Version=1.0.0.0, Culture=neutral,
           PublicKeyToken=null" />
      </bindingElementExtensions>
</extensions>
```

Po uruchomieniu serwera programu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli. Naciśnij klawisz ENTER w oknie, aby zamknąć serwer.

```console
Press Enter key to Exit.

        Server Echo(string input) called:
        Client message: Simple hello

        Server BigEcho(string[] input) called:
        64 client messages
```

Po uruchomieniu klienta żądania operacji i odpowiedzi są wyświetlane w oknie konsoli. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

```console
Calling Echo(string):
Server responds: Simple hello Simple hello

Calling BigEcho(string[]):
Server responds: Hello 0

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj program ASP.NET 4,0 przy użyciu następującego polecenia:

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`
