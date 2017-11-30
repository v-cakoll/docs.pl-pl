---
title: "Używanie standardu JSONP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83160ce0574b19205c8fc866a02bc9c642c7acb7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-jsonp"></a>Używanie standardu JSONP

Dopełnienie JSON (JSONP) jest mechanizm, który umożliwia obsługę skryptów między witrynami w przeglądarkach sieci Web. Format JSONP jest zaprojektowana dla możliwość ładowanie skryptów z poziomu witryny innej niż załadować dokument został pobrany z przeglądarki sieci Web. Mechanizm działa przez ładunek JSON z nazwą funkcji zdefiniowanej przez użytkownika wywołania zwrotnego, jak pokazano w poniższym przykładzie.

```javascript
callback({"a" = \\"b\\"});
```

W powyższym przykładzie ładunek JSON `{"a" = \\"b\\"}`, jest ujęte w wywołaniu funkcji `callback`. Funkcja wywołania zwrotnego musi być już zdefiniowana w bieżącej strony sieci Web. Typ zawartości odpowiedzi JSONP jest `application/javascript`.

JSONP nie jest automatycznie włączone. Aby go włączyć, ustaw `javascriptCallbackEnabled` atrybutu `true` na jednym standardowych punktów końcowych HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> lub <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak pokazano w poniższym przykładzie.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Nazwa funkcji wywołania zwrotnego można określić w zmienną zapytania o nazwie wywołania zwrotnego, jak pokazano w następującym adresem URL.

`http://baseaddress/Service/RestService?callback=functionName`

Gdy została wywołana, usługa wysyła odpowiedź podobne do następujących.

```javascript
functionName({"root":"Something"});
```  

Można również określić nazwę funkcji wywołania zwrotnego, stosując <xref:System.ServiceModel.Web.JavascriptCallbackBehaviorAttribute> do klasy usługi, jak pokazano w poniższym przykładzie.

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

W usłudze przedstawione wcześniej żądanie wygląda następująco.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Gdy została wywołana, usługa odpowiada z następujących czynności.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Kody stanu HTTP

Odpowiedzi JSONP z kodów stanu HTTP innych niż 200 obejmują drugi parametr z reprezentację liczbową kod stanu HTTP, jak pokazano w poniższym przykładzie.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Sprawdzanie poprawności

Gdy format JSONP jest włączony, wykonywane są następujących sprawdzań poprawności:

- Infrastruktura WCF zgłasza wyjątek, jeśli `javascriptCallback` jest włączona, parametr ciągu zapytania wywołania zwrotnego jest obecne w żądaniu i format odpowiedzi jest ustawiona na format JSON.

- Jeśli żądanie zawiera parametr ciągu zapytania wywołania zwrotnego, ale ta operacja nie jest HTTP GET, parametr wywołania zwrotnego jest ignorowany.

- Jeśli nazwa wywołania zwrotnego jest `null` lub pusty ciąg odpowiedzi nie jest sformatowany jako JSONP.

## <a name="see-also"></a>Zobacz także

[Omówienie modelu programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
