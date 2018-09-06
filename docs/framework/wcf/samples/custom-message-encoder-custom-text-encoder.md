---
title: 'Niestandardowy koder komunikatów: Niestandardowy koder tekstu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: aeb1690d7ead9116bd9c4afe3c64d65d8f51ad50
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43732225"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Niestandardowy koder komunikatów: Niestandardowy koder tekstu
Ten przykład demonstruje sposób implementacji tekst niestandardowy koder komunikatów, za pomocą usługi Windows Communication Foundation (WCF).  
  
> [!WARNING]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> Programu WCF obsługuje tylko kodowania UTF-8, UTF-16 i Big Endean Unicode. Koder komunikatów niestandardowego tekstu, w tym przykładzie obsługuje wszystkie obsługiwane platformy kodowanie znaków, które mogą być wymagane do współdziałania. Przykład składa się z konsoli program kliencki (.exe), Usługa biblioteki (.dll), obsługiwane przez usługi Internet Information Services (IIS) i tekst komunikatu kodera biblioteki (.dll). Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź". Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (dodawania, odejmowania, mnożenia i dzielenia). Klient wysyła żądań synchronicznych operacji matematycznych danego i odpowiedzi usługi z wynikiem. Zarówno klient, jak i usługa używa `CustomTextMessageEncoder` zamiast domyślnego <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 Implementacji niestandardowego kodera składa się z fabryki kodera komunikatów, kodera komunikatów, komunikatu kodowanie elementu powiązania i obsługi konfiguracji i pokazuje następujące czynności:  
  
-   Tworzenie niestandardowego kodera, a koder fabryki.  
  
-   Tworzenie elementu powiązania dla niestandardowego kodera.  
  
-   Za pomocą konfiguracji powiązania niestandardowego do integrowania elementy niestandardowego powiązania.  
  
-   Tworzenie obsługi niestandardowej konfiguracji, który umożliwia skonfigurowanie pliku elementu niestandardowego powiązania.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0, używając następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>Fabryki kodera komunikatów i kodera komunikatów  
 Gdy <xref:System.ServiceModel.ServiceHost> lub klient zostanie otwarty kanał, składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory`. Tworzy fabrykę `CustomTextMessageEncoder`. Koder komunikatów działa zarówno w trybie przesyłania strumieniowego i tryb buforowany. Używa ona <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio. W przeciwieństwie do zoptymalizowane czytniki XML i składników zapisywania programu WCF, które obsługują tylko UTF-8, UTF-16 i Big Endean Unicode te czytników i składników zapisywania kodowanie jest obsługiwane wszystkie obsługiwane platformy.  
  
 Poniższy przykład kodu pokazuje CustomTextMessageEncoder.  
  
```csharp  
public class CustomTextMessageEncoder : MessageEncoder  
{  
    private CustomTextMessageEncoderFactory factory;  
    private XmlWriterSettings writerSettings;  
    private string contentType;  
  
    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)  
    {  
        this.factory = factory;  
  
        this.writerSettings = new XmlWriterSettings();  
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);  
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
    }  
  
    public override string ContentType  
    {  
        get  
        {  
            return this.contentType;  
        }  
    }  
  
    public override string MediaType  
    {  
        get   
        {  
            return factory.MediaType;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {  
            return this.factory.MessageVersion;  
        }  
    }  
  
    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)  
    {     
        byte[] msgContents = new byte[buffer.Count];  
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);  
        bufferManager.ReturnBuffer(buffer.Array);  
  
        MemoryStream stream = new MemoryStream(msgContents);  
        return ReadMessage(stream, int.MaxValue);  
    }  
  
    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)  
    {  
        XmlReader reader = XmlReader.Create(stream);  
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);  
    }  
  
    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)  
    {  
        MemoryStream stream = new MemoryStream();  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
  
        byte[] messageBytes = stream.GetBuffer();  
        int messageLength = (int)stream.Position;  
        stream.Close();  
  
        int totalLength = messageLength + messageOffset;  
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);  
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);  
  
        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);  
        return byteArray;  
    }  
  
    public override void WriteMessage(Message message, Stream stream)  
    {  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
    }  
}  
```  
  
 Poniższy przykład kodu pokazuje, jak tworzyć fabryki kodera komunikatów.  
  
```csharp  
public class CustomTextMessageEncoderFactory : MessageEncoderFactory  
{  
    private MessageEncoder encoder;  
    private MessageVersion version;  
    private string mediaType;  
    private string charSet;  
  
    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,  
        MessageVersion version)  
    {  
        this.version = version;  
        this.mediaType = mediaType;  
        this.charSet = charSet;  
        this.encoder = new CustomTextMessageEncoder(this);  
    }  
  
    public override MessageEncoder Encoder  
    {  
        get   
        {   
            return this.encoder;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {   
            return this.version;  
        }  
    }  
  
    internal string MediaType  
    {  
        get  
        {  
            return this.mediaType;  
        }  
    }  
  
    internal string CharSet  
    {  
        get  
        {  
            return this.charSet;  
        }  
    }  
}  
```  
  
## <a name="message-encoding-binding-element"></a>Element powiązania kodowania komunikatu  
 Elementy powiązania umożliwiają konfigurację stos środowiska wykonawczego programu WCF. Aby użyć niestandardowy koder komunikatów w aplikacji WCF, wymagany jest element powiązania tworząca fabryki kodera komunikatów z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.  
  
 `CustomTextMessageBindingElement` Pochodzi od klasy <xref:System.ServiceModel.Channels.BindingElement> klasy bazowej i dziedziczy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy. Dzięki temu inne składniki usługi WCF do rozpoznawania tego elementu powiązania jako element powiązania z kodowania komunikatu. Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> Zwraca wystąpienie pasującego fabryki kodera komunikatów za pomocą odpowiednich ustawień.  
  
 `CustomTextMessageBindingElement` Udostępnia ustawienia dla `MessageVersion`, `ContentType`, i `Encoding` za pośrednictwem właściwości. Koder obsługuje zarówno Soap11Addressing, jak i Soap12Addressing1 wersji. Wartość domyślna to Soap11Addressing1. Wartość domyślna `ContentType` jest "text/xml". `Encoding` Właściwość można ustawić wartości kodowania żądany znak. Przykładowy klient i usługa używa ISO-8859-1 (Latin1) kodowanie znaków, które nie są obsługiwane przez <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> programu WCF.  
  
 Poniższy kod pokazuje, jak programowo utworzyć powiązania za pomocą tekst niestandardowy koder komunikatów.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Dodanie obsługi metadanych do kodowania, Element powiązania komunikatu  
 Dowolny typ, który pochodzi od klasy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania protokołu SOAP w dokumencie WSDL, wygenerowany dla usługi. Polega to na implementowanie `ExportEndpoint` metody <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsu, a następnie zmodyfikowanie wygenerowanego pliku WSDL. W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL `TextMessageEncodingBinidngElement`.  
  
 W tym przykładzie konfiguracja klienta jest skonfigurowane ręcznie. Nie można użyć Svcutil.exe do generowania konfiguracji klienta, ponieważ `CustomTextMessageBindingElement` nie eksportuje asercję zasad w celu opisania jego zachowanie. Ogólnie należy zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu na element niestandardowego powiązania, aby wyeksportować asercji zasad niestandardowych, opisujący zachowanie lub możliwości implementowane przez element powiązania. Na przykład sposobu eksportowania asercję zasad dla elementu niestandardowego powiązania zobacz [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
## <a name="message-encoding-binding-configuration-handler"></a>Program obsługi konfiguracji powiązania kodowania komunikatu  
 Poprzedniej sekcji pokazano, jak programowo używać tekst niestandardowy koder komunikatów. `CustomTextMessageEncodingBindingSection` Implementuje obsługi konfiguracji, który pozwala określić niestandardowy komunikat koder tekstu w pliku konfiguracji. `CustomTextMessageEncodingBindingSection` Klasa pochodzi od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. `BindingElementType` Właściwość informuje system konfiguracji typu elementu powiązania do utworzenia dla tej sekcji.  
  
 Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są widoczne jako właściwości w `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> Pomaga w mapowania atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli ten atrybut nie jest ustawiona. Po wartości z konfiguracji zostaną załadowane i zastosowane do właściwości typu <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> wywoływana jest metoda, która konwertuje właściwości na konkretne wystąpienie elementu powiązania.  
  
 Ta procedura obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config, usługi lub klienta.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 W przykładzie użyto kodowania ISO-8859-1.  
  
 Aby użyć tej obsługi konfiguracji, które muszą być zarejestrowane przy użyciu następującego elementu konfiguracji.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a>Zobacz też
