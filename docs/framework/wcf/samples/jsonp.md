---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 6b5b42285539c2334bccaa04e1ba179d2cf0046c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183570"
---
# <a name="jsonp"></a>JSONP
W tym przykładzie pokazano, jak obsługiwać JSON z padding (JSONP) w usługach WCF REST. JSONP jest konwencją używaną do wywoływania skryptów między domenami przez generowanie tagów skryptów w bieżącym dokumencie. Wynik jest zwracany w określonej funkcji wywołania zwrotnego. JSONP opiera się na założeniu, `<script src="http://..." >` że tagi, takie jak można ocenić skrypty z dowolnej domeny i skrypt pobrany przez te tagi jest oceniane w zakresie, w którym inne funkcje mogą być już zdefiniowane.

## <a name="demonstrates"></a>Demonstracje
 Skrypty między domenami z JSONP.

## <a name="discussion"></a>Dyskusji
 Przykład zawiera stronę sieci Web, która dynamicznie dodaje blok skryptu po renderowaniu strony w przeglądarce. Ten blok skryptu wywołuje usługę WCF REST, która ma jedną operację, `GetCustomer`. Usługa WCF REST zwraca nazwę i adres klienta opakowane w nazwę funkcji wywołania zwrotnego. Gdy usługa WCF REST odpowiada, funkcja wywołania zwrotnego na stronie sieci Web jest wywoływana z danymi klienta, a funkcja wywołania zwrotnego wyświetla dane na stronie sieci Web. Iniekcja tagu skryptu i wykonanie funkcji wywołania zwrotnego jest automatycznie obsługiwane przez ASP.NET kontrolki AJAX ScriptManager. Wzorzec użycia jest taki sam jak w wszystkich ASP.NET serwerów proxy AJAX, z dodatkiem jednego wiersza, aby włączyć JSONP, jak pokazano w poniższym kodzie:

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 Strona sieci Web może wywołać usługę WCF <xref:System.ServiceModel.Description.WebScriptEndpoint> REST, ponieważ usługa używa z `crossDomainScriptAccessEnabled` zestawem do `true`. Obie te konfiguracje są wykonywane w pliku Web.config w ramach \<elementu system.serviceModel>.

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

 ScriptManager zarządza interakcji z usługą i ukrywa złożoność ręcznego implementowania dostępu JSONP. Po `crossDomainScriptAccessEnabled` ustawieniu `true` i format odpowiedzi dla operacji jest JSON, infrastruktura WCF sprawdza identyfikator URI żądania dla parametru ciągu zapytania wywołania zwrotnego i zawija odpowiedź JSON z wartością parametru ciągu zapytania wywołania zwrotnego. W przykładzie strona sieci Web wywołuje usługę WCF REST z następującym identyfikatorem URI.

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 Ponieważ parametr ciągu zapytania wywołania `JsonPCallback`zwrotnego ma wartość , usługa WCF zwraca odpowiedź JSONP pokazano w poniższym przykładzie.

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 Ta odpowiedź JSONP zawiera dane klienta sformatowane jako JSON, opakowane o nazwę funkcji wywołania zwrotnego, że strona sieci Web żądana. ScriptManager wykona to wywołanie zwrotne przy użyciu tagu skryptu do wykonania żądania między domenami, a następnie przekazać wynik do onSuccess obsługi, który został przekazany do GetCustomer operacji ASP.NET ajax proxy.

 Przykład składa się z dwóch ASP.NET aplikacji sieci web: jeden zawiera tylko usługę WCF, a drugi zawiera stronę sieci Web .aspx, która wywołuje usługę. Po uruchomieniu rozwiązania visual studio 2012 będzie hostować dwie witryny sieci Web na różnych portach, co tworzy środowisko, w którym usługa i klient działają w różnych domenach.

> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić próbkę  
  
1. Otwórz rozwiązanie dla próbki JSONP.  
  
2. Naciśnij klawisz F5, aby uruchomić go `http://localhost:26648/JSONPClientPage.aspx` w przeglądarce.  
  
3. Należy zauważyć, że po załadowaniu strony, wprowadzania tekstu dla "Nazwa" i "Adres" są wypełniane przez wartości.  Te wartości zostały dostarczone z wywołania do usługi WCF po zakończeniu renderowania strony przez przeglądarkę.
