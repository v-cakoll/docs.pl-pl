---
title: Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: f1185e7f8d455a59edf2b11e4e77ac6470d768fc
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43417341"
---
# <a name="wcf-web-http-programming-model-overview"></a>Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF
Model programowania protokołu HTTP sieci WEB Windows Communication Foundation (WCF) udostępnia podstawowe elementy, które są wymagane do kompilowania usług HTTP w sieci WEB z programem WCF. Usługi WCF WEB HTTP można uzyskać dostęp przez największą liczbę potencjalnych klientów, w tym przeglądarki sieci Web i ma następujące wymagania:  
  
-   **Identyfikatory URI i identyfikator URI przetwarzania** identyfikatorów URI odgrywają główną rolę w projekcie usługi sieci WEB HTTP. WCF WEB HTTP używa modelu programowania <xref:System.UriTemplate> i <xref:System.UriTemplateTable> klasy zapewniające możliwości przetwarzania identyfikatora URI.  
  
-   **Obsługa operacje GET i POST** usługi sieci WEB HTTP użytkowania zlecenie GET za pobieranie danych, oprócz różnych wywołania poleceń do modyfikacji danych i zdalnego wywoływania. WCF WEB HTTP używa modelu programowania <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> skojarzyć operacji usługi zarówno GET, jak i innych poleceń HTTP, takich jak PUT, POST i usuwania.  
  
-   **Wiele formatów danych** stylu sieci Web usług przetworzenia wielu rodzajów danych oprócz komunikaty protokołu SOAP. WCF WEB HTTP używa modelu programowania <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> do obsługi wielu formatów różnych danych, w tym dokumentów XML, obiekt danych JSON i strumieni zawartości binarnej, takie jak obrazy, pliki wideo lub zwykłego tekstu.  
  
 Model programowania protokołu HTTP sieci WEB WCF rozszerza zasięg usługi WCF do scenariuszy komunikacji między stylu sieci Web, które zawierają usług HTTP w sieci WEB, usług AJAX i JSON oraz (ATOM/RSS) zespolone kanały informacyjne. Aby uzyskać więcej informacji na temat usług AJAX i JSON, zobacz [JSON Obsługa integracji AJAX i](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Aby uzyskać więcej informacji na temat syndykacji zobacz [omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Istnieją dodatkowe ograniczenia na typy danych, które mogą być zwrócone z usługi sieci WEB HTTP. Dowolny typ możliwy do serializacji mogą być zwracane z operacji usługi sieci WEB HTTP. Ponieważ operacje usług sieci WEB HTTP może być wywołanie przez przeglądarkę sieci web, który istnieje ograniczenie na danych, jakie typy, które można określić w adresie URL. Aby uzyskać więcej informacji na temat typów są obsługiwane przez domyślny zobacz **adresy URL i parametry ciągu zapytania UriTemplate** poniższej sekcji. Zachowanie domyślne można zmienić, zapewniając Twojej własnej implementacji T:System.ServiceModel.Dispatcher.QueryStringConverter, który określa sposób konwertowania parametrów określonych w adresie URL na typ rzeczywistego parametru. Aby uzyskać więcej informacji zobacz <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Usługi napisane przy użyciu modelu programowania protokołu HTTP sieci WEB WCF nie należy używać komunikaty protokołu SOAP. Ponieważ protokołu SOAP nie są używane, nie można użyć funkcjach zabezpieczeń zapewnianych przez architekturę WCF. Można jednak użyć zabezpieczenia na poziomie transportu, udostępniając usługi przy użyciu protokołu HTTPS. Aby uzyskać więcej informacji na temat zabezpieczeń programu WCF zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Instalowanie rozszerzenia WebDAV dla usług IIS może spowodować usług HTTP w sieci Web do zwrócenia błędu HTTP 405 WebDAV rozszerzenia próbuje obsłużyć wszystkie żądania PUT. Aby obejść ten problem, można odinstalować rozszerzenie WebDAV lub wyłączyć rozszerzenie WebDAV dla witryny sieci web. Aby uzyskać więcej informacji, zobacz [usługi IIS i WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Identyfikator URI przetwarzania za pomocą klasy UriTemplate i UriTemplateTable  
 Identyfikator URI Szablony zapewniają efektywne składni dla wyrażania dużych zestawów strukturalnie podobne identyfikatorów URI. Na przykład następujący szablon określa zbiór identyfikatorów URI z wszystkich trzech segmentu, które zaczynają się od "a" i kończyć się znakiem "c" bez względu na wartość pośredni segmentu: / {segment} /c  
  
 Ten szablon zawiera opis identyfikatorów URI podobne do następującego:  
  
-   a/x/c  
  
-   a/y/c  
  
-   a/z/c  
  
-   i tak dalej.  
  
 W tym szablonie notacji nawias klamrowy ("{segment}") wskazuje segment zmiennej zamiast wartości literału.  
  
 .NET framework zapewnia interfejs API, Praca z szablonami URI nazywana <xref:System.UriTemplate>. `UriTemplates` Zezwalaj na wykonywanie następujących czynności:  
  
-   Można też wywołać jedną z `Bind` metody z zestawem parametrów do wygenerowania *pełni zamkniętego URI* który jest zgodny z szablonem. Oznacza to, że wszystkie zmienne w szablonie identyfikatora URI są zastępowane wartości rzeczywiste.  
  
-   Możesz wywołać `Match`() za pomocą kandydat identyfikatora URI, który używa szablonu, aby rozbić Release candidate, identyfikator URI do jego składnika części i zwraca słownik, który zawiera różne części identyfikatora URI etykietą zgodnie ze zmiennymi w szablonie.  
  
-   `Bind`() i `Match`() są inverses, dzięki czemu można wywołać `Match`( `Bind`(x)) i wróć za pomocą tego samego środowiska pracy z usługą.  
  
 Istnieje wiele razy (zwłaszcza na serwerze, gdy jest konieczne wysyła żądania do operacji usługi, w oparciu o identyfikator URI) chcesz śledzić zbiór <xref:System.UriTemplate> obiektów w strukturze danych, które można niezależnie dotyczą każdego zamkniętego Szablony. <xref:System.UriTemplateTable> reprezentuje zestaw szablonów identyfikatora URI, a następnie wybiera najlepsze dopasowanie, biorąc pod uwagę zestaw szablonów i Kandydat identyfikatora URI. To nie jest powiązany z określonego stosu sieciowego (dołączony do programu WCF) aby można było go używać wszędzie tam, gdzie to konieczne.  
  
 Model usług WCF sprawia, że użycie <xref:System.UriTemplate> i <xref:System.UriTemplateTable> do skojarzenia z operacji usługi ze zbiorem identyfikatorów URI opisanego przez <xref:System.UriTemplate>. Operacja usługi jest skojarzona z <xref:System.UriTemplate>, za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute>. Aby uzyskać więcej informacji na temat <xref:System.UriTemplate> i <xref:System.UriTemplateTable>, zobacz [klasy UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>WebGet i atrybuty WebInvoke  
 Usługi WCF WEB HTTP użytkowania pobierania czasowniki (na przykład HTTP GET) oprócz różnych wywołania czasowniki (na przykład żądania HTTP POST, PUT i DELETE). Model programowania protokołu HTTP sieci WEB WCF umożliwia deweloperom usługi kontroli zarówno szablon identyfikatora URI i zlecenie skojarzonych z ich operacji usługi za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> Zezwalaj na pobieranie pozwala kontrolować, jak poszczególne operacje powiązane z identyfikatorów URI i metod HTTP skojarzone z tych identyfikatorów URI. Na przykład dodanie <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> w poniższym kodzie.  
  
```  
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
  
 Powyższy kod umożliwia zapewnienie następujące żądania HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Wartość domyślna to POST, ale można go użyć do innych poleceń zbyt.  
  
```  
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
  
 Aby zobaczyć pełny przykład usługi WCF, która używa modelu programowania protokołu HTTP sieci WEB WCF, zobacz [porady: tworzenie podstawowa usługa HTTP w sieci Web WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Adresy URL i parametry ciągu zapytania UriTemplate  
 Usługi w stylu sieci Web można wywołać z przeglądarki sieci Web, wpisując adres URL, który jest skojarzony z operacji usługi. Te operacje usługi może potrwać parametry ciągu zapytania, które muszą być określone w postaci ciągu w adresie URL. W poniższej tabeli przedstawiono typy, które mogą być przekazywane w ramach adresu URL i format używany.  
  
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
|<xref:System.Single>|-3, 402823E38 - 3, 402823E38 (notacja wykładnika nie jest wymagane)|  
|<xref:System.Double>|-1, 79769313486232E308 - 1, 79769313486232E308 (notacja wykładnika nie jest wymagane)|  
|<xref:System.Char>|Dowolny pojedynczy znak|  
|<xref:System.Decimal>|Każdy znak dziesiętny w standardowej notacji (nie wykładnika)|  
|<xref:System.Boolean>|Wartość TRUE lub False (zamierzone, Zapisz nie liter)|  
|<xref:System.String>|Dowolny ciąg (wartość null ciąg nie jest obsługiwana i odbywa się nie anulowania zapewnianego element)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/RRRR HH: MM: [AM&AMP;#124;PM]<br /><br /> Miesiąc dzień roku<br /><br /> Miesiąc, dzień roku: mm: ss [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Gdzie DD = dni, HH = godziny, MM = minuty, SS = sekund|  
|<xref:System.Guid>|Identyfikator GUID, na przykład:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM/DD/RRRR HH: MM: MM: SS<br /><br /> Gdzie DD = dni, HH = godziny, MM = minuty, SS = sekund|  
|Wyliczenia|Wartość wyliczenia na przykład, który definiuje wyliczenie, jak pokazano w poniższym kodzie.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> W ciągu zapytania można określić jedną z wartości wyliczenia poszczególnych (lub odpowiadające im wartości liczby całkowitej).|  
|Typy, które mają `TypeConverterAttribute` , konwersji typu, do i z reprezentację ciągu znaków.|Zależy od konwertera typów.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formaty i modelu programowania protokołu HTTP sieci WEB WCF  
 Model programowania protokołu HTTP sieci WEB WCF oferuje nowe funkcje do pracy z wielu formatów danych. W warstwie powiązania <xref:System.ServiceModel.WebHttpBinding> mogą odczytywać i zapisywać różne rodzaje danych:  
  
-   XML  
  
-   JSON  
  
-   Strumienie binarne nieprzezroczyste  
  
 Oznacza to, model programowania protokołu HTTP sieci WEB WCF może obsłużyć dowolny typ danych, ale mogą programować przy <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] zapewnia obsługę dla danych JSON (technologia AJAX), a także zespolone kanały informacyjne (w tym ATOM i RSS). Aby uzyskać więcej informacji o tych funkcjach, zobacz [WCF Web HTTP formatowanie](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) i [JSON Obsługa integracji AJAX i](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Model programowania protokołu HTTP sieci WEB WCF i zabezpieczenia  
 Ponieważ model programowania protokołu HTTP sieci WEB WCF nie obsługuje protokołu WS-* protokołów, jest jedynym sposobem, aby zabezpieczyć usługi WCF WEB HTTP, aby uwidocznić usługę przy użyciu protokołu HTTPS przy użyciu protokołu SSL. Aby uzyskać więcej informacji o konfigurowaniu protokołu SSL za pomocą [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [Implementowanie protokołu SSL w usługach IIS](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Rozwiązywanie problemów z Model programowania protokołu HTTP sieci WEB WCF  
 Podczas wywoływania WCF WEB HTTP services przy użyciu <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> próba utworzenia kanału, <xref:System.ServiceModel.Description.WebHttpBehavior> używa <xref:System.ServiceModel.EndpointAddress> ustawione w pliku konfiguracji nawet jeśli inny <xref:System.ServiceModel.EndpointAddress> jest przekazywany do <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Zobacz też  
 [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
