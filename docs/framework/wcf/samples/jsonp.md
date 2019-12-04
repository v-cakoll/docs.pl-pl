---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 82fa0bb09ebdf3ca2325872c2b884f4940de17ed
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715723"
---
# <a name="jsonp"></a>JSONP
Ten przykład pokazuje, jak obsługiwać kod JSON z dopełnieniem (JSONP) w usługach WCF REST. JSONP to Konwencja używana do wywoływania skryptów międzydomenowych przez generowanie tagów skryptów w bieżącym dokumencie. Wynik jest zwracany w określonej funkcji wywołania zwrotnego. JSONP opiera się na koncepcji, że Tagi takie jak `<script src="http://..." >` mogą ocenić skrypty z dowolnej domeny, a skrypt pobrany przez te Tagi jest oceniany w zakresie, w którym inne funkcje mogą już być zdefiniowane.

## <a name="demonstrates"></a>Przedstawia
 Wykonywanie skryptów międzydomenowych z JSONP.

## <a name="discussion"></a>Dyskusji
 Przykład zawiera stronę sieci Web, która dynamicznie dodaje blok skryptu po wyrenderowaniu strony w przeglądarce. Ten blok skryptu wywołuje usługę WCF REST z pojedynczą operacją `GetCustomer`. Usługa WCF REST zwraca nazwę i adres klienta opakowane w nazwie funkcji wywołania zwrotnego. Gdy usługa REST WCF reaguje, funkcja wywołania zwrotnego na stronie sieci Web jest wywoływana z danymi klienta, a funkcja wywołania zwrotnego wyświetla dane na stronie sieci Web. Wstrzyknięcie znacznika skryptu i wykonywanie funkcji wywołania zwrotnego jest automatycznie obsługiwane przez kontrolkę ScriptManager ASP.NET AJAX. Wzorzec użycia jest taki sam jak w przypadku wszystkich serwerów proxy ASP.NET AJAX, z dodaniem jednej linii do włączenia JSONP, jak pokazano w poniższym kodzie:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Strona sieci Web może wywoływać usługę WCF REST, ponieważ usługa używa <xref:System.ServiceModel.Description.WebScriptEndpoint> z `crossDomainScriptAccessEnabled` ustawionym na `true`. Obie te konfiguracje są wykonywane w pliku Web. config w ramach elementu \<system. serviceModel >.

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

 Element ScriptManager zarządza interakcją z usługą i ukrywa złożoność ręcznej implementacji dostępu JSONP. Gdy `crossDomainScriptAccessEnabled` jest ustawiona na `true` i format odpowiedzi dla operacji to JSON, Infrastruktura WCF bada identyfikator URI żądania dla parametru ciągu zapytania wywołania zwrotnego i zawija odpowiedź JSON z wartością parametru ciągu zapytania wywołania zwrotnego. W przykładzie Strona sieci Web wywołuje usługę WCF REST z następującym identyfikatorem URI.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Ponieważ parametr ciągu zapytania wywołania zwrotnego ma wartość `JsonPCallback`, usługa WCF zwraca odpowiedź JSONP pokazaną w poniższym przykładzie.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Ta odpowiedź JSONP zawiera dane klienta sformatowane jako JSON, opakowane z nazwą funkcji wywołania zwrotnego żądaną przez stronę sieci Web. Obiekt ScriptManager wykona to wywołanie zwrotne przy użyciu tagu skryptu do wykonania żądania międzydomenowego, a następnie przekaże wynik do procedury obsługi onSuccess, która została przekazana do operacji GetCustomer serwera proxy ASP.NET AJAX.

 Przykład składa się z dwóch ASP.NET aplikacji sieci Web: jeden zawiera tylko usługę WCF, a drugi zawiera stronę sieci Web. aspx, która wywołuje usługę. W przypadku uruchamiania rozwiązania program Visual Studio 2012 będzie obsługiwał dwie witryny sieci Web na różnych portach, co tworzy środowisko, w którym usługa i klient znajdują się w różnych domenach.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1. Otwórz rozwiązanie dla przykładu JSONP.  
  
2. Naciśnij klawisz F5, aby uruchomić `http://localhost:26648/JSONPClientPage.aspx` w przeglądarce.  
  
3. Zwróć uwagę, że po załadowaniu strony dane wejściowe dla "name" i "Address" są wypełniane przez wartości.  Te wartości zostały przekazane z wywołania usługi WCF po zakończeniu renderowania strony przez przeglądarkę.
