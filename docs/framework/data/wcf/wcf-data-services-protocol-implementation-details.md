---
title: Szczegóły implementacji protokołu usługi danych WCF
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 82218f1f8e14c9909d8b617c66b1f18a28e4dcee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363724"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Szczegóły implementacji protokołu usługi danych WCF
## <a name="odata-protocol-implementation-details"></a>Szczegóły implementacji protokołu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Wymaga podania niektórych minimalny zestaw funkcji usług danych, który implementuje ten protokół. Te funkcje są opisane w dokumentacji protokołu pod względem "powinien" i "musisz". Opisano inne opcjonalne funkcje w postaci "może." W tym temacie opisano te funkcje opcjonalne, które nie są obecnie implementowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby uzyskać więcej informacji, zobacz [dokumentacji protokołu OData](http://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Obsługa opcji zapytania $format  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokół obsługuje zarówno w notacji języka JavaScript (JSON), jak i źródła danych Atom, i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zapewnia `$format` systemu opcję zapytania, aby umożliwić klientowi żądanie format odpowiedzi źródła danych. Tej opcji zapytania system obsługiwane przez usługę danych musi zastąpić wartości nagłówka Accept żądania. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obsługuje zwracanie źródeł danych JSON i Atom. Domyślna implementacja nie obsługuje jednak `$format` opcji zapytania i używa tylko wartości nagłówka Accept do określenia format odpowiedzi. Istnieją przypadki, gdy usługi danych może być konieczne obsługuje `$format` opcji, takie jak kiedy klienci nie można ustawić nagłówek Accept zapytania. Do obsługi tych scenariuszy, będzie konieczne rozszerzenie usługi danych do obsługi tej opcji w identyfikatorze URI. Z usługą danych można dodać tę funkcję, pobierając [JSONP i kontrolowane przez adres URL format obsługę usług danych ADO.NET](http://go.microsoft.com/fwlink/?LinkId=208228) przykładowego projektu z galerii kodu MSDN witryny sieci web i dodanie go do projektu usługi danych. W tym przykładzie powoduje usunięcie `$format` opcji zapytania i zmieni nagłówka Accept do `application/json`. Jeśli dołączysz próbki projektu i dodaniu `JSONPSupportBehaviorAttribute` danych klasy usługi umożliwia usłudze obsługi `$format` opcji zapytania `$format=json`. Dalszego dostosowania tego projektu próbki jest wymagany do obsługi również `$format=atom` lub inne niestandardowe formaty.  
  
## <a name="wcf-data-services-behaviors"></a>Zachowania usługi danych WCF  
 Następujące [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zachowania nie są jawnie zdefiniowane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu:  
  
### <a name="default-sorting-behavior"></a>Domyślne zachowanie sortowania  
 Jeżeli zawiera żądanie zapytania, które są wysyłane do usługi data `$top` lub `$skip` systemu opcji zapytania i nie zawiera `$orderby` systemu opcji zapytania, zwracane źródła danych są sortowane według właściwości klucza w kolejności rosnącej. Jest to spowodowane porządkowania jest konieczne, aby zapewnić poprawne stronicowania wyników. Aby to zrobić, Usługa danych dodaje wyrażenie sortowania do zapytania. Ten problem występuje także w przypadku, gdy włączono stronicowania obsługiwanego przez serwer w usłudze danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Aby kontrolować kolejność zwracanych źródła danych, należy uwzględnić `$orderby` zapytania identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
