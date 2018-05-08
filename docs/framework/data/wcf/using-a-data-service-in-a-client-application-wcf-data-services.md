---
title: Usługi danych w aplikacji klienckiej (usługi danych WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: b25489de9a64ba4f1938e4d52c1cc677a218495b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Usługi danych w aplikacji klienckiej (usługi danych WCF)
Można uzyskać dostępu to usługa, która przedstawia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych, podając identyfikator URI do przeglądarki sieci Web. Identyfikator URI zawiera adres zasobu, a żądanie komunikaty są wysyłane do tych adresów na dostęp lub zmienić danych, który reprezentuje zasobu. W przeglądarce polecenia HTTP GET i zwraca wartość żądanego zasobu jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do usługi z przeglądarką sieci Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Mimo że przeglądarki sieci Web może być przydatna przy testowaniu, który [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługa zwraca oczekiwanych danych produkcyjnych [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usług, które umożliwiają także tworzyć, aktualizować i usuwać dane są zazwyczaj używane przez kod aplikacji lub skryptów języków na stronie sieci Web. W tym temacie omówiono sposób uzyskiwania dostępu do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych z aplikacji klienta.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Uzyskiwanie dostępu i zmienianie danych za pomocą semantyki REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pomaga zagwarantować współdziałanie usług, które udostępniają [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych i aplikacji, które wykorzystują [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych. Aplikacje dostępu i zmiany danych w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi przez wysyłanie komunikatów żądań określonej akcji HTTP i z identyfikatorem URI, który dotyczy zasobu jednostki, którą można wykonać akcji. Gdy należy podać dane jednostki, jest dostarczany jako zakodowany w szczególności ładunek w treści wiadomości.  
  
### <a name="http-actions"></a>Akcje HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje następujące akcje HTTP do wykonania tworzenia, odczytu, aktualizacji, a następnie usuń operacje na danych jednostki, reprezentujący zaadresowane zasobów:  
  
-   **HTTP GET** — jest to domyślne działanie, gdy zasób jest dostępny z poziomu przeglądarki. Ładunek jest dostarczany w komunikacie żądania, i zwróceniu metody odpowiedzi z ładunku, który zawiera żądanych danych.  
  
-   **HTTP POST** -wstawia nowe dane jednostki do dostarczonego zasobów. Aby wstawić dane są dostarczane w ładunku komunikatu żądania. Obciążenie komunikatu odpowiedzi zawiera dane dla nowo utworzonej jednostki. Obejmuje to wszystkie wartości klucza wygenerowana automatycznie. Nagłówek zawiera również identyfikator URI, który dotyczy nowego zasobu jednostki.  
  
-   **HTTP DELETE** — usuwa dane jednostki, które reprezentują określonego zasobu. Ładunku nie jest obecny w wiadomości żądania lub odpowiedzi.  
  
-   **HTTP PUT** — zastępuje istniejące dane jednostki na żądany zasób z nowymi danymi, które jest dostarczone w ładunku komunikatu żądania.  
  
-   **SCAL HTTP** — ze względu na wydajność podczas wykonywania delete, a następnie Wstaw w źródle danych tylko w celu zmiany danych jednostki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] wprowadza nową akcję scalania HTTP. Ładunek komunikatu żądania zawiera właściwości, które należy zmienić na zasobu zaadresowane jednostki. Ponieważ scalania HTTP nie jest zdefiniowany w specyfikacji HTTP, mogą wymagać dodatkowego przetwarzania można przekierować żądania HTTP scalania za pośrednictwem innego niż[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] pamiętać serwerów.  
  
 Aby uzyskać więcej informacji, zobacz [OData: operacje](http://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formaty ładunku  
 HTTP PUT, POST protokołu HTTP lub żądania HTTP scalania ładunku komunikatu żądania zawiera dane jednostki wysłać do usługi danych. Zawartość ładunku zależy od formatu danych wiadomości. Odpowiedzi HTTP do wszystkich akcji, z wyjątkiem usunąć również zawierać takie ładunku. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] obsługuje następujące formaty ładunku do uzyskiwania dostępu i zmiana danych z usługą:  
  
-   **Atom** -Kodowanie komunikatu opartych na języku XML, który jest zdefiniowany przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jako rozszerzenie Atom publikowania protokołu (AtomPub), aby umożliwić wymianę danych za pośrednictwem protokołu HTTP dla źródeł danych w sieci Web, podkasty, stron typu wiki oraz funkcje internetowe opartych na języku XML. Aby uzyskać więcej informacji, zobacz [OData: Atom Format](http://go.microsoft.com/fwlink/?LinkId=185794).  
  
-   **JSON** -JavaScript Object Notation (JSON) to format wymiany danych lekkie opartego na podzbiór języka programowania w języku JavaScript. Aby uzyskać więcej informacji, zobacz [OData: JSON Format](http://go.microsoft.com/fwlink/?LinkId=185795).  
  
 Format komunikatu ładunku żądania w nagłówku komunikatu żądania HTTP. Aby uzyskać więcej informacji, zobacz [OData: operacje](http://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Uzyskiwanie dostępu i zmiana danych przy użyciu bibliotek klienta  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obejmuje bibliotek klienta, które umożliwiają łatwiej wykorzystać [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła .NET Framework i aplikacje klienckie oparte na technologii Silverlight. Te biblioteki upraszczają wysyłanie i odbieranie wiadomości HTTP. Tłumaczenie one również ładunek komunikatu do obiektów CLR, które reprezentują danych jednostki. Dwa podstawowe klasy funkcji bibliotek klienckich <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601>. Te klasy umożliwiają zapytania usługi danych, a następnie pracować z danymi zwróconą jednostkę jako obiekty CLR. Aby uzyskać więcej informacji, zobacz [biblioteki klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) i [usługi danych WCF (platformy Silverlight)](http://msdn.microsoft.com/library/c0cd9f4b-1372-48e4-9935-c8421239da30).  
  
 Można użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio, aby dodać odwołania do usług danych. To narzędzie żądania metadanych usługi z usługą danych występujące w odwołaniu i generuje <xref:System.Data.Services.Client.DataServiceContext> który reprezentuje usługę danych, a także wygeneruje klasy usługi danych klienta, które reprezentują jednostek. Aby uzyskać więcej informacji, zobacz [generowania biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
 Są dostępne, której można korzystać z biblioteki programistyczne [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w innych rodzajach aplikacji klienckich. Aby uzyskać więcej informacji, zobacz [OData SDK](http://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do zasobów usługi danych](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
