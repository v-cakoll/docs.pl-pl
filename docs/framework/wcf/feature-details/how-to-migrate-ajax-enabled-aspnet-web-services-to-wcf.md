---
title: 'Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: dfbb32a751623fb1e3753cfd8bbbaf5910d571b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143003"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a>Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF
W tym temacie opisano procedury migracji podstawowej usługi ASP.NET AJAX do równoważne usługi obsługujące technologie AJAX Windows Communication Foundation (WCF). Widoczny jest sposób utworzyć funkcjonalnie równoważne wersję usługi ASP.NET AJAX WCF. Te dwie usługi mogą następnie służyć obok siebie lub usługi WCF umożliwia zastąpienie usługi ASP.NET AJAX.

 Migrowanie istniejących technologii ASP.NET AJAX Usługa do usługi WCF w technologii AJAX zapewnia następujące korzyści:

-   Usługa AJAX może narazić jako usługę protokołu SOAP z minimalną konfiguracją dodatkowe.

-   Korzystaj z funkcji usługi WCF, takie jak śledzenie i tak dalej.

 W poniższych procedurach założono, że używasz programu Visual Studio 2012.

 Kod, który jest wynikiem procedury opisane w tym temacie podano w przykładzie zamieszczonym procedur.

 Aby uzyskać więcej informacji na temat udostępniania usługi WCF, za pośrednictwem punktu końcowego z włączoną obsługą technologii AJAX, zobacz [jak: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tematu.

### <a name="to-create-and-test-the-aspnet-web-service-application"></a>Do tworzenia i testowania aplikacji usługi sieci Web platformy ASP.NET

1.  Open Visual Studio 2012.

2.  Z **pliku** menu, wybierz opcję **nowy**, następnie **projektu**, następnie **Web**, a następnie wybierz pozycję **aplikacji usługi sieci Web platformy ASP.NET** .

3.  Nadaj projektowi nazwę `ASPHello` i kliknij przycisk **OK**.

4.  Usuń znaczniki komentarza w pliku Service1.asmx.cs, który zawiera `System.Web.Script.Services.ScriptService]` umożliwiające AJAX dla tej usługi.

5.  Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

6.  Z **debugowania** menu, wybierz opcję **Rozpocznij bez debugowania**.

7.  Na stronie sieci Web, generowany wybierz `HelloWorld` operacji.

8.  Kliknij przycisk **Invoke** znajdujący się na `HelloWorld` strony testowej. Powinny pojawić się następujące odpowiedzi XML.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <string xmlns="http://tempuri.org/">Hello World</string>
    ```

9. Ta odpowiedź potwierdza, że teraz działa usługa ASP.NET AJAX i, w szczególności, że usługa ma teraz dostępne punktu końcowego w Service1.asmx/HelloWorld, który odpowiada na żądania HTTP POST żądania i zwraca XML.

     Teraz można przystąpić do przekonwertowania tej usługi do używania usługi WCF w technologii AJAX.

### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a>Aby utworzyć aplikację usługi równoważne WCF AJAX

1.  Kliknij prawym przyciskiem myszy **ASPHello** projektu, a następnie wybierz **Dodaj**, następnie **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX**.

2.  Nazwij usługę `WCFHello` i kliknij przycisk **Dodaj**.

3.  Otwórz plik WCFHello.svc.cs.

4.  Service1.asmx.cs, skopiuj następującą implementacją z `HelloWorld` operacji.

    ```
    public string HelloWorld()
    {
         return "Hello World";
    }
    ```

5.  Wklej skopiowany implementacji `HelloWorld` operacji na pliku WCFHello.svc.cs zamiast następujący kod.

    ```
    public void DoWork()
    {
          // Add your operation implementation here
          return;
    }
    ```

6.  Określ `Namespace` atrybutu dla <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.

    ```
    [ServiceContract(Namespace="WCFHello")]
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]
    public class WCFHello
    { … }
    ```

7.  Dodaj <xref:System.ServiceModel.Web.WebInvokeAttribute> do `HelloWorld` operacji i ustaw <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości do zwrócenia <xref:System.ServiceModel.Web.WebMessageFormat.Xml>. Należy pamiętać, że jeśli nie jest ustawiony domyślny typ zwracany jest <xref:System.ServiceModel.Web.WebMessageFormat.Json>.

    ```
    [OperationContract]
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]
    public string HelloWorld()
    {
        return "Hello World";
    }
    ```

8.  Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

9. Otwórz plik WCFHello.svc i **debugowania** menu, wybierz opcję **Rozpocznij bez debugowania**.

10. Usługa teraz udostępnia punkt końcowy w `WCFHello.svc/HelloWorld`, który odpowiada na żądania HTTP POST. Nie można przetestować żądań POST protokołu HTTP z przeglądarki, ale XML następujące XML zwracany przez punkt końcowy.

    ```xml
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>
    ```

11. `WCFHello.svc/HelloWorld` i `Service1.aspx/HelloWorld` punktów końcowych, teraz są funkcjonalnie równoważne.

## <a name="example"></a>Przykład
 Kod, który jest wynikiem procedury opisane w tym temacie znajduje się w następującym przykładzie.

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

 <xref:System.Xml.XmlDocument> Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ nie jest możliwy do serializacji, <xref:System.Xml.Serialization.XmlSerializer>. Można użyć dowolnego <xref:System.Xml.Linq.XDocument> wpisz lub serializacji <xref:System.Xml.XmlDocument.DocumentElement%2A> zamiast tego.

 Jeśli usługi sieci Web ASMX uaktualniania i migracji side-by-side do usług WCF, należy unikać mapowanie dwa typy do tej samej nazwie, na komputerze klienckim. To powoduje, że wyjątek w serializatory w przypadku używania tego samego typu w <xref:System.Web.Services.WebMethodAttribute> i <xref:System.ServiceModel.ServiceContractAttribute>:

-   Jeśli usługa WCF jest dodawany jako pierwsze, wywołania metody usługi sieci Web ASMX powoduje wyjątek w <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> ponieważ definicji stylu usług WCF zamówienia przez serwer proxy ma pierwszeństwo.

-   Jeśli usługa sieci Web ASMX zostanie dodany jako pierwsze, wywołanie metody WCF usługi powoduje, że wyjątek w <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ definicji stylu usług sieci Web zamówienia przez serwer proxy ma pierwszeństwo.

 Istnieją między nimi istotne różnice w zachowaniu między <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>. Na przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> reprezentuje słownik jako tablica par klucz wartość, natomiast ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> reprezentuje słownik jako rzeczywistych obiektów JSON. Dlatego następujące słownika reprezentowane w technologii ASP.NET AJAX.

```
Dictionary<string, int> d = new Dictionary<string, int>();
d.Add("one", 1);
d.Add("two", 2);
```

 Tego słownika jest reprezentowana w obiekty JSON, jak pokazano na poniższej liście:

-   [{"Key": "Jednego", "Value": 1}, {"Key": "Dwóch", "Value": 2}], <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>

-   {"jeden": 1 "dwa": 2}, ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>

 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Jest bardziej skuteczna, w tym sensie, że może obsługiwać słowników gdzie typ klucza nie jest ciągiem, gdy <xref:System.Web.Script.Serialization.JavaScriptSerializer> nie. Ale nie jest bardziej przyjaznego dla formatu JSON.

 Znaczne różnice między tymi serializatory podsumowano w poniższej tabeli.

|Kategoria różnice|DataContractJsonSerializer|ASP.NET AJAX JavaScriptSerializer|
|-----------------------------|--------------------------------|---------------------------------------|
|Podczas deserializacji pusty bufor (nowe byte[0]) do <xref:System.Object> (lub <xref:System.Uri>, lub niektóre inne klasy).|SerializationException|wartość null|
|Serializacja <xref:System.DBNull.Value>|{} (lub {"__type": "#System"})|Null|
|Serializacja prywatnych składowych typów [Serializable].|serializacji|nie serializacji|
|Serializacja publicznymi właściwościami <xref:System.Runtime.Serialization.ISerializable> typów.|nie serializacji|serializacji|
|"Rozszerzenia" JSON|Jest zgodna ze specyfikacją formatu JSON, co wymaga cudzysłowów wokół nazwy elementów członkowskich obiektu ({"": "hello"}).|Obsługuje nazwy elementów członkowskich obiektu, bez znaków cudzysłowu ({a: "hello"}).|
|<xref:System.DateTime> Uniwersalny czas koordynowany (UTC)|Nie obsługuje formatu "\\/Date(123456789U)\\/" lub "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".|Obsługuje format "\\/Date(123456789U)\\/" i "\\/Date\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "jako wartości daty/godziny.|
|Reprezentacja słowników|Tablica KeyValuePair\<K, V >, obsługuje typy kluczy, które nie są ciągami.|Jako rzeczywistych obiektów JSON — ale jedyne typy kluczy uchwyty, które są ciągami.|
|Znaki ucieczki|Zawsze za pomocą ucieczki ukośnika (/); nigdy nie umożliwia niezmieniony nieprawidłowe znaki JSON, takich jak "\n".|Za pomocą ucieczki ukośnika (/) dla wartości daty/godziny.|

## <a name="see-also"></a>Zobacz także

- [Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
