---
title: Szczegóły implementacji protokołu usługi danych WCF
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 1d68e278fbac0137d1a5b2dca2daedba2294a7ee
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803850"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Szczegóły implementacji protokołu usługi danych WCF
## <a name="odata-protocol-implementation-details"></a>Szczegóły implementacji protokołu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Wymaga podania niektórych minimalny zestaw funkcjonalności usługi danych, który implementuje ten protokół. Te funkcje są opisane w dokumentacji protokołu pod względem "powinien" i "musisz". Inne opcjonalne funkcje jest opisywana w kategoriach "maja." W tym temacie opisano te opcjonalne funkcje, które nie są obecnie implementowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby uzyskać więcej informacji, zobacz [dokumentacji protokołu OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Obsługa opcji zapytania $format  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokół obsługuje zarówno w notacji JSON (JavaScript), jak i źródła danych Atom, i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zapewnia `$format` opcję zapytania systemu, aby umożliwić klientowi żądanie format odpowiedzi źródła danych. Tej opcji zapytania systemu, jeśli jest obsługiwany przez usługę danych muszą przesłaniać wartości nagłówka Accept żądania. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje zwracania kanały informacyjne Atom i JSON. Domyślna implementacja nie obsługuje jednak `$format` opcji zapytania i używa tylko wartości nagłówka Accept, aby określić format odpowiedzi. Istnieją przypadki, w przypadku usługi danych może być konieczne do obsługi `$format` zapytania opcją, np. gdy klienci nie można ustawić nagłówek Accept. Aby zapewnić obsługę tych scenariuszy, będzie konieczne rozszerzenie usługi danych w celu obsługi tej opcji w identyfikatorze URI. Można dodać tę funkcjonalność do usługi danych, pobierając [JSONP i kontrolowane przez adres URL format Obsługa architektury ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) przykładowego projektu z galerii kodu MSDN witryny sieci web i dodanie go do projektu usługi danych. W tym przykładzie usuwa `$format` opcji zapytania i zmieni się nagłówek Accept do `application/json`. Jeśli dołączysz próbki projektu i dodawanie `JSONPSupportBehaviorAttribute` danych klasy usługi umożliwia usłudze obsługę `$format` zapytania opcji `$format=json`. Dalsze dostosowywanie ten przykładowy projekt jest wymagany do obsługi również `$format=atom` lub innych niestandardowych formatów.  
  
## <a name="wcf-data-services-behaviors"></a>Zachowania usługi danych WCF  
 Następujące [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zachowania nie są jawnie definiowane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu:  
  
### <a name="default-sorting-behavior"></a>Domyślne zachowanie sortowania  
 Podczas żądania zapytania, które są wysyłane do usługi danych obejmuje `$top` lub `$skip` systemu opcji zapytania i nie obejmuje `$orderby` opcję zapytania systemu zwróconego źródła danych są posortowane według właściwości klucza, w kolejności rosnącej. Jest to spowodowane porządkowania jest wymagana, aby zapewnić poprawne stronicowania wyników. Aby to zrobić, Usługa danych dodaje szeregowania wyrażenia zapytania. To zachowanie występuje także w przypadku, gdy stronicowania opartych na serwerze jest włączone w usłudze danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Aby kontrolować kolejność zwróconego źródła danych, należy uwzględnić `$orderby` zapytania identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
