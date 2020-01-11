---
title: Korzystanie z usługi danych w aplikacji klienckiej (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, getting started
ms.assetid: 90872d0c-e989-4490-b3e9-54afb10d33d4
ms.openlocfilehash: 41d3af831ff3c99e7f3000593db52d307d37ac38
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900908"
---
# <a name="using-a-data-service-in-a-client-application-wcf-data-services"></a>Korzystanie z usługi danych w aplikacji klienckiej (Usługi danych programu WCF)
Możesz uzyskać dostęp do usługi, która udostępnia kanał informacyjny protokołu Open Data Protocol (OData), dostarczając identyfikator URI do przeglądarki sieci Web. Identyfikator URI zapewnia adres zasobu, a komunikaty żądań są wysyłane na te adresy w celu uzyskania dostępu lub zmiany danych źródłowych, które reprezentuje zasób. Przeglądarka wysyła polecenie HTTP GET i zwraca żądany zasób jako źródło danych OData. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do usługi z przeglądarki sieci Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).  
  
 Mimo że przeglądarka sieci Web może być przydatna do testowania, że usługa OData zwraca oczekiwane dane, produkcyjne usługi OData, które umożliwiają również tworzenie, aktualizowanie i usuwanie danych, są zwykle używane przez kod aplikacji lub języki skryptów na stronie sieci Web. Ten temat zawiera omówienie sposobu uzyskiwania dostępu do źródeł danych OData z aplikacji klienckiej.  
  
## <a name="accessing-and-changing-data-using-rest-semantics"></a>Uzyskiwanie dostępu do danych i zmiana ich przy użyciu semantyki REST  
 Usługa OData pomaga zagwarantować współdziałanie między usługami, które uwidaczniają źródła danych OData i aplikacje korzystające ze źródeł danych OData. Aplikacje uzyskują dostęp do danych w usłudze opartej na protokole OData i je zmieniać, wysyłając komunikaty żądań określonej akcji HTTP i z identyfikatorem URI, który jest adresem zasobu jednostki, względem którego ma zostać wykonana akcja. Gdy muszą zostać dostarczone dane jednostki, są one dostarczane jako zaszyfrowane ładunki w treści wiadomości.  
  
### <a name="http-actions"></a>Akcje HTTP  
 Usługa OData obsługuje następujące akcje HTTP do wykonywania operacji tworzenia, odczytu, aktualizacji i usuwania na danych jednostki, które reprezentuje zasób:  
  
- **Http Get** — jest to domyślna akcja podczas uzyskiwania dostępu do zasobu z przeglądarki. W komunikacie żądania nie podano żadnego ładunku i zwracana jest metoda odpowiedzi z ładunkiem zawierającym żądane dane.  
  
- **Http post** — wstawia nowe dane jednostki do podanego zasobu. Dane, które mają zostać wstawione, są dostarczane w ładunku komunikatu żądania. Ładunek komunikatu odpowiedzi zawiera dane dla nowo utworzonej jednostki. Obejmuje to wszystkie automatycznie generowane wartości kluczy. Nagłówek zawiera również identyfikator URI, który odnosi się do nowego zasobu jednostki.  
  
- **Http Delete** — usuwa dane jednostki reprezentowane przez określony zasób. Ładunek nie występuje w wiadomościach żądania lub odpowiedzi.  
  
- **Http Put** — zastępuje istniejące dane jednostki w żądanym zasobie przy użyciu nowych danych, które są dostarczane w ładunku komunikatu żądania.  
  
- **Scalanie http** — ze względu na nieefektywność wykonywania operacji usuwania, po której następuje wstawienie w źródle danych, aby zmienić dane jednostki, usługa OData wprowadza nową akcję scalania http. Ładunek komunikatu żądania zawiera właściwości, które należy zmienić w założonym zasobie jednostki. Ponieważ SCALAnie HTTP nie jest zdefiniowane w specyfikacji protokołu HTTP, może wymagać dodatkowego przetwarzania do kierowania żądania scalania HTTP za pośrednictwem serwerów nieobsługujących protokołu OData.  
  
 Aby uzyskać więcej informacji, zobacz [OData: Operations](https://www.odata.org/documentation/odata-version-2-0/operations/).
  
### <a name="payload-formats"></a>Formaty ładunku  
 W przypadku żądania HTTP PUT, POST HTTP lub HTTP, ładunek komunikatu żądania zawiera dane jednostki wysyłane do usługi danych. Zawartość ładunku zależy od formatu danych wiadomości. Odpowiedzi HTTP na wszystkie akcje z wyjątkiem usuwania również zawierają takie ładunki. Usługa OData obsługuje następujące formaty ładunków do uzyskiwania dostępu do danych i zmiany ich w usłudze:  
  
- **Atom** — kodowanie komunikatów opartych na języku XML zdefiniowane przez funkcję OData jako rozszerzenie protokołu publikowania Atom (AtomPub) w celu umożliwienia wymiany danych za pośrednictwem protokołu HTTP dla kanałów informacyjnych sieci Web, podkastów, stron typu wiki i funkcji internetowych opartych na języku XML. Aby uzyskać więcej informacji, zobacz [Format OData: Atom](https://www.odata.org/documentation/odata-version-2-0/atom-format/).
  
- **JSON** -JavaScript Object Notation (JSON) jest lekkim formatem wymiany danych opartym na podzbiorze języka programowania JavaScript. Aby uzyskać więcej informacji, zobacz [Format OData: JSON](https://www.odata.org/documentation/odata-version-2-0/json-format/).
  
 W nagłówku komunikatu żądania HTTP jest żądany format komunikatu ładunku. Aby uzyskać więcej informacji, zobacz [OData: Operations](https://www.odata.org/documentation/odata-version-2-0/operations/).
  
## <a name="accessing-and-changing-data-using-client-libraries"></a>Uzyskiwanie dostępu do danych i zmiana ich przy użyciu bibliotek klienckich  
 Usługi danych programu WCF obejmuje biblioteki klienckie, które umożliwiają łatwiejsze korzystanie z kanału informacyjnego OData z .NET Framework i aplikacji klienckich opartych na technologii Silverlight. Te biblioteki upraszczają wysyłanie i otrzymywanie komunikatów HTTP. Tłumaczą one również ładunek komunikatów na obiekty CLR, które reprezentują dane jednostki. Biblioteki klienckie oferują dwie klasy podstawowe <xref:System.Data.Services.Client.DataServiceContext> i <xref:System.Data.Services.Client.DataServiceQuery%601>. Te klasy umożliwiają wykonywanie zapytań do usługi danych, a następnie współpracują z zwróconymi danymi jednostki jako obiektami CLR. Aby uzyskać więcej informacji, zobacz [usługi danych programu WCF biblioteki klienta](wcf-data-services-client-library.md) i [usługi danych programu WCF (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).  
  
 Możesz użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio, aby dodać odwołanie do usługi danych. To narzędzie żąda metadanych usługi z usługi danych, której dotyczy odwołanie, i generuje <xref:System.Data.Services.Client.DataServiceContext>, która reprezentuje usługę danych, a także generuje klasy usługi danych klienta reprezentujące jednostki. Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md).  
  
 Dostępne są biblioteki programistyczne, których można użyć do użycia źródła danych OData w innych rodzajach aplikacji klienckich. Aby uzyskać więcej informacji na temat zestawu OData SDK, zobacz [kod przykładowy usługi OData SDK](https://www.odata.org/ecosystem/#sdk).
  
## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do zasobów usługi danych](accessing-data-service-resources-wcf-data-services.md)
- [Szybki start](quickstart-wcf-data-services.md)
