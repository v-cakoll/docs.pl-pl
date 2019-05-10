---
title: 'Niestandardowy koder komunikatów: Koder kompresji'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: d5ec330fb4aa0a136c4a0e4c8d249d7ebb9d0692
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650198"
---
# <a name="custom-message-encoder-compression-encoder"></a>Niestandardowy koder komunikatów: Koder kompresji
Ten przykład demonstruje sposób implementacji niestandardowego kodera, za pomocą platformy Windows Communication Foundation (WCF).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Przykład szczegółów  
 W tym przykładzie składa się z (.exe) klienta konsoli programu, (.exe) usługa hostowana samodzielnie konsoli programu i kompresji komunikat kodera biblioteki (.dll). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `ISampleServer` interfejs, który ujawnia podstawowe parametry wyświetlania operacji (`Echo` i `BigEcho`). Klient wysyła żądań synchronicznych do danej operacji i odpowiedzi usługi przez powtórzenie komunikatu do klienta. Aktywność klienta i usługi jest widoczna w oknie konsoli. Zamiarem tego przykładu jest pokazują, jak napisać niestandardowy koder i demonstrować wpływ kompresji wiadomości na łączu. Można dodać Instrumentację do kodera komunikatów kompresji, do obliczenia rozmiaru dla wiadomości i/lub czas przetwarzania.  
  
> [!NOTE]
>  W programie .NET Framework 4 dekompresja automatyczna jest ma włączone klienta WCF, jeśli serwer wysyła odpowiedź skompresowany (utworzonych za pomocą algorytmu, takich jak GZip lub Deflate). W przypadku usługi sieci Web hostowanych w Internet Information Server (IIS), usługi IIS można skonfigurować do wysyłania skompresowane odpowiedzi usługi. Można w tym przykładzie, jeśli wymagane jest celu kompresja i Dekompresja zarówno klient, jak i usługi lub usługi jest samodzielnie hostowana.  
  
 W przykładzie pokazano sposób tworzenia i zintegrować niestandardowy koder komunikatów aplikacji WCF. Biblioteka GZipEncoder.dll jest wdrażana przy użyciu zarówno klient, jak i usługi. Niniejszy przykład pokazuje także wpływ kompresowanie wiadomości. Kod w GZipEncoder.dll pokazuje następujące czynności:  
  
- Tworzenie niestandardowego kodera, a koder fabryki.  
  
- Tworzenie elementu powiązania dla niestandardowego kodera.  
  
- Za pomocą konfiguracji powiązania niestandardowego do integrowania elementy niestandardowego powiązania.  
  
- Tworzenie obsługi niestandardowej konfiguracji, który umożliwia skonfigurowanie pliku elementu niestandardowego powiązania.  
  
 Jak wcześniej wspomniano, istnieje kilka warstw, które są implementowane w niestandardowego kodera. Aby lepiej zilustrować relacji między każdym z tych warstw, uproszczone kolejności zdarzeń dla uruchamiania usługi jest na poniższej liście:  
  
1. Serwer jest uruchamiany.  
  
2. Informacje o konfiguracji jest do odczytu.  
  
    1. Konfiguracja usługi rejestruje obsługi konfiguracji niestandardowej.  
  
    2. Host usługi zostanie utworzony i otwarty.  
  
    3. Niestandardowy element konfiguracji, tworzy i zwraca element niestandardowego powiązania.  
  
    4. Element niestandardowego powiązania, tworzy i zwraca fabrykę koder komunikatu.  
  
3. Wiadomość zostaje odebrana.  
  
4. Fabryki kodera komunikatów zwraca kodera komunikatów do odczytu w komunikacie i wypisywanie odpowiedzi.  
  
5. Warstwa kodera jest implementowany jako fabrykę klas. Fabryka klas kodera musi być publicznie udostępniany dla niestandardowego kodera. Obiekt fabryki jest zwracany przez element powiązania podczas <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601> obiekt zostanie utworzony. Kodery komunikat może działać w tryb buforowany lub przesyłania strumieniowego. Niniejszy przykład pokazuje, zarówno w trybie buforowanego, jak i w trybie przesyłania strumieniowego.  
  
 Dla każdego trybu istnieje towarzyszący `ReadMessage` i `WriteMessage` metody abstrakcyjnej `MessageEncoder` klasy. Większość pracy kodowania odbywa się w tych metodach. Przykład opakowuje istniejący tekst i koderów komunikatu binarnego. Zezwala na przykład delegować odczytu i zapisu o komunikacji sieciowej reprezentacji w postaci wiadomości do wewnętrznego kodera i umożliwia koder kompresji kompresji lub dekompresji wyniki. Ponieważ nie ma żadnych potoku na potrzeby kodowania komunikatu, jest tylko model dla programu WCF za pomocą koderów wielu. Gdy komunikat został zdekompresowany, wynikowy wiadomości są przekazywane stosu stosu kanału do obsługi. Podczas kompresji wynikowy skompresowany wiadomości są zapisywane bezpośrednio z podanego strumienia.  
  
 W tym przykładzie użyto metody pomocnika (`CompressBuffer` i `DecompressBuffer`) do wykonywania konwersji z buforów do strumieni, aby użyć `GZipStream` klasy.  
  
 Buforowane `ReadMessage` i `WriteMessage` wprowadzić klasy użytkowania `BufferManager` klasy. Koder jest dostępna wyłącznie za pośrednictwem fabryki kodera. Abstrakcyjna `MessageEncoderFactory` klasy zawiera właściwości o nazwie `Encoder` do uzyskiwania dostępu do bieżącego encoder i metodę o nazwie `CreateSessionEncoder` dla tworzenia koder, który obsługuje sesji. Takie koder może służyć w sytuacji, gdy kanał obsługuje sesji, porządkowania i jest niezawodne. Ten scenariusz umożliwia optymalizacji w każdej sesji dane zapisywane podczas transmisji. Jeśli jest to niepożądane, nie być przeciążone metody podstawowej. `Encoder` Właściwość udostępnia mechanizm do uzyskiwania dostępu do mniej sesji kodera i domyślną implementację elementu `CreateSessionEncoder` metoda zwraca wartość właściwości. Ponieważ próbki opakowuje istniejących koder zapewnienie kompresji, `MessageEncoderFactory` akceptuje implementacji `MessageEncoderFactory` reprezentujący fabryki wewnętrzny kodera.  
  
 Skoro zdefiniowano encoder i fabryki kodera służy za pomocą klienta WCF i usługi. Jednak te koderów należy dodać do stosu kanału. Utworzeniu klasy pochodnej klasy z <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ChannelFactory%601> klasy i zastąpienie `OnInitialize` metody, aby ręcznie dodać tę fabrykę kodera. Należy również udostępnić fabryki kodera za pośrednictwem elementu niestandardowego powiązania.  
  
 Aby utworzyć nowy element niestandardowego powiązania, należy wyprowadzić klasę z <xref:System.ServiceModel.Channels.BindingElement> klasy. Istnieje jednak kilka typów elementów wiązania. Aby upewnić się, że element niestandardowego powiązania jest rozpoznawany jako element powiązania kodowania komunikatu, należy także zaimplementować <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Udostępnia metodę tworzenia nowej fabryki koder komunikatu (`CreateMessageEncoderFactory`), które jest implementowane w celu zwrócenia wystąpienia pasującego fabryki kodera komunikatów. Ponadto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> nie ma właściwości, aby wskazać, wersja adresowania. Ponieważ w tym przykładzie opakowuje istniejących koderów, w przykładowej implementacji również opakowuje kodera istniejących elementów wiązania przyjmuje kodera wewnętrzny element powiązania jako parametr do konstruktora i udostępnia go za pośrednictwem właściwości. Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingBindingElement` klasy.  
  
```  
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
  
 Należy pamiętać, że `GZipMessageEncodingBindingElement` klasy implementuje `IPolicyExportExtension` interfejsu, tak aby ten element powiązania można wyeksportować jako zasady w metadanych, jak pokazano w poniższym przykładzie.  
  
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
  
 `GZipMessageEncodingBindingElementImporter` Klasy implementuje `IPolicyImportExtension` interfejsu, ta klasa zaimportowanie zasad dla `GZipMessageEncodingBindingElement`. Narzędzia svcutil.exe może służyć do zaimportowania zasady do pliku konfiguracji, aby obsłużyć `GZipMessageEncodingBindingElement`, dodaje do Svcutil.exe.config.  
  
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
  
 Teraz, czy jest pasujący element powiązania dla koder kompresji, jego mogą być programowo dołączane do usługi lub klienta tworząc nowy obiekt niestandardowego powiązania i Dodawanie elementu niestandardowego powiązania, jak pokazano w poniższym przykładowym kodzie.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 Chociaż może to być wystarczające w większości scenariuszy użytkowników, obsługa plik konfiguracyjny ma krytyczne znaczenie, jeśli usługa ma być hostowane w sieci Web. Aby zapewnić obsługę scenariusza hostingu w sieci Web, możesz tworzyć obsługi niestandardowej konfiguracji, aby zezwolić na element niestandardowego powiązania umożliwiać konfigurację w pliku.  
  
 Można utworzyć program obsługi konfiguracji dla elementu powiązania na podstawie dostarczonych przez system konfiguracji [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Obsługa konfiguracji element powiązania musi pochodzić od klasy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. `BindingElementType` Właściwość jest używana w celu poinformowania systemu konfiguracji typu elementu powiązania do utworzenia dla tej sekcji. Wszystkie aspekty `BindingElement` , może być zestaw powinny zostać ujawnione jako właściwości na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy pochodnej. <xref:System.Configuration.ConfigurationPropertyAttribute> Jest używany jako pomoc w mapowania atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli atrybuty są spełnione. Po wartości z konfiguracji zostaną załadowane i zastosowane do właściwości, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> wywoływana jest metoda, która konwertuje właściwości na konkretne wystąpienie elementu powiązania. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda jest używana do konwersji właściwości na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy pochodnej na wartości, które ma być ustawiony na element powiązania newlycreated.  
  
 Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingElement`.  
  
```  
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
  
 Ta procedura obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config, usługi lub klienta.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Aby korzystać z tej obsługi konfiguracji, musi być zarejestrowana w ramach [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, jak pokazano w poniższym Przykładowa konfiguracja.  
  
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
  
 Po uruchomieniu serwera, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli. Naciśnij klawisz ENTER w oknie do zamykania serwera.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 Po uruchomieniu klienta, operacji żądań i odpowiedzi są wyświetlane w oknie konsoli. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1. Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
