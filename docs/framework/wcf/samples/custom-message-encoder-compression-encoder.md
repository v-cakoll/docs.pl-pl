---
title: 'Niestandardowy koder komunikatów: Koder kompresji'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: 5dc665da3b28a98f1b3016d38ce706bf77dce06f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808744"
---
# <a name="custom-message-encoder-compression-encoder"></a>Niestandardowy koder komunikatów: Koder kompresji
W tym przykładzie pokazano, jak wdrożyć niestandardowego kodera przy użyciu platformy Windows Communication Foundation (WCF).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Szczegóły próbki  
 W tym przykładzie składa się z konsoli program kliencki (.exe), (.exe) hostowanie Samoobsługowe konsoli programu i kompresji biblioteki kodera wiadomości (.dll). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ISampleServer` interfejsu, który ujawnia podstawowe ciągu wyświetlania operacji (`Echo` i `BigEcho`). Klient wysyła żądań synchronicznych operacji i odpowiedzi usługi powtarzając wiadomość do klienta. Aktywność klienta i usługi jest widoczna w oknie konsoli. Celem tego przykładu jest pokazują, jak zapisać niestandardowego kodera i Wykaż wpływ kompresji wiadomości w sieci. Możesz dodać Instrumentacji do kodera wiadomości kompresji do obliczenia rozmiaru wiadomości i czas przetwarzania.  
  
> [!NOTE]
>  W .NET Framework 4 został włączony automatycznej dekompresji na klienta WCF, jeśli serwer wysyła odpowiedź skompresowane (utworzone przy użyciu algorytmu, takich jak GZip i Deflate). W przypadku usługi sieci Web hostowanych w Internet Information Server (IIS), usługi IIS można skonfigurować do wysyłania skompresowane odpowiedzi usługi. Można w tym przykładzie, jeśli wymagane jest przeprowadzenie kompresji i dekompresji zarówno klient, jak i usługi lub usługa jest samodzielnie hostowana.  
  
 Przykład pokazuje, jak kompilacji i integracji niestandardowy koder komunikatów w aplikacji WCF. Biblioteka GZipEncoder.dll jest wdrażana z zarówno klient, jak i usługi. W przykładzie pokazano także wpływ kompresowania wiadomości. Kod w GZipEncoder.dll przedstawiono poniżej:  
  
-   Tworzenie niestandardowego kodera i fabryki kodera.  
  
-   Tworzenie elementu powiązania dla niestandardowego kodera.  
  
-   Za pomocą konfiguracji powiązania niestandardowego do integracji elementy niestandardowego powiązania.  
  
-   Tworzenie konfiguracji niestandardowej obsługi umożliwia konfigurację pliku element niestandardowego powiązania.  
  
 Jak wcześniej wspomniano, istnieje kilka warstwy, które zostały wdrożone w niestandardowego kodera. Aby lepiej zilustrować relacji między każdym z tych warstw, uproszczone kolejność zdarzeń do uruchamiania usługi jest na poniższej liście:  
  
1.  Serwer zostanie uruchomiony.  
  
2.  Informacje o konfiguracji jest do odczytu.  
  
    1.  Konfiguracja usługi rejestruje obsługi konfiguracji niestandardowej.  
  
    2.  Host usługi jest utworzony i otwarty.  
  
    3.  Element konfiguracji niestandardowej tworzy i zwraca element niestandardowego powiązania.  
  
    4.  Element niestandardowego powiązania tworzy i zwraca fabrykę kodera wiadomości.  
  
3.  Wiadomość zostanie odebrana.  
  
4.  Fabryka kodera wiadomości zwraca kodera wiadomości za odczytywanie wiadomości i zapisywania odpowiedzi.  
  
5.  Warstwa koder jest implementowany jako fabrykę klas. Fabryka klas kodera musi być publicznie wystawiony dla niestandardowego kodera. Obiekt fabryki jest zwracany przez element powiązania podczas <xref:System.ServiceModel.ServiceHost> lub <xref:System.ServiceModel.ChannelFactory%601> tworzony jest obiekt. Kodery komunikat może działać w trybie buforowanego lub przesyłania strumieniowego. W przykładzie pokazano, zarówno w trybie buforowanego, jak i w trybie przesyłania strumieniowego.  
  
 Dla każdego trybu istnieje towarzyszącego `ReadMessage` i `WriteMessage` metoda abstrakcyjna `MessageEncoder` klasy. Większość pracy kodowania odbywa się w tych metod. Przykład opakowuje istniejący tekst i kodery komunikatu binarnego. To pozwala na przykład, aby delegować do odczytywania i zapisywania reprezentacja przesyłania wiadomości do kodera wewnętrzny oraz umożliwia koder kompresji, które mają być kompresowane lub dekompresja wyniki. Ponieważ nie ma żadnych potoku dla kodowania komunikatu, jest tylko model dla programu WCF za pomocą koderów wiele. Po komunikat został zdekompresowany, komunikat wynikowy jest przekazywany w górę stosu stosu kanału do obsługi. Podczas kompresji wynikowy skompresowany wiadomości są zapisywane bezpośrednio do dostarczonego strumienia.  
  
 W przykładzie użyto metody pomocnicze (`CompressBuffer` i `DecompressBuffer`) aby dokonać konwersji z buforów do strumieni, aby użyć `GZipStream` klasy.  
  
 Buforowane `ReadMessage` i `WriteMessage` klasy należy korzystać z `BufferManager` klasy. Koder jest dostępna tylko za pośrednictwem fabryki kodera. Abstract `MessageEncoderFactory` klasy zawiera właściwości o nazwie `Encoder` do uzyskiwania dostępu do bieżącego kodera i metodę o nazwie `CreateSessionEncoder` umożliwiający utworzenie kodera, który obsługuje sesji. Takie kodera służy w sytuacji, gdy kanał obsługuje sesji, porządkowania i niezawodności. Ten scenariusz umożliwia optymalizacji w każdej sesji zapisanych do przesyłania danych. Jeśli jest to niepożądane, nie można przeciążać metodę podstawową. `Encoder` Właściwość udostępnia mechanizm do uzyskiwania dostępu do kodera bez sesji i domyślną implementację elementu `CreateSessionEncoder` metoda zwraca wartość właściwości. Ponieważ próbki opakowuje kodera istniejących zapewnienie kompresji, `MessageEncoderFactory` akceptuje implementacji `MessageEncoderFactory` reprezentujący fabryki wewnętrzny kodera.  
  
 Teraz, gdy są zdefiniowane koder i fabryki kodera służy z klienta WCF i usługi. Jednak te kodery należy dodać do stosu kanału. Mogą dziedziczyć klasy z <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ChannelFactory%601> klasy i zastąpienie `OnInitialize` metod, aby ręcznie dodać tej fabryki kodera. Można również ujawniać fabryki kodera przez element niestandardowego powiązania.  
  
 Aby utworzyć nowy element niestandardowego powiązania, pochodzi z klasy <xref:System.ServiceModel.Channels.BindingElement> klasy. Istnieje jednak kilka typów elementów powiązania. Aby upewnić się, że element niestandardowego powiązania jest rozpoznawana jako powiązanie element kodowania komunikatu, również należy zaimplementować <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> Udostępnia metodę tworzenia fabrykę kodera wiadomości (`CreateMessageEncoderFactory`), którego jest stosowana do zwrócenia wystąpienia pasującej fabryki kodera wiadomości. Ponadto <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> ma właściwość, aby wskazać wersja adresowania. Ponieważ w tym przykładzie opakowuje istniejące kodery, przykładowe zastosowanie również opakowuje koder istniejących elementów wiązania i przyjmuje kodera wewnętrznego powiązania elementu jako parametr do konstruktora i uwidacznia go za pośrednictwem właściwości. Następujący przykładowy kod przedstawia implementację `GZipMessageEncodingBindingElement` klasy.  
  
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
  
 Należy pamiętać, że `GZipMessageEncodingBindingElement` klasa implementuje `IPolicyExportExtension` interfejsu, tak aby ten element powiązania mogą być eksportowane jako zasady w metadanych, jak pokazano w poniższym przykładzie.  
  
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
  
 `GZipMessageEncodingBindingElementImporter` Klasa implementuje `IPolicyImportExtension` interfejsu, ta klasa zaimportowanie zasad dla `GZipMessageEncodingBindingElement`. Narzędzia svcutil.exe umożliwia importowanie zasad do pliku konfiguracji, aby obsłużyć `GZipMessageEncodingBindingElement`, dodaje do Svcutil.exe.config.  
  
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
  
 Teraz, brak pasującego elementu powiązania dla koder kompresji, jego mogą być programowane dołączane do usługi lub klienta tworząc nowy obiekt niestandardowego powiązania i Dodawanie elementu niestandardowego powiązania, jak pokazano w poniższym kodzie próbki.  
  
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
  
 Może to być wystarczające w większości scenariuszy użytkownika, Obsługa konfiguracji plików jest krytyczne, jeśli usługa ma być hostowana w sieci Web. Na potrzeby scenariusza hostowanych w sieci Web, należy utworzyć programu obsługi niestandardowej konfiguracji umożliwia element niestandardowego powiązania, będzie można skonfigurować w pliku.  
  
 Można utworzyć modułu obsługi konfiguracji element powiązania na udostępnione przez system konfiguracji [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. Obsługa konfiguracji dla elementu powiązania musi pochodzić od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. `BindingElementType` Właściwość jest używana do informuje system konfiguracji typu elementu powiązania, aby utworzyć dla tej sekcji. Wszystkie aspekty `BindingElement` które może być zestaw powinny zostać ujawnione jako właściwości <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. <xref:System.Configuration.ConfigurationPropertyAttribute> Jest używany jako pomoc w Mapowanie atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli brakuje atrybutów. Po wartości z konfiguracji są ładowane i stosowane do właściwości, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda jest wywoływana, który konwertuje na konkretne wystąpienie elementu powiązania właściwości. <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> Metoda jest używana do konwertowania właściwości na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> pochodnej klasy na wartości, należy ustawić w elemencie powiązania newlycreated.  
  
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
  
 Ten program obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config dla usługi lub klienta.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Aby korzystać z tej obsługi konfiguracji, musi być zarejestrowana w ramach [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, jak pokazano w poniższych Przykładowa konfiguracja.  
  
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
  
 Po uruchomieniu serwera operację żądania i odpowiedzi są wyświetlane w oknie konsoli. Naciśnij klawisz ENTER w oknie, aby zamknąć serwera.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 Po uruchomieniu klienta operacji żądania i odpowiedzi są wyświetlane w oknie konsoli. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>Zobacz też
