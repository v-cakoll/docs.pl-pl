---
title: 'Niestandardowy koder komunikatów: Niestandardowy koder tekstu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88aeeb4f1d09795b768441d2a572d959f27e0226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145114"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Niestandardowy koder komunikatów: Niestandardowy koder tekstu

W tym przykładzie pokazano, jak zaimplementować niestandardowy koder wiadomości tekstowych przy użyciu programu Windows Communication Foundation (WCF).

> [!WARNING]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

WCF <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> obsługuje tylko kodowania UTF-8, UTF-16 i big-endian Unicode. Koder niestandardowych wiadomości tekstowych w tym przykładzie obsługuje wszystkie kodowania znaków obsługiwanych przez platformę, które mogą być wymagane do współdziałania. Przykład składa się z programu konsoli klienta (exe), biblioteki usług (dll) hostowanego przez internetowe usługi informacyjne (IIS) oraz biblioteki kodera wiadomości tekstowych (.dll). Usługa implementuje kontrakt, który definiuje wzorzec komunikacji żądanie odpowiedź. Kontrakt jest zdefiniowany `ICalculator` przez interfejs, który udostępnia operacje matematyczne (Dodaj, Odejmij, Mnądko i Podziel). Klient sprawia, że synchroniczne żądania do danej operacji matematycznej i odpowiedzi usługi z wynikiem. Zarówno klient, jak `CustomTextMessageEncoder` i usługa używają <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>zamiast domyślnego .

Implementacja niestandardowego kodera składa się z fabryki kodera wiadomości, kodera wiadomości, elementu wiązania kodującego wiadomości i programu obsługi konfiguracji i pokazuje, co następuje:

- Tworzenie niestandardowego znaudera i fabryki kodera.

- Tworzenie elementu wiązania dla kodera niestandardowego.

- Przy użyciu konfiguracji wiązania niestandardowego do integracji elementów wiązania niestandardowego.

- Tworzenie niestandardowego programu obsługi konfiguracji, aby umożliwić konfigurację pliku niestandardowego elementu wiązania.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę

1. Zainstaluj ASP.NET 4.0 za pomocą następującego polecenia.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).

## <a name="message-encoder-factory-and-the-message-encoder"></a>Fabryka kodera wiadomości i koder wiadomości

Po <xref:System.ServiceModel.ServiceHost> otwarciu kanału klienta składnik czasu `CustomTextMessageBindingElement` projektowania `CustomTextMessageEncoderFactory`tworzy plik . Fabryka tworzy `CustomTextMessageEncoder`plik . Koder wiadomości działa zarówno w trybie przesyłania strumieniowego, jak i w trybie buforowanym. Używa <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio. W przeciwieństwie do zoptymalizowanych czytników XML i modułów zapisujących WCF, które obsługują tylko UTF-8, UTF-16 i big-endian Unicode, te czytniki i moduły zapisujące obsługują wszystkie kodowania obsługiwane przez platformę.

Poniższy przykład kodu pokazuje Koder CustomTextMessageEn.

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
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
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

W poniższym przykładzie kodu pokazano, jak utworzyć fabrykę kodera wiadomości.

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

## <a name="message-encoding-binding-element"></a>Element wiązania kodowania wiadomości

Elementy wiązania umożliwiają konfigurację stosu w czasie wykonywania WCF. Aby użyć kodera wiadomości niestandardowe w aplikacji WCF, element wiązania jest wymagane, który tworzy fabrykę kodera wiadomości z odpowiednimi ustawieniami na odpowiednim poziomie w stosie w czasie wykonywania.

Pochodzi `CustomTextMessageBindingElement` z klasy <xref:System.ServiceModel.Channels.BindingElement> podstawowej i dziedziczy z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy. Dzięki temu inne składniki WCF rozpoznać ten element wiązania jako element wiązania kodowania wiadomości. Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> zwraca wystąpienie pasujące fabryki kodera komunikatów z odpowiednimi ustawieniami.

Udostępnia `CustomTextMessageBindingElement` ustawienia dla `MessageVersion` `ContentType`, `Encoding` i za pośrednictwem właściwości. Koder obsługuje zarówno soap11Addressing i Soap12Addressing1 wersje. Wartość domyślna to Soap11Addressing1. Domyślną wartością `ContentType` jest "text/xml". Właściwość `Encoding` umożliwia ustawienie wartości kodowania żądanych znaków. Przykładowy klient i usługa używa kodowania znaków ISO-8859-1 (Latin1), które <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> nie jest obsługiwane przez WCF.

Poniższy kod pokazuje, jak programowo utworzyć powiązanie przy użyciu kodera niestandardowych wiadomości tekstowych.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Dodawanie obsługi metadanych do elementu wiązania kodowania wiadomości

Każdy typ, który <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> pochodzi od jest odpowiedzialny za aktualizowanie wersji powiązania PROTOKOŁU SOAP w dokumencie WSDL wygenerowanym dla usługi. Odbywa się to przez `ExportEndpoint` implementowanie <xref:System.ServiceModel.Description.IWsdlExportExtension> metody w interfejsie, a następnie modyfikowanie wygenerowanego WSDL. W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL z . `TextMessageEncodingBindingElement`

W tym przykładzie konfiguracja klienta jest ręcznie skonfigurowana. Nie można użyć programu Svcutil.exe do `CustomTextMessageBindingElement` wygenerowania konfiguracji klienta, ponieważ nie eksportuje potwierdzenia zasad w celu opisania jego zachowania. Ogólnie należy zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejs na niestandardowy element wiązania do eksportu potwierdzenia zasad niestandardowych, który opisuje zachowanie lub możliwości zaimplementowane przez element wiązania. Na przykład jak wyeksportować asercja zasad dla niestandardowego elementu wiązania, zobacz [Transport: Przykład UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)

## <a name="message-encoding-binding-configuration-handler"></a>Program obsługi konfiguracji powiązania kodowania komunikatów
W poprzedniej sekcji pokazano, jak programowo używać niestandardowego kodera wiadomości tekstowych. Implementuje `CustomTextMessageEncodingBindingSection` program obsługi konfiguracji, który pozwala określić użycie kodera niestandardowych wiadomości tekstowych w pliku konfiguracji. Klasa `CustomTextMessageEncodingBindingSection` pochodzi od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. Właściwość `BindingElementType` informuje system konfiguracji typu elementu wiązania do utworzenia dla tej sekcji.

Wszystkie ustawienia zdefiniowane `CustomTextMessageBindingElement` przez są widoczne jako `CustomTextMessageEncodingBindingSection`właściwości w . Asysty <xref:System.Configuration.ConfigurationPropertyAttribute> w mapowaniu atrybutów elementu konfiguracji do właściwości i ustawiania wartości domyślnych, jeśli atrybut nie jest ustawiony. Po wartości z konfiguracji są ładowane i stosowane do <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> właściwości typu, metoda jest wywoływana, która konwertuje właściwości na konkretne wystąpienie elementu wiązania.

Ten program obsługi konfiguracji mapuje do następującej reprezentacji w app.config lub Web.config dla usługi lub klienta.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

W przykładzie użyto kodowania ISO-8859-1.

Aby użyć tego programu obsługi konfiguracji musi być zarejestrowany przy użyciu następującego elementu konfiguracji.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
