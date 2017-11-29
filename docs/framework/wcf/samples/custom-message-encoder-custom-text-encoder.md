---
title: "Niestandardowy koder komunikatów: Niestandardowy koder tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: def37608321923017e17a0296a4351cb951d6726
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Niestandardowy koder komunikatów: Niestandardowy koder tekstu
W tym przykładzie pokazano, jak zaimplementować tekst niestandardowy koder komunikatów, przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!WARNING]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko kodowania UTF-8, UTF-16 i Big Endean Unicode. Tekst niestandardowy koder komunikatów w tym przykładzie obsługuje wszystkie obsługiwane platformy kodowanie znaków, które mogą być wymagane ze względu na współdziałanie. Próbka składa się z konsoli programu klienckiego (.exe), Usługa biblioteki (.dll), obsługiwane przez usługi Internet Information Services (IIS) i tekst biblioteki kodera wiadomości (.dll). Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest definiowana za pomocą `ICalculator` interfejsu, który udostępnia operacji matematycznych (Dodawanie, odjąć mnożenia i dzielenia). Klient wysyła żądań synchronicznych operacji matematycznych danego i odpowiedzi usługi z wynikiem. Zarówno klient, jak i usługa używa `CustomTextMessageEncoder` zamiast domyślnej <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 Implementacji niestandardowego kodera składa się z fabryki kodera wiadomości, kodera wiadomości, kodowanie elementu powiązania i konfiguracji obsługi wiadomości i pokazano poniżej:  
  
-   Tworzenie niestandardowego kodera i fabryki kodera.  
  
-   Tworzenie elementu powiązania dla niestandardowego kodera.  
  
-   Za pomocą konfiguracji powiązania niestandardowego do integracji elementy niestandardowego powiązania.  
  
-   Tworzenie konfiguracji niestandardowej obsługi umożliwia konfigurację pliku element niestandardowego powiązania.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Zainstaluj [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 za pomocą następującego polecenia.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>Fabryka kodera wiadomości i koder komunikatów  
 Gdy <xref:System.ServiceModel.ServiceHost> lub klient otworzyć kanału, składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory`. Tworzy fabrykę `CustomTextMessageEncoder`. Koder komunikatów działa zarówno w trybie przesyłania strumieniowego i tryb buforowany. Używa <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio. Zamiast zoptymalizowane czytników XML i autorzy z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługują tylko UTF-8, UTF-16, jak i Unicode Big-Endean tych czytników i zapisywania obsługuje wszystkie obsługiwane platformy kodowania.  
  
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
  
 W poniższym przykładzie przedstawiono sposób zbudować fabryki kodera wiadomości.  
  
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
 Elementy można konfigurować [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu w czasie wykonywania. Aby użyć niestandardowy koder komunikatów w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikację, wymagany jest element powiązania tworzącą fabryki kodera wiadomości z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.  
  
 `CustomTextMessageBindingElement` Pochodną <xref:System.ServiceModel.Channels.BindingElement> klasa podstawowa i dziedziczy <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy. Dzięki temu innych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składniki rozpoznanie tego elementu powiązania jako powiązanie element kodowania komunikatu. Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> Zwraca wystąpienie klasy pasującej fabryki kodera wiadomości z odpowiednimi ustawieniami.  
  
 `CustomTextMessageBindingElement` Udostępnia ustawienia dla `MessageVersion`, `ContentType`, i `Encoding` za pośrednictwem właściwości. Koder obsługuje zarówno Soap11Addressing i Soap12Addressing1 wersji. Wartość domyślna to Soap11Addressing1. Wartość domyślna `ContentType` jest "text/xml". `Encoding` Właściwości można ustawić kodowanie znaków żądaną wartość. Przykładowe klient i usługa używa kodowania znaków ISO 8859-1 (Latin1), który nie jest obsługiwany przez <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Poniższy kod przedstawia sposób programowo Utwórz powiązanie, używając tekst niestandardowy koder komunikatów.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Dodawanie obsługi metadanych do kodowania, Element wiązania komunikatu  
 Dowolnego typu, która jest pochodną <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania SOAP w dokumencie WSDL wygenerowany dla usługi. W tym celu implementowania `ExportEndpoint` metody w <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejs, a następnie modyfikując wygenerowanego WSDL. W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL `TextMessageEncodingBinidngElement`.  
  
 Dla tego przykładu Konfiguracja klienta jest skonfigurowane ręcznie. Nie można użyć Svcutil.exe do wygenerowania konfiguracji klienta, ponieważ `CustomTextMessageBindingElement` nie eksportuje potwierdzenia zasad, opisujący zachowanie. Ogólnie należy zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejsu na element niestandardowego powiązania, aby wyeksportować potwierdzenia zasad niestandardowych, opisujący zachowanie lub możliwości implementowane przez element powiązania. Na przykład sposobu eksportowania potwierdzenia zasad dla elementu niestandardowego powiązania zobacz [transportu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) próbki.  
  
## <a name="message-encoding-binding-configuration-handler"></a>Program obsługi konfiguracji powiązania Kodowanie komunikatu  
 Poprzedniej sekcji pokazano, jak używać tekstu niestandardowego kodera wiadomości programowo. `CustomTextMessageEncodingBindingSection` Implementuje obsługi konfiguracji, która pozwala określić niestandardowy komunikat koder tekstu w pliku konfiguracji. `CustomTextMessageEncodingBindingSection` Pochodną klasy <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. `BindingElementType` Właściwości informuje system konfiguracji typu elementu powiązania, aby utworzyć dla tej sekcji.  
  
 Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są widoczne jako właściwości w `CustomTextMessageEncodingBindingSection`. <xref:System.Configuration.ConfigurationPropertyAttribute> Pomaga w Mapowanie atrybutów elementów konfiguracji do właściwości i ustawianie wartości domyślnych, jeśli nie ustawiono atrybutu. Po wartości z konfiguracji są ładowane i stosowane do właściwości typu <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> metoda jest wywoływana, który konwertuje na konkretne wystąpienie elementu powiązania właściwości.  
  
 Ten program obsługi konfiguracji mapuje następujące reprezentacja w pliku App.config lub Web.config dla usługi lub klienta.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 W przykładzie zastosowano kodowanie ISO 8859-1.  
  
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
