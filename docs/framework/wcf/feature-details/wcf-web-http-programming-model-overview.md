---
title: Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 9f2350b58e3cb33613ebc8e2c3cda1e234bcde25
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291748"
---
# <a name="wcf-web-http-programming-model-overview"></a>Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF
Model programowania HTTP web fundacji Windows Communication Foundation (WCF) zawiera podstawowe elementy wymagane do tworzenia usług HTTP w sieci WEB za pomocą WCF. Usługi WCF WEB HTTP są przeznaczone do uzyskiwania dostępu przez najszerszą gamę możliwych klientów, w tym przeglądarki sieci Web i mają następujące unikatowe wymagania:  
  
- **Identyfikatory URI i przetwarzanie identyfikatorów URI** Identyfikatory URI odgrywają kluczową rolę w projektowaniu usług WEB HTTP. Model programowania WCF WEB HTTP <xref:System.UriTemplate> <xref:System.UriTemplateTable> używa i klas, aby zapewnić możliwości przetwarzania identyfikatora URI.  
  
- **Obsługa operacji GET i POST** Usługi HTTP sieci WEB korzystają z zlecenia GET do pobierania danych, oprócz różnych zleceń wywoływania do modyfikacji danych i zdalnego wywoływania. Model programowania WCF WEB HTTP <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> używa i do kojarzenia operacji usługi z get i innych zleceń HTTP, takich jak PUT, POST i DELETE.  
  
- **Wiele formatów danych** Usługi w stylu sieci Web przetwarzają wiele rodzajów danych oprócz komunikatów PROTOKOŁU SOAP. Model programowania WCF WEB HTTP <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> używa i do obsługi wielu różnych formatów danych, w tym dokumentów XML, obiektu danych JSON i strumieni zawartości binarnej, takich jak obrazy, pliki wideo lub zwykły tekst.  
  
 Model programowania WCF WEB HTTP rozszerza zasięg WCF na scenariusze w stylu sieci Web, które obejmują usługi HTTP w sieci Web, usługi AJAX i JSON oraz źródła danych Syndication (ATOM/RSS). Aby uzyskać więcej informacji na temat usług AJAX i JSON, zobacz [Ajax Integration i JSON Support](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Aby uzyskać więcej informacji na temat syndykacji, zobacz [Przegląd syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Nie ma żadnych dodatkowych ograniczeń dotyczących typów danych, które mogą być zwracane z usługi HTTP sieci WEB. Każdy typ serializowalny można zwrócić z operacji usługi HTTP w sieci WEB. Ponieważ operacje usługi HTTP sieci WEB mogą być wywoływane przez przeglądarkę sieci Web, istnieje ograniczenie dotyczące typów danych, które można określić w adresie URL. Aby uzyskać więcej informacji na temat typów, które są domyślnie obsługiwane, zobacz sekcję **Parametry ciągu zapytania uritemplate i adresy URL** poniżej. Domyślne zachowanie można zmienić, udostępniając własną implementację T:System.ServiceModel.Dispatcher.QueryStringConverter, która określa sposób konwersji parametrów określonych w adresie URL na rzeczywisty typ parametru. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.Dispatcher.QueryStringConverter>.  
  
> [!CAUTION]
> Usługi napisane za pomocą modelu programowania HTTP WCF web nie używają komunikatów SOAP. Ponieważ funkcja SOAP nie jest używana, nie można używać funkcji zabezpieczeń dostarczonych przez WCF. Można jednak użyć zabezpieczeń opartych na transporcie, hostując usługę za pomocą protokołu HTTPS. Aby uzyskać więcej informacji na temat zabezpieczeń WCF, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
> Zainstalowanie rozszerzenia WebDAV dla usług IIS może spowodować, że usługi HTTP w sieci Web zwracają błąd HTTP 405, gdy rozszerzenie WebDAV próbuje obsłużyć wszystkie żądania PUT. Aby obejść ten problem, można odinstalować rozszerzenie WebDAV lub wyłączyć rozszerzenie WebDAV dla witryny sieci Web. Aby uzyskać więcej informacji, zobacz [usługi IIS i WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Przetwarzanie URI za pomocą uritemplate i uritemplatetable  
 Szablony identyfikatorów URI zapewniają wydajną składnię do wyrażania dużych zestawów strukturalnie podobnych identyfikatorów URI. Na przykład poniższy szablon wyraża zestaw wszystkich trzysegmentowych identyfikatorów URI, które zaczynają się od "a" i kończą na "c" bez względu na wartość segmentu pośredniego: a/{segment}/c  
  
 W tym szablonie opisano identyfikatory URI w następujący sposób:  
  
- a/x/c  
  
- r/c  
  
- a/z/c  
  
- i tak dalej.  
  
 W tym szablonie notacja nawiasów klamrowych ("{segment}") wskazuje segment zmiennej zamiast wartości literału.  
  
 .NET Framework udostępnia interfejs API do pracy <xref:System.UriTemplate>z szablonami URI o nazwie . `UriTemplates`umożliwiają następujące czynności:  
  
- Można wywołać jedną `Bind` z metod z zestawem parametrów, aby utworzyć *całkowicie zamknięty identyfikator URI,* który pasuje do szablonu. Oznacza to, że wszystkie zmienne w szablonie URI są zastępowane wartościami rzeczywistymi.  
  
- Można wywołać `Match`() z identyfikatorem URI kandydata, który używa szablonu do podziału identyfikatora URI kandydata na jego części składowe i zwraca słownik, który zawiera różne części identyfikatora URI oznaczone zgodnie ze zmiennymi w szablonie.  
  
- `Bind`() `Match`i () są odwrotnością, `Match`dzięki `Bind`czemu można zadzwonić ( ( x ) ) i wrócić z tym samym środowisku, które zaczęło się od.  
  
 Istnieje wiele razy (zwłaszcza na serwerze, gdzie wysyłanie żądania do operacji usługi na podstawie identyfikatora URI <xref:System.UriTemplate> jest konieczne), które chcesz śledzić zestaw obiektów w strukturze danych, które mogą niezależnie adres każdego z zawartych szablonów. <xref:System.UriTemplateTable>reprezentuje zestaw szablonów URI i wybiera najlepsze dopasowanie danego zestawu szablonów i identyfikatora URI kandydata. Nie jest to powiązane z żadnym stosem sieci (WCF w zestawie), dzięki czemu można go używać w razie potrzeby.  
  
 Model usługi WCF używa <xref:System.UriTemplate> <xref:System.UriTemplateTable> i do kojarzenia operacji usługi z zestawem <xref:System.UriTemplate>identyfikatorów URI opisanych przez . Operacja serwisowa jest skojarzona z <xref:System.UriTemplate>, <xref:System.ServiceModel.Web.WebGetAttribute> przy <xref:System.ServiceModel.Web.WebInvokeAttribute>użyciu lub . Aby uzyskać <xref:System.UriTemplate> więcej <xref:System.UriTemplateTable>informacji na temat i , zobacz [UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atrybuty WebGet i WebInvoke  
 Usługi WCF WEB HTTP korzystają z zleceń pobierania (na przykład HTTP GET) oprócz różnych zleceń invoke (na przykład HTTP POST, PUT i DELETE). Model programowania WCF WEB HTTP umożliwia deweloperom usług sterowanie zarówno szablonem URI, <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute>jak i zleceniem skojarzonym z ich operacjami usługi z i . I <xref:System.ServiceModel.Web.WebGetAttribute> umożliwiają <xref:System.ServiceModel.Web.WebInvokeAttribute> kontrolowanie sposobu, w jaki poszczególne operacje są powiązane z identyfikatorami URI i metodami HTTP skojarzonymi z tymi identyfikatorami URI. Na przykład <xref:System.ServiceModel.Web.WebGetAttribute> dodawanie <xref:System.ServiceModel.Web.WebInvokeAttribute> i w poniższym kodzie.  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 Powyższy kod umożliwia następujące żądania HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>domyślnie post, ale można go używać dla innych zleceń też.  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 Aby wyświetlić pełną próbkę usługi WCF korzystającej z modelu programowania HTTP WCF WEB, zobacz [Jak: Tworzenie podstawowej usługi HTTP w sieci WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Parametry ciągu zapytania uritemplate i adresy URL  
 Usługi w stylu sieci Web można wywołać z przeglądarki sieci Web, wpisując adres URL skojarzony z operacją usługi. Te operacje usługi mogą przyjmować parametry ciągu zapytania, które muszą być określone w formularzu ciągu w adresie URL. W poniższej tabeli przedstawiono typy, które można przekazać w obrębie adresu URL i używany format.  
  
|Typ|Format|  
|----------|------------|  
|<xref:System.Byte>|0 - 255|  
|<xref:System.SByte>|-128 - 127|  
|<xref:System.Int16>|-32768 - 32767|  
|<xref:System.Int32>|-2,147,483,648 - 2,147,483,647|  
|<xref:System.Int64>|-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807|  
|<xref:System.UInt16>|0 - 65535|  
|<xref:System.UInt32>|0 - 4,294,967,295|  
|<xref:System.UInt64>|0 - 18,446,744,073,709,551,615|  
|<xref:System.Single>|-3.402823e38 - 3.402823e38 (notacja wykładnicza nie jest wymagana)|  
|<xref:System.Double>|-1.79769313486232e308 - 1.79769313486232e308 (notacja wykładnicza nie jest wymagana)|  
|<xref:System.Char>|Dowolny pojedynczy znak|  
|<xref:System.Decimal>|Wszelkie miejsca dziesiętne w notacji standardowej (bez wykładnika)|  
|<xref:System.Boolean>|Prawda lub fałsz (bez uwzględniania wielkości liter)|  
|<xref:System.String>|Dowolny ciąg (ciąg null nie jest obsługiwany i nie jest wykonywana żadna ucieczka)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/YYYY HH:MM:SS [&#124;PM]<br /><br /> Miesiąc Dzień Rok<br /><br /> Miesiąc Dzień Rok HH:MM:SS [AM&#124;PM]|  
|<xref:System.TimeSpan>|Dd. Ss<br /><br /> Gdzie DD = dni, HH = godziny, MM = minuty, SS = sekundy|  
|<xref:System.Guid>|Identyfikator GUID, na przykład:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/YYYY HH:MM:SS MM:SS<br /><br /> Gdzie DD = dni, HH = godziny, MM = minuty, SS = sekundy|  
|Wyliczenia|Wartość wyliczenia na przykład, która definiuje wyliczenie, jak pokazano w poniższym kodzie.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> Dowolna z poszczególnych wartości wyliczenia (lub odpowiadające im wartości całkowite) może być określona w ciągu zapytania.|  
|Typy, `TypeConverterAttribute` które mają, które można przekonwertować typ do i z reprezentacji ciągu.|Zależy od konwertera typów.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formaty i model programowania HTTP WCF WEB  
 Model programowania WCF WEB HTTP ma nowe funkcje do pracy z wieloma różnymi formatami danych. W warstwie wiązania <xref:System.ServiceModel.WebHttpBinding> można odczytać i zapisać następujące różne rodzaje danych:  
  
- XML  
  
- JSON  
  
- Nieprzezroczyste strumienie binarne  
  
 Oznacza to, że model programowania WCF WEB HTTP może obsługiwać <xref:System.IO.Stream>dowolny typ danych, ale możesz być programowanie przeciwko .  
  
 .NET Framework 3.5 zapewnia obsługę danych JSON (AJAX) oraz źródeł danych Syndication (w tym ATOM i RSS). Aby uzyskać więcej informacji na temat tych funkcji, zobacz [Formatowanie http WCF w sieci Web,](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md) [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)oraz [Integracja AJAX i obsługa JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Model programowania I zabezpieczenia WCF WEB HTTP  

Ponieważ model programowania WCF WEB HTTP nie obsługuje protokołów WS-*, jedynym sposobem zabezpieczenia usługi WCF WEB HTTP jest udostępnienie usługi za pośrednictwem protokołu HTTPS przy użyciu protokołu SSL. Aby uzyskać więcej informacji na temat konfigurowania ssl z IIS 7.0, zobacz [Jak zaimplementować SSL w iIS](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Rozwiązywanie problemów z modelem programowania HTTP WCF WEB  
 Podczas wywoływania usług WCF <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> WEB HTTP przy <xref:System.ServiceModel.Description.WebHttpBehavior> użyciu <xref:System.ServiceModel.EndpointAddress> kanału, używa zestawu w <xref:System.ServiceModel.EndpointAddress> pliku konfiguracyjnym, nawet jeśli inny jest przekazywany do <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Zobacz też

- [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
- [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
