---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 37da57a000376f972cd6da9e04be46ddec1b7144
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767542"
---
# <a name="jsonp"></a>JSONP
Niniejszy przykład pokazuje sposób obsługi formatu JSON przy użyciu dopełnienie (JSONP) w usługach REST programu WCF. JSONP jest Konwencji, używane do wywołania między domenami skryptów przez generowanie tagi skryptu w bieżącym dokumencie. Wynik jest zwracany dla funkcji określonego wywołania zwrotnego. JSONP opiera się na koncepcji, takich jak tagi `<script src="http://..." >` ocenić skryptów z dowolnej domeny, a skrypt pobierane przez tych znaczników jest szacowana w zakresie, w którym innych funkcji może być już zdefiniowane.

## <a name="demonstrates"></a>Demonstracje
 Między domenami korzystanie ze standardu JSONP skryptów.

## <a name="discussion"></a>Dyskusja
 Przykład obejmuje strony sieci Web, w której są dodawane dynamicznie bloku skryptu po stronie zostało wyrenderowane w przeglądarce. Ten blok skryptu wywołań usługi REST usługi WCF, która ma jedną operację `GetCustomer`. Usługa REST programu WCF zwraca nazwę i adres opakowane w nazwie funkcji wywołania zwrotnego klienta. Gdy usługa WCF REST odpowiada, funkcja wywołania zwrotnego na stronie sieci Web jest wywoływana z danymi klienta i funkcji wywołania zwrotnego wyświetla dane na stronie sieci Web. Iniekcja tag skryptu i wykonanie funkcji wywołania zwrotnego jest realizowane automatycznie przez formantu ScriptManager AJAX programu ASP.NET. Wzorzec użycia jest taki sam jak z wszystkich serwerów proxy ASP.NET AJAX, dodając jeden wiersz, aby umożliwić JSONP, jak pokazano w poniższym kodzie:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Strony sieci Web może wywołać usługi REST usługi WCF, ponieważ usługa używa <xref:System.ServiceModel.Description.WebScriptEndpoint> z `crossDomainScriptAccessEnabled` równa `true`. Obie te konfiguracje są wykonywane w pliku Web.config w obszarze \<system.serviceModel > element.

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 ScriptManager zarządza interakcję z usługą i natychmiast powoduje ukrycie złożoności ręcznie wykonawczych JSONP dostępu. Gdy `crossDomainScriptAccessEnabled` ustawiono `true` i format odpowiedzi dla operacji JSON, infrastruktura WCF sprawdza identyfikator URI żądania dla parametru ciągu zapytania wywołania zwrotnego i otacza odpowiedź JSON z wartością ciągu zapytania wywołania zwrotnego parametr. W tym przykładzie strony sieci Web wywołań usługi REST programu WCF za pomocą następujący identyfikator URI.

```
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Ponieważ parametr ciągu zapytania wywołanie zwrotne ma wartość `JsonPCallback`, usługi WCF, zwraca odpowiedź JSONP pokazano w poniższym przykładzie.

```
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Ta odpowiedź JSONP zawiera dane klienta w formacie JSON, ujęte w nawiasy nazwy funkcji wywołania zwrotnego, który zażądał strony sieci Web. ScriptManager wykonać to wywołanie zwrotne przy użyciu tagu skryptu do wykonania żądania między domenami, a następnie przekazać wynik do obsługi onSuccess, który został przekazany do operacji GetCustomer proxy ASP.NET AJAX.

 Przykład składa się z dwóch aplikacji sieci web programu ASP.NET: jedna z nich zawiera tylko usługi WCF, a inny zawiera strona sieci Web .aspx, który wywołuje usługę. Podczas uruchamiania rozwiązania, Visual Studio 2012 hostować dwie witryny sieci Web na innym, co powoduje utworzenie środowiska, miejsca zamieszkania usługi i klienta w różnych domenach.

> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. Otwórz rozwiązanie dla przykładu JSONP.  
  
2. Naciśnij klawisz F5, aby uruchomić `http://localhost:26648/JSONPClientPage.aspx` w przeglądarce.  
  
3. Należy zauważyć, że po załadowaniu strony danych wejściowych tekst "Name" i "Address" zostaną wypełnione wartościami.  Te wartości zostały dostarczone z wywołania do usługi WCF, po zakończeniu przeglądarki, renderowanie strony.
