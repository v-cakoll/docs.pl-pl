---
title: Używanie standardu JSONP
ms.date: 03/30/2017
ms.assetid: f386718c-b4ba-4931-a610-40c27a46672a
ms.openlocfilehash: 622fbdbf2674aea552cfd57f528d7cc5168cfda8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713489"
---
# <a name="using-jsonp"></a>Używanie standardu JSONP

Dopełnienie JSON (JSONP) to mechanizm, który umożliwia obsługę skryptów między witrynami w przeglądarkach sieci Web. JSONP został opracowany na możliwość ładowania skryptów z witryny innej niż bieżący załadować dokument został pobrany z przeglądarki sieci Web. Mechanizm polega na dopełnienie ładunek JSON z nazwą funkcji zdefiniowanych przez użytkownika wywołania zwrotnego, jak pokazano w poniższym przykładzie.

```javascript
callback({"a" = \\"b\\"});
```

W powyższym przykładzie ładunek JSON `{"a" = \\"b\\"}`, jest opakowana w wywołaniu funkcji `callback`. Funkcja wywołania zwrotnego musi być już zdefiniowane w bieżącej strony sieci Web. Typ zawartości odpowiedzi JSONP jest `application/javascript`.

JSONP nie jest automatycznie włączone. Aby ją włączyć, ustaw `javascriptCallbackEnabled` atrybutu `true` na jednym z standardowych punktów końcowych HTTP (<xref:System.ServiceModel.Description.WebHttpEndpoint> lub <xref:System.ServiceModel.Description.WebScriptEndpoint>), jak pokazano w poniższym przykładzie.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint name="" javascriptCallbackEnabled="true"/>
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Można określić nazwę funkcji wywołania zwrotnego w zmiennej zapytania o nazwie wywołania zwrotnego, jak pokazano w następującym adresem URL.

`http://baseaddress/Service/RestService?callback=functionName`

Wywołana usługa wysyła odpowiedź, jak pokazano poniżej.

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

W przypadku usługi przedstawionego wcześniej żądanie wygląda podobnie do poniższego.

`http://baseaddress/Service/RestService?$callback=anotherFunction`

Wywołana usługa odpowiada za pomocą następujących.

```javascript
anotherFunction ({"root":"Something"});
```

## <a name="http-status-codes"></a>Kody stanu HTTP

JSONP odpowiedzi z kodów stanu HTTP inne niż 200 obejmują drugim parametrem reprezentację liczbową kod stanu HTTP, jak pokazano w poniższym przykładzie.

```javascript
anotherFunction ({"root":"Something"}, 201);
```

## <a name="validations"></a>Liczba ocen

Następujące operacje sprawdzania poprawności są wykonywane, gdy format JSONP jest włączony:

- Infrastruktura WCF zgłasza wyjątek, jeśli `javascriptCallback` jest włączona, parametr ciągu zapytania wywołania zwrotnego jest obecne w żądaniu i format odpowiedzi jest ustawiona na format JSON.

- Jeśli żądanie zawiera parametr ciągu zapytania wywołania zwrotnego, ale ta operacja nie jest żądania HTTP GET, parametr wywołania zwrotnego jest ignorowany.

- Jeśli nazwa wywołania zwrotnego jest `null` lub pusty ciąg, w odpowiedzi nie jest sformatowany jako JSONP.

## <a name="see-also"></a>Zobacz także

- [Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
