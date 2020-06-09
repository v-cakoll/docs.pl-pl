---
title: 'Niestandardowy koder komunikatów: Niestandardowy koder tekstu'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: b60fa2a84520ad208d435a0c9284c19b5de8e989
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600610"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Niestandardowy koder komunikatów: Niestandardowy koder tekstu

W tym przykładzie przedstawiono sposób implementacji niestandardowego kodera komunikatów tekstowych przy użyciu Windows Communication Foundation (WCF).

> [!WARNING]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

W programie <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF obsługiwane są tylko kodowania UTF-8, UTF-16 i big-endian. Koder niestandardowej wiadomości tekstowej w tym przykładzie obsługuje wszystkie kodowania znaków obsługiwane przez platformę, które mogą być wymagane w celu współdziałania. Przykład składa się z programu konsoli klienta (exe), biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS) i biblioteki kodera wiadomości tekstowych (. dll). Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź. Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie). Klient wykonuje synchroniczne żądania do danej operacji matematycznej, a usługa zwraca wynik. Zarówno klient, jak i usługa używa `CustomTextMessageEncoder` zamiast domyślnego <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> .

Implementacja kodera niestandardowego składa się z fabryki kodera komunikatów, kodera komunikatów, elementu powiązania kodowania komunikatów i programu obsługi konfiguracji, a następnie ilustruje następujące kwestie:

- Kompilowanie kodera niestandardowego i fabryki kodera.

- Tworzenie elementu powiązania dla kodera niestandardowego.

- Używanie konfiguracji niestandardowego powiązania do integrowania niestandardowych elementów powiązania.

- Opracowywanie niestandardowego programu obsługi konfiguracji w celu zezwolenia na konfigurację pliku niestandardowego powiązania.

## <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

3. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

4. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

## <a name="message-encoder-factory-and-the-message-encoder"></a>Fabryka koderów komunikatów i koder komunikatów

Po <xref:System.ServiceModel.ServiceHost> otwarciu lub uruchomieniu kanału klienta składnik czasu projektowania `CustomTextMessageBindingElement` tworzy `CustomTextMessageEncoderFactory` . Fabryka tworzy `CustomTextMessageEncoder` . Koder komunikatów działa zarówno w trybie przesyłania strumieniowego, jak i w trybie buforowanym. Używa <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter> do odczytu i zapisu wiadomości odpowiednio. W przeciwieństwie do zoptymalizowanych czytników XML i autorów programu WCF, które obsługują tylko UTF-8, UTF-16 i big-endian Unicode, te czytelnicy i autorzy obsługują wszystkie kodowanie obsługiwane przez platformę.

Poniższy przykład kodu przedstawia CustomTextMessageEncoder.

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

Poniższy przykład kodu pokazuje, jak utworzyć fabrykę kodera komunikatów.

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

## <a name="message-encoding-binding-element"></a>Element powiązania kodowania komunikatów

Elementy powiązania umożliwiają konfigurację stosu wykonawczego programu WCF. Aby użyć niestandardowego kodera komunikatów w aplikacji WCF, wymagany jest element powiązania, który tworzy fabrykę kodera komunikatów z odpowiednimi ustawieniami na odpowiednim poziomie w stosie czasu wykonywania.

`CustomTextMessageBindingElement`Pochodzi z <xref:System.ServiceModel.Channels.BindingElement> klasy bazowej i dziedziczy z <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> klasy. Dzięki temu inne składniki usługi WCF mogą rozpoznać ten element powiązania jako element powiązania kodowania komunikatów. Implementacja <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> zwraca wystąpienie zgodnej fabryki kodera komunikatów z odpowiednimi ustawieniami.

`CustomTextMessageBindingElement`Uwidacznia ustawienia dla `MessageVersion` , `ContentType` i `Encoding` za pomocą właściwości. Koder obsługuje zarówno wersje Soap11Addressing, jak i Soap12Addressing1. Wartość domyślna to Soap11Addressing1. Wartość domyślna `ContentType` to "text/xml". `Encoding`Właściwość pozwala ustawić wartość kodowania żądanego znaku. Przykładowy klient i usługa używają kodowania znaków ISO-8859-1 (Latin1), które nie jest obsługiwane przez program <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.

Poniższy kod pokazuje, jak programowo utworzyć powiązanie przy użyciu niestandardowego kodera wiadomości tekstowych.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Dodawanie obsługi metadanych do elementu powiązania kodowania komunikatu

Każdy typ pochodzący od <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> jest odpowiedzialny za aktualizowanie wersji powiązania protokołu SOAP w dokumencie WSDL wygenerowanym dla usługi. Jest to realizowane przez implementację `ExportEndpoint` metody w <xref:System.ServiceModel.Description.IWsdlExportExtension> interfejsie, a następnie zmodyfikowanie wygenerowanego WSDL. W tym przykładzie `CustomTextMessageBindingElement` używa logiki eksportu WSDL z `TextMessageEncodingBindingElement` .

W tym przykładzie konfiguracja klienta jest konfigurowana ręcznie. Nie można użyć Svcutil. exe do wygenerowania konfiguracji klienta, ponieważ nie `CustomTextMessageBindingElement` eksportuje potwierdzenia zasad, aby opisać jego zachowanie. Należy zwykle zaimplementować <xref:System.ServiceModel.Description.IPolicyExportExtension> interfejs na elemencie powiązania niestandardowego, aby wyeksportować potwierdzenie zasad niestandardowych, który opisuje zachowanie lub możliwość implementowaną przez element powiązania. Aby zapoznać się z przykładem sposobu eksportowania potwierdzenia zasad dla elementu niestandardowego powiązania, zapoznaj się z przykładem [transport: UDP](transport-udp.md) .

## <a name="message-encoding-binding-configuration-handler"></a>Procedura obsługi konfiguracji powiązania kodowania komunikatów
W poprzedniej sekcji pokazano, jak programowo używać niestandardowego kodera wiadomości tekstowych. `CustomTextMessageEncodingBindingSection`Implementacja programu obsługi konfiguracji, która pozwala określić użycie niestandardowego kodera komunikatów tekstowych w pliku konfiguracji. `CustomTextMessageEncodingBindingSection`Klasa pochodzi od <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> klasy. `BindingElementType`Właściwość informuje system konfiguracji typu elementu powiązania, który ma zostać utworzony dla tej sekcji.

Wszystkie ustawienia zdefiniowane przez `CustomTextMessageBindingElement` są udostępniane jako właściwości w `CustomTextMessageEncodingBindingSection` . <xref:System.Configuration.ConfigurationPropertyAttribute>Pomaga w mapowaniu atrybutów elementu konfiguracji do właściwości i ustawiania wartości domyślnych, jeśli atrybut nie jest ustawiony. Po załadowaniu wartości z konfiguracji i zastosowaniu ich do właściwości typu <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> Metoda zostaje wywołana, co spowoduje konwersję właściwości w konkretnym wystąpieniu elementu powiązania.

Ta procedura obsługi konfiguracji mapuje do następującej reprezentacji w pliku App. config lub Web. config dla usługi lub klienta.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

Przykład używa kodowania ISO-8859-1.

Aby użyć tego programu obsługi konfiguracji, należy go zarejestrować przy użyciu następującego elementu konfiguracji.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
