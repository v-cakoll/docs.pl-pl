---
title: Używanie standardu JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 82290319b5d8b58708f0b2ebf40522ee76127b84
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594962"
---
# <a name="using-jsonp"></a>Używanie standardu JSONP

Uzupełnienie JSON (JSONP) to mechanizm, który umożliwia obsługę skryptów między lokacjami w przeglądarkach sieci Web. Funkcja JSONP została zaprojektowana z założenia, że przeglądarki sieci Web mają ładować skrypty z innej lokacji niż ta, z której został pobrany bieżący załadowany dokument. Mechanizm ten działa przez uzupełnienie ładunku JSON przez zdefiniowaną przez użytkownika nazwę funkcji wywołania zwrotnego, jak pokazano w poniższym przykładzie.

```javascript
callback({"a" = \\"b\\"});
```

W poprzednim przykładzie ładunek JSON `{"a" = \\"b\\"}` jest opakowany w wywołaniu funkcji `callback` . Funkcja wywołania zwrotnego musi już być zdefiniowana na bieżącej stronie sieci Web. Typ zawartości odpowiedzi JSONP to `application/javascript` .

JSONP nie jest automatycznie włączona. Aby je włączyć, należy ustawić `javascriptCallbackEnabled` atrybut na `true` jeden z standardowych punktów końcowych protokołu HTTP ( <xref:System.ServiceModel.Description.WebHttpEndpoint> lub <xref:System.ServiceModel.Description.WebScriptEndpoint> ), jak pokazano w poniższym przykładzie.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Nazwę funkcji wywołania zwrotnego można określić w zmiennej zapytania o nazwie callback, jak pokazano w poniższym adresie URL.

`http://baseaddress/Service/RestService?callback=functionName`

Po wywołaniu usługa wysyła odpowiedź podobną do następującej.

```javascript
functionName({"root":"Something"});
```  

Możesz również określić nazwę funkcji wywołania zwrotnego, stosując <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> do klasy usługi, jak pokazano w poniższym przykładzie.

```csharp
[ServiceContract]
[JavascriptCallbackBehavior(ParameterName = "$callback")]
public class Service1
{
    [OperationContract]
    [WebGet(ResponseFormat=WebMessageFormat.Json)]
    public string GetData()
    {
    }
}
```

W przypadku usługi pokazanej wcześniej żądanie wygląda następująco.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Po wywołaniu usługa reaguje na następujące polecenie.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Kody stanu HTTP

Odpowiedzi JSONP z kodami stanu HTTP innych niż 200 zawierają drugi parametr z reprezentacją liczbową kodu stanu HTTP, jak pokazano w poniższym przykładzie.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Weryfikacje

Następujące walidacji są wykonywane po włączeniu JSONP:

- Infrastruktura WCF zgłasza wyjątek `javascriptCallback` , jeśli jest włączona, w żądaniu jest obecny parametr ciągu zapytania wywołania zwrotnego, a format odpowiedzi jest ustawiony na wartość JSON.

- Jeśli żądanie zawiera parametr ciągu zapytania wywołania zwrotnego, ale operacja nie jest operacją HTTP GET, parametr wywołania zwrotnego jest ignorowany.

- Jeśli nazwa wywołania zwrotnego to `null` lub pusty ciąg, odpowiedź nie jest sformatowana jako JSONP.

## <a name="see-also"></a>Zobacz też

- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](wcf-web-http-programming-model-overview.md)
