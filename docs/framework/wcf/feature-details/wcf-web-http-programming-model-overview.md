---
title: Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
caps.latest.revision: 45
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f617aa68a052b60933db2dc4b2051c910af6b9b9
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-web-http-programming-model-overview"></a>Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Model programowania protokołu HTTP sieci WEB udostępnia podstawowe elementy wymagane do tworzenia usług HTTP w sieci WEB za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Usługi sieci WEB HTTP można uzyskać dostęp przez szeroki zakres możliwości klientów, w tym przeglądarki sieci Web i ma następujące wymagania:  
  
-   **Identyfikatory URI i przetwarzania URI** identyfikatorów URI odgrywają główną rolę w projekcie usługi sieci WEB HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Używa modelu programowania usług HTTP w sieci WEB <xref:System.UriTemplate> i <xref:System.UriTemplateTable> klasy możliwości przetwarzania identyfikatora URI.  
  
-   **Obsługa operacji GET i POST** usług HTTP sieci WEB upewnij wykorzystanie zlecenie GET do pobierania danych, oprócz różnych wywołania czasowniki modyfikacji danych i zdalnego wywoływania. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Używa modelu programowania usług HTTP w sieci WEB <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> skojarzyć operacji usługi zarówno GET i innych poleceń HTTP, takie jak PUT, POST i usuwania.  
  
-   **Wiele formatów danych** stylu sieci Web usług przetworzenia wielu rodzajów danych oprócz wiadomości SOAP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Używa modelu programowania usług HTTP w sieci WEB <xref:System.ServiceModel.WebHttpBinding> i <xref:System.ServiceModel.Description.WebHttpBehavior> do obsługi wielu formatów danych, w tym dokumentów XML, obiekt danych JSON i strumienie binarne zawartości, takich jak obrazy, pliki wideo lub zwykłego tekstu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programowania protokołu HTTP sieci WEB rozszerza zasięg [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] do stylu sieci Web obejmują scenariusze, w które obejmują usług HTTP sieci WEB, usług AJAX i JSON i źródła zespolonym (ATOM/RSS). Aby uzyskać więcej informacji o usługach technologii AJAX i JSON, zobacz [integracji AJAX i obsługi JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md). Aby uzyskać więcej informacji na temat zespolonego zobacz [omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md).  
  
 Nie ma żadnych dodatkowych ograniczeń typów danych, które mogą być zwrócone z usługi sieci WEB HTTP. Dowolny typ możliwy do serializacji mogą być zwracane z operacji usługi sieci WEB HTTP. Ponieważ operacje usługi sieci WEB HTTP można wywołać przez przeglądarkę sieci web, który istnieje ograniczenie na temat danych, można określić typy w adresie URL. Aby uzyskać więcej informacji o tym, jakie typy są obsługiwane domyślnie zobacz **adresy URL i parametrów ciągu zapytania elementu UriTemplate** poniższej sekcji. Domyślne zachowanie można zmienić, podając własne implementacji T:System.ServiceModel.Dispatcher.QueryStringConverter, który określa sposób konwertowania określone w adresie URL do typu rzeczywistego parametru parametry. Aby uzyskać więcej informacji zobacz <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
> [!CAUTION]
>  Napisany za pomocą usługi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania protokołu HTTP sieci WEB nie należy używać protokołu SOAP wiadomości. Ponieważ protokołu SOAP nie są używane, zabezpieczenia udostępniane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie można użyć. Można jednak używać zabezpieczenia na poziomie transportu, udostępniając usługi z protokołu HTTPS. Aby uzyskać więcej informacji na temat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń, zobacz [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
> [!WARNING]
>  Instalowanie usług IIS rozszerzenie WebDAV może spowodować usług HTTP sieci Web zwraca błąd HTTP 405 jako WebDAV rozszerzenia próbuje obsługuje wszystkie żądania PUT. Aby obejść ten problem, można odinstalować rozszerzenie WebDAV lub wyłączyć rozszerzenie WebDAV dla witryny sieci web. Aby uzyskać więcej informacji, zobacz [usług IIS i WebDav](http://learn.iis.net/page.aspx/357/webdav-for-iis-70/)  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a>Identyfikator URI przetwarzania za pomocą klasy UriTemplate i UriTemplateTable  
 Identyfikator URI Szablony stanowią wydajne składni wyrażenia dużych zestawów strukturę podobną identyfikatorów URI. Na przykład następujący szablon wyraża zestaw identyfikatorów URI wszystkie trzy segmentu zaczynać się od ciągu "" i kończyć się "c" niezależnie wartość segmentu pośredniego: / {segment} /c  
  
 Ten szablon zawiera opis identyfikatorów URI podobne do poniższych:  
  
-   a/x/c  
  
-   a/y/c  
  
-   a/z/c  
  
-   i tak dalej.  
  
 W tym szablonie notacji nawias klamrowy ("{segment}") wskazuje segment zmiennej zamiast wartości literału.  
  
 .NET framework zapewnia interfejs API, Praca z szablonami URI nazywana <xref:System.UriTemplate>. `UriTemplates` umożliwiają wykonywanie następujących czynności:  
  
-   Można wywołać elementu `Bind` metody z zestawem parametrów w celu utworzenia *pełni zamkniętego URI* który jest zgodny z szablonem. Oznacza to, że wszystkie zmienne w szablonie identyfikatora URI są zastępowane rzeczywistymi wartościami.  
  
-   Możesz wywołać `Match`() z kandydata identyfikatora URI, który używa szablonu podziału candidate identyfikator URI do jego składnika części i zwraca słownik, który zawiera różne części identyfikatora URI z etykietą zgodnie ze zmiennych w szablonie.  
  
-   `Bind`() i `Match`() są inverses, dzięki czemu można wywołać `Match`( `Bind`(x)), a następnie powrót z tym samym środowisku pracy z.  
  
 Istnieje wiele razy (zwłaszcza na serwerze, gdzie wysyła żądania do operacji usługi na podstawie identyfikatora URI jest niezbędne) mają do śledzenia zestaw <xref:System.UriTemplate> obiektów w strukturze danych, który można niezależnie dotyczą każdego zamkniętego Szablony. <xref:System.UriTemplateTable> reprezentuje zestaw szablonów identyfikatora URI i wybiera najlepsze dopasowanie, mając do dyspozycji zestaw szablonów i candidate identyfikatora URI. To nie jest powiązany z dowolnej określonej stos sieciowy ([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uwzględnione) dzięki czemu można go używać tam, gdzie jest to konieczne.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Modelu usługi sprawia, że użycie <xref:System.UriTemplate> i <xref:System.UriTemplateTable> do skojarzenia z zestawem opisanego przez identyfikatory URI operacji usługi <xref:System.UriTemplate>. Operacja usługi jest skojarzony z <xref:System.UriTemplate>, za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute>. Aby uzyskać więcej informacji na temat <xref:System.UriTemplate> i <xref:System.UriTemplateTable>, zobacz [UriTemplate i UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
  
## <a name="webget-and-webinvoke-attributes"></a>Atrybuty WebInvoke i WebGet  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Usługi sieci WEB HTTP należy użycie czasowników pobierania (na przykład HTTP GET) oprócz różnych wywołania zlecenia (na przykład HTTP POST, PUT i DELETE). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programowania protokołu HTTP sieci WEB umożliwia deweloperom usługi kontroli zarówno szablon identyfikatora URI i zlecenie skojarzonych z ich operacji usługi z <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute>. <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> Zezwalaj do kontrolowania poszczególnych operacji powiązane z identyfikatorów URI i metod HTTP skojarzone z tych identyfikatorów URI. Na przykład dodać <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> w poniższym kodzie.  
  
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
  
 Poprzedni kod umożliwia tworzenie następujących żądania HTTP.  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> Wartość domyślna to POST, ale może być używany dla innych zleceń za.  
  
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
  
 Aby wyświetlić pełny przykład [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która używa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania protokołu HTTP w sieci WEB, zobacz [porady: tworzenie podstawowa usługa HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a>Adresy URL i parametrów ciągu zapytania elementu UriTemplate  
 Usługi sieci Web stylu można wywołać z przeglądarki sieci Web, wpisując adres URL, który jest skojarzony z operacji usługi. Te operacje usługi może potrwać parametrów ciągu zapytania, które muszą być określone w formie ciągu w adresie URL. W poniższej tabeli przedstawiono typy, które mogą być przekazywane w ramach adresu URL i format używany.  
  
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
|<xref:System.Single>|-3, 402823E38 - 3, 402823E38 (notation wykładnika nie jest wymagana)|  
|<xref:System.Double>|-1, 79769313486232E308 - 1, 79769313486232E308 (notation wykładnika nie jest wymagana)|  
|<xref:System.Char>|Dowolny pojedynczy znak|  
|<xref:System.Decimal>|Wszelkie dziesiętnych w standardowej notacji (nie wykładnik)|  
|<xref:System.Boolean>|Wartość TRUE lub False (wielkość liter nie liter)|  
|<xref:System.String>|Dowolny ciąg (pusty ciąg nie jest obsługiwana i anulowania nie jest wykonywane)|  
|<xref:System.DateTime>|MM/DD/RRRR<br /><br /> MM/DD/RRRR GG [AM&AMP;#124;PM]<br /><br /> Miesiąc dzień roku<br /><br /> Miesiąc, dzień roku hh: mm: [AM&#124;PM]|  
|<xref:System.TimeSpan>|DD.HH:MM:SS<br /><br /> Gdzie DD = dni HH = godziny, MM = minut, a SS = sekund|  
|<xref:System.Guid>|Identyfikator GUID, na przykład:<br /><br /> 936DA01F-9ABD-4d9d-80C7-02AF85C822A8|  
|<xref:System.DateTimeOffset>|MM: SS MM/DD/RRRR GG<br /><br /> Gdzie DD = dni HH = godziny, MM = minut, a SS = sekund|  
|Wyliczenia|Wartość wyliczenia na przykład, który definiuje wyliczenie, jak pokazano w poniższym kodzie.<br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> W ciągu zapytania można określić jedną z wartości wyliczenia poszczególnych (lub odpowiadające im wartości Liczba całkowita).|  
|Typy, które mają `TypeConverterAttribute` który można przekonwertować typu do i z reprezentacji w postaci ciągu.|Zależy od typu konwertera.|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a>Formaty i modelu programowania protokołu HTTP sieci WEB WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programowania protokołu HTTP sieci WEB zawiera nowe funkcje do pracy z wielu formatów danych. W warstwie powiązania <xref:System.ServiceModel.WebHttpBinding> można odczytać i zapisać różne rodzaje danych:  
  
-   XML  
  
-   JSON  
  
-   Strumienie binarne nieprzezroczyste  
  
 Oznacza to, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania protokołu HTTP sieci WEB może obsługiwać dowolny rodzaj danych, ale użytkownik może być programowanie w odniesieniu do <xref:System.IO.Stream>.  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] zapewnia obsługę danych JSON (technologia AJAX) oraz zespolonego źródła danych (w tym ATOM i RSS). Aby uzyskać więcej informacji o tych funkcjach, zobacz [formatowania HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)[omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md) i [integracji AJAX i obsługi JSON](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md).  
  
## <a name="wcf-web-http-programming-model-and-security"></a>Model programowania protokołu HTTP sieci WEB WCF i zabezpieczenia  
 Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania protokołu HTTP sieci WEB nie obsługuje WS-* protokoły, jedynym sposobem zabezpieczenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa HTTP w sieci WEB jest do udostępnienia usługi za pośrednictwem protokołu HTTPS przy użyciu protokołu SSL. Aby uzyskać więcej informacji o konfigurowaniu protokołu SSL z [!INCLUDE[iisver](../../../../includes/iisver-md.md)], zobacz [Implementowanie protokołu SSL w usługach IIS](http://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a>Rozwiązywanie problemów z Model programowania protokołu HTTP sieci WEB WCF  
 Gdy protokołu HTTP sieci WEB WCF do wywoływania usług za pomocą <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> próba utworzenia kanału, <xref:System.ServiceModel.Description.WebHttpBehavior> używa <xref:System.ServiceModel.EndpointAddress> ustawiony w pliku konfiguracji, nawet gdy innej <xref:System.ServiceModel.EndpointAddress> jest przekazywana do <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.  
  
## <a name="see-also"></a>Zobacz też  
 [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 [Model obiektowy programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
