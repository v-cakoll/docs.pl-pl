---
title: Używanie usługi danych w aplikacji klienckiej (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: c2923a1940e3d58b6e3434f5b02edfb02995a202
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875316"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Używanie usługi danych w aplikacji klienckiej (WCF Data Services)
Uzyskaniem dostępu do usług, który udostępnia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanału informacyjnego, podając identyfikator URI do przeglądarki sieci Web. Identyfikator URI dostarcza adres zasobu, a żądania są wysyłane do tych adresów na dostęp lub zmienić danych bazowych, który reprezentuje zasobu. Przeglądarka wydaje polecenie HTTP GET i zwraca żądany zasób jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do usługi z przeglądarki sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Chociaż przeglądarki sieci Web może być przydatna przy testowaniu, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługa zwraca oczekiwanych danych produkcyjnych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usług, które umożliwiają również tworzenie, aktualizowanie i usuwanie danych zazwyczaj są używane przez kod aplikacji lub języków skryptów na stronie sieci Web. Ten temat zawiera omówienie sposobów dostępu do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych z aplikacji klienckiej.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Uzyskiwanie dostępu do i zmieniającymi się danymi przy użyciu semantyki REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pomaga zagwarantować współdziałanie między usługami, które uwidaczniają [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych i aplikacje używające [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aplikacje dostępu do danych i ich zmienianie w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]—, wysyłając komunikatów żądania określonych akcji HTTP i za pomocą identyfikatora URI, odnoszący się do zasobu jednostki, której można wykonać akcji na podstawie usługi. Gdy należy podać dane jednostki, jest podany w postaci specjalnie zakodowany ładunku w treści wiadomości.  
  
### <a name="http-actions"></a>Akcje HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje następujące akcje HTTP do wykonania, tworzenia, odczytu, aktualizowanie i usuwanie operacji na danych jednostki, które reprezentuje zaadresowane zasobów:  
  
- **HTTP GET** — jest to domyślne działanie, gdy zasób jest dostępny z poziomu przeglądarki. Ładunek jest dostarczany w komunikacie żądania, i jest zwracany przez metodę odpowiedzi z ładunkiem, który zawiera żądane dane.  
  
- **Żądania HTTP POST** -wstawia nowe dane jednostki do dostarczonego zasobu. Dane, które ma zostać wstawiony jest dostarczany w ładunku komunikatu żądania. Obciążenie komunikatu odpowiedzi zawiera dane dla nowo utworzonej jednostki. Obejmuje to wszystkie wartości klucza wygenerowany automatycznie. Nagłówek zawiera również identyfikator URI, odnoszący się do nowego zasobu jednostki.  
  
- **HTTP DELETE** -usuwa dane jednostki, która reprezentuje określonego zasobu. Ładunek nie jest obecny w komunikatów żądania lub odpowiedzi.  
  
- **HTTP PUT** — zastępuje istniejące dane jednostki w żądany zasób z nowymi danymi, która jest dostarczana w ładunku komunikatu żądania.  
  
- **SCAL HTTP** — ze względu na nieefektywność wykonywania delete, insert w źródle danych, aby zmienić dane jednostki, a następnie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] wprowadza nową akcję scalania HTTP. Ładunek komunikatu żądania zawiera właściwości, które musi zostać zmienione w zasobie jednostki zaadresowane. Ponieważ scalania HTTP nie jest zdefiniowana w specyfikacji protokołu HTTP, może wymagać dodatkowego przetwarzania, aby skierować żądanie SCALENIA HTTP za pośrednictwem non -[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pamiętać serwerów.  
  
 Aby uzyskać więcej informacji, zobacz [OData: Operacje](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formaty ładunków  
 HTTP PUT, POST protokołu HTTP lub HTTP scalania żądania ładunku komunikatu żądania zawiera dane jednostki, które możesz wysłać do usługi danych. Zawartość ładunek, zależy od formatu danych wiadomości. Odpowiedzi HTTP do wszystkich akcji, z wyjątkiem usuwania, również zawierać takie ładunku. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje następujące formaty ładunków do uzyskiwania dostępu i zmieniającymi się danymi w usłudze:  
  
- **Atom** — Kodowanie komunikatu opartych na języku XML, oznacza to zdefiniowane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jako rozszerzenie Atom publikowania protokół (AtomPub), aby umożliwić wymianę danych za pośrednictwem protokołu HTTP dla sieci Web źródła danych, transmisje podcast, strony typu wiki i funkcje internetowe oparte na języku XML. Aby uzyskać więcej informacji, zobacz [OData: Atom Format](https://go.microsoft.com/fwlink/?LinkId=185794).  
  
- **JSON** — JavaScript Object Notation (JSON) jest formatem wymiany uproszczone danych, który jest oparty na podzbiorze język programowania języka JavaScript. Aby uzyskać więcej informacji, zobacz [OData: JSON Format](https://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Format komunikatu ładunku żądania w nagłówku komunikatu żądania HTTP. Aby uzyskać więcej informacji, zobacz [OData: Operacje](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Uzyskiwanie dostępu do i zmieniającymi się danymi przy użyciu biblioteki klienta  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zawiera biblioteki klienckie, które umożliwiają łatwiejsze korzystanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Kanał informacyjny z .NET Framework i aplikacji klienckich opartych na technologii Silverlight. Te biblioteki upraszczają wysyłanie i odbieranie komunikatów HTTP. Mogą również wykonuje translację elementu ładunek komunikatu do obiektów CLR, które reprezentują dane jednostki. Biblioteki klienckie są wyposażone w dwóch głównych klas <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601>. Klasy te umożliwiają zapytań usługi danych, a następnie pracować z danymi zwróconą jednostkę jako obiekty typu CLR. Aby uzyskać więcej informacji, zobacz [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) i [usług danych WCF (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Możesz użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio, aby dodać odwołanie do usługi danych. To narzędzie żąda metadanych usługi z usługą danych występujące w odwołaniu i generuje <xref:System.Data.Services.Client.DataServiceContext> , reprezentuje usługę danych, a także generuje klas usługi danych klienta, które reprezentują jednostki. Aby uzyskać więcej informacji, zobacz [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Brak biblioteki programistyczne, które są dostępne, której można używać [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w innych rodzajów aplikacji klienckich. Aby uzyskać więcej informacji, zobacz [OData SDK](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
