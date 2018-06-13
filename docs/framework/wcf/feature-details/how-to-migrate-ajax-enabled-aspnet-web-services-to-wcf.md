---
title: 'Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF'
ms.date: 03/30/2017
ms.assetid: 1428df4d-b18f-4e6d-bd4d-79ab3dd5147c
ms.openlocfilehash: 048408adf8678c243a225a233cb1173c9b7f869f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495554"
---
# <a name="how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf"></a><span data-ttu-id="b3135-102">Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF</span><span class="sxs-lookup"><span data-stu-id="b3135-102">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>
<span data-ttu-id="b3135-103">W tym temacie przedstawiono procedury migracji podstawowej usługi ASP.NET AJAX równoważne usługi z obsługą technologii AJAX Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b3135-103">This topic outlines procedures to migrate a basic ASP.NET AJAX service to an equivalent AJAX-enabled Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="b3135-104">Widoczny jest sposób utworzyć taką samą wersję usługi ASP.NET AJAX WCF.</span><span class="sxs-lookup"><span data-stu-id="b3135-104">It shows how to create a functionally equivalent WCF version of an ASP.NET AJAX service.</span></span> <span data-ttu-id="b3135-105">Te dwie usługi mogą być następnie używane obok siebie lub usługi WCF może być używany do zastąpienia usługi ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b3135-105">The two services can then be used side by side, or the WCF service can be used to replace the ASP.NET AJAX service.</span></span>  
  
 <span data-ttu-id="b3135-106">Migrowanie istniejących ASP.NET AJAX usługi z usługą WCF AJAX zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="b3135-106">Migrating an existing ASP.NET AJAX service to a WCF AJAX service gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="b3135-107">Usługa AJAX mogą uwidaczniać jako usługa SOAP z minimalną konfiguracją dodatkowe.</span><span class="sxs-lookup"><span data-stu-id="b3135-107">You can expose your AJAX service as a SOAP service with minimal extra configuration.</span></span>  
  
-   <span data-ttu-id="b3135-108">Korzystanie z funkcji WCF, takie jak śledzenie i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b3135-108">You can benefit from WCF features such as tracing, and so on.</span></span>  
  
 <span data-ttu-id="b3135-109">W poniższych procedurach założono, że używasz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3135-109">The following procedures assume that you are using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
 <span data-ttu-id="b3135-110">Kod, który jest wynikiem procedury opisane w tym temacie podano w przykładzie zamieszczonym procedur.</span><span class="sxs-lookup"><span data-stu-id="b3135-110">The code that results from the procedures outlined in this topic is provided in the example following the procedures.</span></span>  
  
 <span data-ttu-id="b3135-111">Aby uzyskać więcej informacji na temat udostępnianie usług WCF za pomocą punktu końcowego z włączoną obsługą technologii AJAX, zobacz [porady: Użyj konfiguracji można dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="b3135-111">For more information about exposing a WCF service through an AJAX-enabled endpoint, see the [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) topic.</span></span>  
  
### <a name="to-create-and-test-the-aspnet-web-service-application"></a><span data-ttu-id="b3135-112">Tworzenie i testowanie aplikacji usługi sieci Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b3135-112">To create and test the ASP.NET Web service application</span></span>  
  
1.  <span data-ttu-id="b3135-113">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b3135-113">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="b3135-114">Z **pliku** menu, wybierz opcję **nowy**, następnie **projektu**, następnie **sieci Web**, a następnie wybierz **aplikacji usługi sieci Web ASP.NET** .</span><span class="sxs-lookup"><span data-stu-id="b3135-114">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Service Application**.</span></span>  
  
3.  <span data-ttu-id="b3135-115">Nazwij projekt `ASPHello` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="b3135-115">Name the project `ASPHello` and click **OK**.</span></span>  
  
4.  <span data-ttu-id="b3135-116">Usuń znaczniki komentarza wiersza w pliku Service1.asmx.cs, który zawiera `System.Web.Script.Services.ScriptService]` umożliwiające AJAX dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="b3135-116">Uncomment the line in the Service1.asmx.cs file that contains `System.Web.Script.Services.ScriptService]` to enable AJAX for this service.</span></span>  
  
5.  <span data-ttu-id="b3135-117">Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b3135-117">From the **Build** menu, select **Build Solution**.</span></span>  
  
6.  <span data-ttu-id="b3135-118">Z **debugowania** menu, wybierz opcję **uruchomić bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="b3135-118">From the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
7.  <span data-ttu-id="b3135-119">Na stronie sieci Web wygenerowane, wybierz `HelloWorld` operacji.</span><span class="sxs-lookup"><span data-stu-id="b3135-119">On the Web page generated, select the `HelloWorld` operation.</span></span>  
  
8.  <span data-ttu-id="b3135-120">Kliknij przycisk **Invoke** znajdującego się na `HelloWorld` strony testowej.</span><span class="sxs-lookup"><span data-stu-id="b3135-120">Click the **Invoke** button on the `HelloWorld` test page.</span></span> <span data-ttu-id="b3135-121">Powinien zostać wyświetlony następujący odpowiedzi XML.</span><span class="sxs-lookup"><span data-stu-id="b3135-121">You should receive the following XML response.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <string xmlns="http://tempuri.org/">Hello World</string>  
    ```  
  
9. <span data-ttu-id="b3135-122">Ta odpowiedź potwierdza, że teraz działa usługa ASP.NET AJAX i, w szczególności, że usługa ma teraz widoczne punkt końcowy pod Service1.asmx/HelloWorld, który odpowiada na HTTP POST żądania i zwraca XML.</span><span class="sxs-lookup"><span data-stu-id="b3135-122">This response confirms that you now have a functioning ASP.NET AJAX service and, in particular, that the service has now exposed an endpoint at Service1.asmx/HelloWorld that responds to HTTP POST requests and returns XML.</span></span>  
  
     <span data-ttu-id="b3135-123">Teraz można przystąpić do przekonwertowania tej usługi do korzystania z usługi WCF w technologii AJAX.</span><span class="sxs-lookup"><span data-stu-id="b3135-123">Now you are ready to convert this service to use a WCF AJAX service.</span></span>  
  
### <a name="to-create-an-equivalent-wcf-ajax-service-application"></a><span data-ttu-id="b3135-124">Aby utworzyć aplikację usługi równoważne WCF AJAX</span><span class="sxs-lookup"><span data-stu-id="b3135-124">To create an equivalent WCF AJAX service application</span></span>  
  
1.  <span data-ttu-id="b3135-125">Kliknij prawym przyciskiem myszy **ASPHello** projekt i wybierz **Dodaj**, następnie **nowy element**, a następnie **usługi WCF z włączoną obsługą technologii AJAX**.</span><span class="sxs-lookup"><span data-stu-id="b3135-125">Right-click the **ASPHello** project and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="b3135-126">Nazwa usługi `WCFHello` i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="b3135-126">Name the service `WCFHello` and click **Add**.</span></span>  
  
3.  <span data-ttu-id="b3135-127">Otwórz plik WCFHello.svc.cs.</span><span class="sxs-lookup"><span data-stu-id="b3135-127">Open the WCFHello.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="b3135-128">Service1.asmx.cs, skopiuj następujące wykonania `HelloWorld` operacji.</span><span class="sxs-lookup"><span data-stu-id="b3135-128">From Service1.asmx.cs, copy the following implementation of the `HelloWorld` operation.</span></span>  
  
    ```  
    public string HelloWorld()  
    {  
         return "Hello World";  
    }  
    ```  
  
5.  <span data-ttu-id="b3135-129">Wklej skopiowane wdrażanie `HelloWorld` operacji do pliku WCFHello.svc.cs zamiast poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="b3135-129">Paste to copied implementation of the `HelloWorld` operation into the WCFHello.svc.cs file in place of the following code.</span></span>  
  
    ```  
    public void DoWork()  
    {  
          // Add your operation implementation here  
          return;  
    }  
    ```  
  
6.  <span data-ttu-id="b3135-130">Określ `Namespace` atrybutu dla <xref:System.ServiceModel.ServiceContractAttribute> jako `WCFHello`.</span><span class="sxs-lookup"><span data-stu-id="b3135-130">Specify the `Namespace` attribute for <xref:System.ServiceModel.ServiceContractAttribute> as `WCFHello`.</span></span>  
  
    ```  
    [ServiceContract(Namespace="WCFHello")]  
    [AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Required)]  
    public class WCFHello  
    { … }  
    ```  
  
7.  <span data-ttu-id="b3135-131">Dodaj <xref:System.ServiceModel.Web.WebInvokeAttribute> do `HelloWorld` operacji i zestawu <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości do zwrócenia <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span><span class="sxs-lookup"><span data-stu-id="b3135-131">Add the <xref:System.ServiceModel.Web.WebInvokeAttribute> to the `HelloWorld` operation and set the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> property to return <xref:System.ServiceModel.Web.WebMessageFormat.Xml>.</span></span> <span data-ttu-id="b3135-132">Należy pamiętać, że, jeśli nie jest ustawiony, domyślny typ zwracany jest <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="b3135-132">Note that, if not set, the default return type is <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span>  
  
    ```  
    [OperationContract]  
    [WebInvoke(ResponseFormat=WebMessageFormat.Xml)]  
    public string HelloWorld()  
    {  
        return "Hello World";  
    }  
    ```  
  
8.  <span data-ttu-id="b3135-133">Z **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b3135-133">From the **Build** menu, select **Build Solution**.</span></span>  
  
9. <span data-ttu-id="b3135-134">Otwórz plik WCFHello.svc i z **debugowania** menu, wybierz opcję **uruchomić bez debugowania**.</span><span class="sxs-lookup"><span data-stu-id="b3135-134">Open the WCFHello.svc file and from the **Debug** menu, select **Start Without Debugging**.</span></span>  
  
10. <span data-ttu-id="b3135-135">Usługa udostępnia teraz punkt końcowy pod `WCFHello.svc/HelloWorld`, która odpowiada na żądania HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b3135-135">The service now exposes an endpoint at `WCFHello.svc/HelloWorld`, which responds to HTTP POST requests.</span></span> <span data-ttu-id="b3135-136">Nie można przetestować żądania HTTP POST z przeglądarki, ale punkt końcowy zwraca XML po XML.</span><span class="sxs-lookup"><span data-stu-id="b3135-136">HTTP POST requests cannot be tested from the browser, but the endpoint returns XML following XML.</span></span>  
  
    ```xml  
    <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/">Hello World</string>  
    ```  
  
11. <span data-ttu-id="b3135-137">`WCFHello.svc/HelloWorld` i `Service1.aspx/HelloWorld` punkty końcowe są teraz taką samą funkcję.</span><span class="sxs-lookup"><span data-stu-id="b3135-137">The `WCFHello.svc/HelloWorld` and the `Service1.aspx/HelloWorld` endpoints are now functionally equivalent.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3135-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="b3135-138">Example</span></span>  
 <span data-ttu-id="b3135-139">Kod, który jest wynikiem procedury opisane w tym temacie podano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3135-139">The code that results from the procedures outlined in this topic is provided in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="b3135-140"><xref:System.Xml.XmlDocument> Typ nie jest obsługiwany przez <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> , ponieważ nie jest możliwy do serializacji przez <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b3135-140">The <xref:System.Xml.XmlDocument> type is not supported by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because it is not serializable by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="b3135-141">Możesz użyć dowolnej <xref:System.Xml.Linq.XDocument> wpisz lub serializować <xref:System.Xml.XmlDocument.DocumentElement%2A> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b3135-141">You can use either an <xref:System.Xml.Linq.XDocument> type, or serialize the <xref:System.Xml.XmlDocument.DocumentElement%2A> instead.</span></span>  
  
 <span data-ttu-id="b3135-142">Jeśli usługi sieci Web ASMX uaktualniania i migracji side-by-side do usługi WCF, należy unikać mapowania dwa typy do tej samej nazwie na kliencie.</span><span class="sxs-lookup"><span data-stu-id="b3135-142">If ASMX Web services are being upgraded and migrated side-by-side to WCF services, avoid mapping two types to the same name on the client.</span></span> <span data-ttu-id="b3135-143">Powoduje to, że wystąpił wyjątek w serializatorów w przypadku używania tego samego typu w <xref:System.Web.Services.WebMethodAttribute> i <xref:System.ServiceModel.ServiceContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="b3135-143">This causes an exception in serializers if the same type is used in a <xref:System.Web.Services.WebMethodAttribute> and a <xref:System.ServiceModel.ServiceContractAttribute>:</span></span>  
  
-   <span data-ttu-id="b3135-144">Jeśli usługa WCF zostanie dodany jako pierwszy, wywołanie metody usługi sieci Web ASMX powoduje, że wyjątek w <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> ponieważ definicji stylu WCF w kolejności serwer proxy ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="b3135-144">If WCF service is added first, invoking the method on ASMX Web Service causes exception in <xref:System.Web.UI.ObjectConverter.ConvertValue%28System.Object%2CSystem.Type%2CSystem.String%29> because the WCF style definition of the order in the proxy takes precedence.</span></span>  
  
-   <span data-ttu-id="b3135-145">Jeśli usługa sieci Web ASMX zostanie dodany jako pierwszy, wywoływanie metody dla usługi WCF powoduje, że wyjątek w <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ponieważ definicji stylu kolejności na serwerze proxy usługi sieci Web ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="b3135-145">If ASMX Web Service is added first, invoking method on WCF service causes exception in <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> because the Web Service style definition of the order in the proxy takes precedence.</span></span>  
  
 <span data-ttu-id="b3135-146">Są istotne różnice w zachowaniu między <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b3135-146">There are significant differences in behavior between the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> and the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer>.</span></span> <span data-ttu-id="b3135-147">Na przykład <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> reprezentuje słownik jako tablica par klucz/wartość, podczas gdy ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> reprezentuje słownik jako rzeczywisty obiektów JSON.</span><span class="sxs-lookup"><span data-stu-id="b3135-147">For example, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> represents a dictionary as an array of key/value pairs, whereas the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer> represents a dictionary as actual JSON objects.</span></span> <span data-ttu-id="b3135-148">Dlatego poniżej znajduje się słownik reprezentowane w technologii ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b3135-148">So the following is the dictionary represented in ASP.NET AJAX.</span></span>  
  
```  
Dictionary<string, int> d = new Dictionary<string, int>();  
d.Add("one", 1);  
d.Add("two", 2);  
```  
  
 <span data-ttu-id="b3135-149">Ten słownik jest reprezentowana w obiektów JSON, jak pokazano na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="b3135-149">This dictionary is represented in JSON objects as shown in the following list:</span></span>  
  
-   <span data-ttu-id="b3135-150">[{"Klucza": "Jeden", "Value": 1}, {"Klucza": "Dwa", "Value": 2}] według <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="b3135-150">[{"Key":"one","Value":1},{"Key":"two","Value":2}] by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span></span>  
  
-   <span data-ttu-id="b3135-151">{"jeden": 1, "dwa": 2} przez ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span><span class="sxs-lookup"><span data-stu-id="b3135-151">{"one":1,"two":2} by the ASP.NET AJAX <xref:System.Web.Script.Serialization.JavaScriptSerializer></span></span>  
  
 <span data-ttu-id="b3135-152"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Jest bardziej zaawansowanych, w tym sensie, że może obsługiwać słowniki gdzie typ klucza nie jest ciągiem, gdy <xref:System.Web.Script.Serialization.JavaScriptSerializer> nie.</span><span class="sxs-lookup"><span data-stu-id="b3135-152">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is more powerful in the sense that it can handle dictionaries where the key type is not string, while the <xref:System.Web.Script.Serialization.JavaScriptSerializer> cannot.</span></span> <span data-ttu-id="b3135-153">Ale nie jest bardziej przyjazny JSON.</span><span class="sxs-lookup"><span data-stu-id="b3135-153">But the latter is more JSON-friendly.</span></span>  
  
 <span data-ttu-id="b3135-154">Istotne różnice między tymi serializatorów podsumowano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b3135-154">The significant differences between these serializers are summarized in the following table.</span></span>  
  
|<span data-ttu-id="b3135-155">Kategoria różnic</span><span class="sxs-lookup"><span data-stu-id="b3135-155">Category of Differences</span></span>|<span data-ttu-id="b3135-156">Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="b3135-156">DataContractJsonSerializer</span></span>|<span data-ttu-id="b3135-157">ASP.NET AJAX JavaScriptSerializer</span><span class="sxs-lookup"><span data-stu-id="b3135-157">ASP.NET AJAX JavaScriptSerializer</span></span>|  
|-----------------------------|--------------------------------|---------------------------------------|  
|<span data-ttu-id="b3135-158">Podczas deserializacji pustego buforu (nowe byte[0]) do <xref:System.Object> (lub <xref:System.Uri>, lub niektóre inne klasy).</span><span class="sxs-lookup"><span data-stu-id="b3135-158">Deserializing the empty buffer (new byte[0]) into <xref:System.Object> (or <xref:System.Uri>, or some other classes).</span></span>|<span data-ttu-id="b3135-159">SerializationException</span><span class="sxs-lookup"><span data-stu-id="b3135-159">SerializationException</span></span>|<span data-ttu-id="b3135-160">null</span><span class="sxs-lookup"><span data-stu-id="b3135-160">null</span></span>|  
|<span data-ttu-id="b3135-161">Serializacja <xref:System.DBNull.Value></span><span class="sxs-lookup"><span data-stu-id="b3135-161">Serialization of <xref:System.DBNull.Value></span></span>|<span data-ttu-id="b3135-162">{} (lub {"__type": "#System"})</span><span class="sxs-lookup"><span data-stu-id="b3135-162">{} (or {"__type":"#System"})</span></span>|<span data-ttu-id="b3135-163">Null</span><span class="sxs-lookup"><span data-stu-id="b3135-163">Null</span></span>|  
|<span data-ttu-id="b3135-164">Serializacja prywatne elementy członkowskie typów [Serializable].</span><span class="sxs-lookup"><span data-stu-id="b3135-164">Serialization of the private members of [Serializable] types.</span></span>|<span data-ttu-id="b3135-165">serializowany</span><span class="sxs-lookup"><span data-stu-id="b3135-165">serialized</span></span>|<span data-ttu-id="b3135-166">nie serializacji</span><span class="sxs-lookup"><span data-stu-id="b3135-166">not serialized</span></span>|  
|<span data-ttu-id="b3135-167">Serializacja właściwości publicznej <xref:System.Runtime.Serialization.ISerializable> typów.</span><span class="sxs-lookup"><span data-stu-id="b3135-167">Serialization of the public properties of <xref:System.Runtime.Serialization.ISerializable> types.</span></span>|<span data-ttu-id="b3135-168">nie serializacji</span><span class="sxs-lookup"><span data-stu-id="b3135-168">not serialized</span></span>|<span data-ttu-id="b3135-169">serializowany</span><span class="sxs-lookup"><span data-stu-id="b3135-169">serialized</span></span>|  
|<span data-ttu-id="b3135-170">"Rozszerzenia" JSON</span><span class="sxs-lookup"><span data-stu-id="b3135-170">"Extensions" of JSON</span></span>|<span data-ttu-id="b3135-171">Jest zgodna ze specyfikacją JSON, co wymaga cudzysłowów wokół nazwy elementów członkowskich obiektu ({"": "tekst hello"}).</span><span class="sxs-lookup"><span data-stu-id="b3135-171">Adheres to the JSON specification, which requires quotes on object member names ({"a":"hello"}).</span></span>|<span data-ttu-id="b3135-172">Obsługuje nazwy elementów członkowskich obiektu bez cudzysłowów ({a: "tekst hello"}).</span><span class="sxs-lookup"><span data-stu-id="b3135-172">Supports the names of object members without quotes ({a:"hello"}).</span></span>|  
|<span data-ttu-id="b3135-173"><xref:System.DateTime> Uniwersalny czas koordynowany (UTC)</span><span class="sxs-lookup"><span data-stu-id="b3135-173"><xref:System.DateTime> Coordinated Universal Time (UTC)</span></span>|<span data-ttu-id="b3135-174">Nie obsługuje formatu "\\/Date(123456789U)\\/" lub "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\\\/)".</span><span class="sxs-lookup"><span data-stu-id="b3135-174">Does not support format "\\/Date(123456789U)\\/" or "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)".</span></span>|<span data-ttu-id="b3135-175">Obsługuje format "\\/Date(123456789U)\\/" i "\\/data\\(\d+ (U&#124;(\\+\\-[\d{4}]))?\\) \\ \\/) "jako wartości daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="b3135-175">Supports format "\\/Date(123456789U)\\/" and "\\/Date\\(\d+(U&#124;(\\+\\-[\d{4}]))?\\)\\\\/)" as DateTime values.</span></span>|  
|<span data-ttu-id="b3135-176">Reprezentacja słowników</span><span class="sxs-lookup"><span data-stu-id="b3135-176">Representation of dictionaries</span></span>|<span data-ttu-id="b3135-177">Tablica KeyValuePair\<K, V >, obsługuje typów kluczy, które nie są ciągami.</span><span class="sxs-lookup"><span data-stu-id="b3135-177">An array of KeyValuePair\<K,V>, handles key types that are not strings.</span></span>|<span data-ttu-id="b3135-178">Jako rzeczywisty obiektów JSON -, ale tylko typów kluczy dojść, które są ciągami.</span><span class="sxs-lookup"><span data-stu-id="b3135-178">As actual JSON objects - but only handles key types that are strings.</span></span>|  
|<span data-ttu-id="b3135-179">Znaki zmienionym</span><span class="sxs-lookup"><span data-stu-id="b3135-179">Escaped characters</span></span>|<span data-ttu-id="b3135-180">Zawsze z ucieczki ukośnika (/); nigdy nie umożliwia niezmieniony nieprawidłowe znaki JSON, takie jak "\n".</span><span class="sxs-lookup"><span data-stu-id="b3135-180">Always with an escape forward slash (/); never allows un-escaped invalid JSON characters, such as "\n".</span></span>|<span data-ttu-id="b3135-181">Z ucieczki ukośnika (/) dla wartości daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="b3135-181">With an escape forward slash (/) for DateTime values.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3135-182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3135-182">See Also</span></span>  
 [<span data-ttu-id="b3135-183">Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b3135-183">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
