---
title: 'Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: f492efe9e364195dce6b73a14e9ca5fa34a6df25
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972303"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF
Ten temat zawiera opis procedur migrowania podstawowej usługi ASP.NET AJAX do odpowiedniej usługi Windows Communication Foundation (WCF) z obsługą technologii AJAX. Pokazano, jak utworzyć funkcjonalnie odpowiednikową wersję programu WCF usługi ASP.NET AJAX. Te dwie usługi mogą być następnie używane obok siebie lub można użyć usługi WCF w celu zastąpienia usługi ASP.NET AJAX.

 Migrowanie istniejącej usługi ASP.NET AJAX do usługi WCF AJAX zapewnia następujące korzyści:

- Usługę AJAX można uwidocznić jako usługę SOAP przy minimalnej dodatkowej konfiguracji.

- Można korzystać z funkcji WCF, takich jak śledzenie i tak dalej.

 W poniższych procedurach założono, że używasz programu Visual Studio 2012.

 Kod, który wynika z procedur przedstawionych w tym temacie, znajduje się w przykładzie poniżej procedur.

 Aby uzyskać więcej informacji na temat uwidaczniania usługi WCF za pomocą punktu końcowego z obsługą [technologii AJAX, zobacz How to: Użyj konfiguracji, aby dodać temat punktu końcowego](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) AJAX ASP.NET.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Aby utworzyć i przetestować aplikację usługi sieci Web ASP.NET

1. Open Visual Studio 2012.

2. Z menu **plik** wybierz pozycję **Nowy**, a następnie pozycję **projekt**, **a następnie kliknij**pozycję **aplikacja usługi sieci Web ASP.NET**.

3. Nazwij projekt `ASPHello` , a następnie kliknij przycisk **OK**.

4. Usuń znaczniki komentarza z wiersza w pliku Service1.asmx.cs, `System.Web.Script.Services.ScriptService]` który zawiera, aby włączyć technologię AJAX dla tej usługi.

5. Z menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.

6. Z menu **Debuguj** wybierz polecenie **Uruchom bez debugowania**.

7. Na wygenerowanej stronie sieci Web wybierz `HelloWorld` operację.

8. Kliknij przycisk **Wywołaj** na `HelloWorld` stronie test. Powinna zostać wyświetlona następująca odpowiedź XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Ta odpowiedź potwierdza, że masz już działającą usługę ASP.NET AJAX i, w szczególności, że usługa została teraz uwidoczniona jako punkt końcowy w Service1. asmx/HelloWorld, który reaguje na żądania HTTP POST i zwraca kod XML.

     Teraz możesz przystąpić do konwersji tej usługi w taki sposób, aby korzystała z usługi WCF AJAX.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Aby utworzyć równoważną aplikację usługi WCF AJAX

1. Kliknij prawym przyciskiem myszy projekt **ASPHello** i wybierz polecenie **Dodaj**, a następnie pozycję **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX**.

2. Nazwij usługę `WCFHello` i kliknij przycisk **Dodaj**.

3. Otwórz plik WCFHello.svc.cs.

4. Z Service1.asmx.cs Skopiuj następującą implementację `HelloWorld` operacji.

    ```csharp
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5. Wklej do skopiowanej implementacji `HelloWorld` operacji do pliku WCFHello.svc.cs zamiast poniższego kodu.

    ```csharp
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6. `Namespace` Określ atrybut<xref:System.ServiceModel.ServiceContractAttribute> jako .`WCFHello`

    ```csharp
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7. Dodaj <xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> do operacji i ustaw właściwość do zwrócenia <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. `HelloWorld` Należy pamiętać, że jeśli nie zostanie ustawiona, domyślnym typem zwracanym jest <xref:System.ServiceModel.Web.WebMessageFormat.Json>.

    ```csharp
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8. Z menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.

9. Otwórz plik WCFHello. svc i z menu **Debuguj** wybierz polecenie **Start bez debugowania**.

10. Usługa udostępnia teraz punkt końcowy w lokalizacji `WCFHello.svc/HelloWorld`, który odpowiada na żądania HTTP POST. Nie można przetestować żądań POST protokołu HTTP z przeglądarki, ale punkt końcowy zwraca kod XML po kodzie XML.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld` Punktykońcowesą`Service1.aspx/HelloWorld` teraz równoważne funkcjonalnie.

## <a name="example"></a>Przykład
 Kod, który wynika z procedur przedstawionych w tym temacie, znajduje się w poniższym przykładzie.

```csharp
//This is the ASP.NET code in the Service1.asmx.cs file.

using System;
using System.Collections;
using System.ComponentModel;
using System.Data;
using System.Linq;
using System.Web;
using System.Web.Services;
using System.Web.Services.Protocols;
using System.Xml.Linq;
using System.Web.Script.Services;

namespace ASPHello
{
    /// <summary>
    /// Summary description for Service1.
    /// </summary>
    [WebService(Namespace = "http://tempuri.org/")]
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]
    [ToolboxItem(false)]
    // To allow this Web Service to be called from script, using ASP.NET AJAX, uncomment the following line.
    [System.Web.Script.Services.ScriptService]
    public class Service1 : System.Web.Services.WebService
    {

        [WebMethod]
        public string HelloWorld()
        {
            return "Hello World";
        }
    }
}

//This is the WCF code in the WCFHello.svc.cs file.
using System;
using System.Linq;
using System.Runtime.Serialization;
using System.ServiceModel;
using System.ServiceModel.Activation;
using System.ServiceModel.Web;

namespace ASPHello
{
    [ServiceContract(Namespace = "WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]
    public class WCFHello
    {
        // Add [WebInvoke] attribute to use HTTP GET.
        [OperationContract]
        [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
        public string HelloWorld()
        {
            return "Hello World";
        }

        // Add more operations here and mark them with [OperationContract].
    }
}
```

 Typ nie jest obsługiwany przez element, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ nie jest możliwy do <xref:System.Xml.Serialization.XmlSerializer>serializacji przez. <xref:System.Xml.XmlDocument> Zamiast tego można użyć dowolnego <xref:System.Xml.Linq.XDocument> typu. <xref:System.Xml.XmlDocument.DocumentElement%2A>

 Jeśli usługi sieci Web ASMX są uaktualniane i migrowane obok usług WCF, należy unikać mapowania dwóch typów na taką samą nazwę na kliencie. Powoduje to wyjątek w serializatorach, jeśli ten sam typ jest używany w <xref:System.Web.Services.WebMethodAttribute> <xref:System.ServiceModel.ServiceContractAttribute>i:

- Jeśli najpierw zostanie dodana usługa WCF, wywołanie metody w usłudze sieci Web ASMX powoduje wyjątek <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> , ponieważ definicja stylu WCF zamówienia na serwerze proxy ma pierwszeństwo.

- Jeśli najpierw zostanie dodana usługa sieci Web ASMX, Metoda wywoływania w usłudze WCF powoduje wyjątek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , ponieważ definicja stylu usługi sieci Web zamówienia na serwerze proxy ma pierwszeństwo.

 Istnieją znaczne różnice w zachowaniu między <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i ASP.NET AJAX. <xref:System.Web.Script.Serialization.JavaScriptSerializer> Na przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> reprezentuje słownik jako tablicę par klucz/wartość, natomiast ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> reprezentuje słownik jako rzeczywiste obiekty JSON. Poniżej znajduje się słownik przedstawiony w ASP.NET AJAX.

```csharp
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Ten słownik jest reprezentowany w obiektach JSON, jak pokazano na poniższej liście:

- [{"Key": "jeden", "value": 1}, {"Key": "dwa", "value": 2}] przez<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

- {"jeden": 1, "dwa": 2} przez ASP.NET AJAX<xref:System.Web.Script.Serialization.JavaScriptSerializer>

 Jest to bardziej wydajne w tym sensie, że może obsługiwać słowniki, w których typ klucza nie jest ciągiem <xref:System.Web.Script.Serialization.JavaScriptSerializer> , podczas gdy nie może. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Jednak ten drugi jest bardziej przyjazny dla kodu JSON.

 Znaczące różnice między tymi serializatorami zostały podsumowane w poniższej tabeli.

|Kategoria różnic|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Deserializacja pustego buforu (nowy bajt [0]) do <xref:System.Object> (lub <xref:System.Uri>lub innych klas).|SerializationException|wartość null|
|Serializacja<xref:System.DBNull.Value>|{}(lub {"__type": "#System"})|Null|
|Serializacja prywatnych składowych typów [Serializable].|serializowana|nie Zserializowano|
|Serializacja właściwości <xref:System.Runtime.Serialization.ISerializable> publicznych typów.|nie Zserializowano|serializowana|
|"Rozszerzenia" JSON|Jest zgodna ze specyfikacją JSON, która wymaga cudzysłowów w nazwach elementów członkowskich obiektu ({"a": "Hello"}).|Obsługuje nazwy elementów członkowskich obiektów bez cudzysłowów ({a: "Hello"}).|
|<xref:System.DateTime>Uniwersalny czas koordynowany (UTC)|Nie obsługuje formatu "\\/Date (123456789U)&#124;\\\\\\/" lub "\\/Date (\d{4}++(\\U (-[\d]))")\\ \\\\/)".|Obsługuje format "\\/Date (123456789U)\\/" i "\\/date\\(\d&#124;\\\\+{4}+(-[\d]))")\\ \\ /)\\"jako wartości DateTime.|
|Reprezentacja słowników|Tablica KeyValuePair\<K, V >, obsługuje typy kluczy, które nie są ciągami.|Jako rzeczywiste obiekty JSON — ale obsługuje tylko typy kluczy, które są ciągami.|
|Znaki ucieczki|Zawsze z ukośnikiem ucieczki (/); nigdy nie zezwala na anulowanie ucieczki nieprawidłowych znaków JSON, takich jak "\n".|Za pomocą znaku ucieczki (/) dla wartości typu DateTime.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Użyj konfiguracji, aby dodać punkt końcowy ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
