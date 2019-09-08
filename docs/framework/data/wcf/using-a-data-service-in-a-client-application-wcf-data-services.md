---
title: Korzystanie z usługi danych w aplikacji klienckiej (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 050c1a67a367a6dd5175c535fe89fb0010ae8cbc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790283"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Korzystanie z usługi danych w aplikacji klienckiej (Usługi danych programu WCF)
Możesz uzyskać dostęp do usługi, która uwidacznia [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] kanał informacyjny, dostarczając identyfikator URI do przeglądarki sieci Web. Identyfikator URI zapewnia adres zasobu, a komunikaty żądań są wysyłane na te adresy w celu uzyskania dostępu lub zmiany danych źródłowych, które reprezentuje zasób. Przeglądarka wysyła polecenie HTTP GET i zwraca żądany zasób jako [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródło danych. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Mimo że przeglądarka sieci Web może być przydatna do testowania, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] że usługa zwraca oczekiwane dane, [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi produkcyjne, które umożliwiają również tworzenie, aktualizowanie i usuwanie danych są zwykle używane przez kod aplikacji lub języki skryptów na stronie sieci Web. Ten temat zawiera omówienie sposobu uzyskiwania dostępu [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] do źródeł danych z aplikacji klienckiej.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Uzyskiwanie dostępu do danych i zmiana ich przy użyciu semantyki REST  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]pomaga zagwarantować współdziałanie między usługami [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] , które uwidaczniają kanały [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informacyjne i aplikacje korzystające ze źródeł danych. Aplikacje uzyskują dostęp do danych w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]usłudze bazującej na nich i zmieniają je, wysyłając komunikaty żądań określonej akcji http i z identyfikatorem URI, który jest adresem zasobu jednostki, względem którego powinna zostać wykonana akcja. Gdy muszą zostać dostarczone dane jednostki, są one dostarczane jako zaszyfrowane ładunki w treści wiadomości.  
  
### <a name="http-actions"></a>Akcje HTTP  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Program obsługuje następujące akcje HTTP do wykonywania operacji tworzenia, odczytu, aktualizacji i usuwania na danych jednostki, które reprezentuje zasób:  
  
- **Http Get** — jest to domyślna akcja podczas uzyskiwania dostępu do zasobu z przeglądarki. W komunikacie żądania nie podano żadnego ładunku i zwracana jest metoda odpowiedzi z ładunkiem zawierającym żądane dane.  
  
- **Http post** — wstawia nowe dane jednostki do podanego zasobu. Dane, które mają zostać wstawione, są dostarczane w ładunku komunikatu żądania. Ładunek komunikatu odpowiedzi zawiera dane dla nowo utworzonej jednostki. Obejmuje to wszystkie automatycznie generowane wartości kluczy. Nagłówek zawiera również identyfikator URI, który odnosi się do nowego zasobu jednostki.  
  
- **Http Delete** — usuwa dane jednostki reprezentowane przez określony zasób. Ładunek nie występuje w wiadomościach żądania lub odpowiedzi.  
  
- **Http Put** — zastępuje istniejące dane jednostki w żądanym zasobie przy użyciu nowych danych, które są dostarczane w ładunku komunikatu żądania.  
  
- **Scalanie http** — ze względu na nieefektywność wykonywania operacji usuwania, po której następuje wstawienie w źródle danych, aby zmienić dane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] jednostki, wprowadzono nową akcję scalania http. Ładunek komunikatu żądania zawiera właściwości, które należy zmienić w założonym zasobie jednostki. Ponieważ scalanie http nie jest zdefiniowane w specyfikacji protokołu HTTP, może wymagać dodatkowego przetwarzania do kierowania żądania scalania HTTP za pośrednictwem serwerów[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] bez obsługi.  
  
 Aby uzyskać więcej informacji, [zobacz OData: Operacje](https://go.microsoft.com/fwlink/?LinkId=185792).  
  
### <a name="payload-formats"></a>Formaty ładunku  
 W przypadku żądania HTTP PUT, POST HTTP lub HTTP, ładunek komunikatu żądania zawiera dane jednostki wysyłane do usługi danych. Zawartość ładunku zależy od formatu danych wiadomości. Odpowiedzi HTTP na wszystkie akcje z wyjątkiem usuwania również zawierają takie ładunki. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]Program obsługuje następujące formaty ładunków do uzyskiwania dostępu do danych i zmieniania ich w usłudze:  
  
- **Atom** — kodowanie komunikatów opartych na języku XML, które jest [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zdefiniowane przez rozszerzenie protokołu wymiany Atom (AtomPub), aby umożliwić wymianę danych za pośrednictwem protokołu HTTP w przypadku źródeł internetowych, podkastów, stron typu wiki i funkcji internetowych opartych na języku XML. Aby uzyskać więcej informacji, [zobacz OData: Format](https://go.microsoft.com/fwlink/?LinkId=185794)Atom.  
  
- **JSON** -JavaScript Object Notation (JSON) jest lekkim formatem wymiany danych opartym na podzbiorze języka programowania JavaScript. Aby uzyskać więcej informacji, [zobacz OData: Format](https://go.microsoft.com/fwlink/?LinkId=185795)json.  
  
 W nagłówku komunikatu żądania HTTP jest żądany format komunikatu ładunku. Aby uzyskać więcej informacji, [zobacz OData: Operacje](https://go.microsoft.com/fwlink/?LinkID=185792).  
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Uzyskiwanie dostępu do danych i zmiana ich przy użyciu bibliotek klienckich  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera biblioteki klienckie, które umożliwiają łatwiejsze korzystanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z kanału informacyjnego z .NET Framework i aplikacji klienckich opartych na technologii Silverlight. Te biblioteki upraszczają wysyłanie i otrzymywanie komunikatów HTTP. Tłumaczą one również ładunek komunikatów na obiekty CLR, które reprezentują dane jednostki. Biblioteki klienckie są wyposażone w dwie klasy <xref:System.Data.Services.Client.DataServiceContext> podstawowe i. <xref:System.Data.Services.Client.DataServiceQuery%601> Te klasy umożliwiają wykonywanie zapytań do usługi danych, a następnie współpracują z zwróconymi danymi jednostki jako obiektami CLR. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF biblioteki klienta](wcf-data-services-client-library.md) i [usługi danych programu WCF (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Możesz użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio, aby dodać odwołanie do usługi danych. To narzędzie żąda metadanych usługi z usługi danych, której dotyczy odwołanie, i <xref:System.Data.Services.Client.DataServiceContext> generuje element reprezentujący usługę danych, a także generuje klasy usługi danych klienta, które reprezentują jednostki. Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md).  
  
 Dostępne są biblioteki programistyczne, których można użyć do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] użycia źródła danych w innych rodzajach aplikacji klienckich. Aby uzyskać więcej informacji, zobacz [zestaw SDK OData](https://go.microsoft.com/fwlink/?LinkId=185796).  
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do zasobów usługi danych](accessing-data-service-resources-wcf-data-services.md)
- [Szybki start](quickstart-wcf-data-services.md)
