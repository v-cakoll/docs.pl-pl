---
title: "Szczegóły implementacji protokołu usługi danych WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f5f723ddf5c81550661c6b96de77b35984b1eeb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Szczegóły implementacji protokołu usługi danych WCF
## <a name="odata-protocol-implementation-details"></a>Szczegóły implementacji protokołu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Wymaga podania niektórych minimalny zestaw funkcji usług danych, który implementuje ten protokół. Te funkcje są opisane w dokumentacji protokołu pod względem "powinien" i "musisz". Opisano inne opcjonalne funkcje w postaci "może." W tym temacie opisano te funkcje opcjonalne, które nie są obecnie implementowane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Aby uzyskać więcej informacji, zobacz [dokumentacji protokołu OData](http://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Obsługa opcji zapytania $format  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Protokół obsługuje zarówno w notacji języka JavaScript (JSON), jak i źródła danych Atom, i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zapewnia `$format` systemu opcję zapytania, aby umożliwić klientowi żądanie format odpowiedzi źródła danych. Tej opcji zapytania system obsługiwane przez usługę danych musi zastąpić wartości nagłówka Accept żądania. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje zwracanie źródeł danych JSON i Atom. Domyślna implementacja nie obsługuje jednak `$format` opcji zapytania i używa tylko wartości nagłówka Accept do określenia format odpowiedzi. Istnieją przypadki, gdy usługi danych może być konieczne obsługuje `$format` opcji, takie jak kiedy klienci nie można ustawić nagłówek Accept zapytania. Do obsługi tych scenariuszy, będzie konieczne rozszerzenie usługi danych do obsługi tej opcji w identyfikatorze URI. Z usługą danych można dodać tę funkcję, pobierając [JSONP i kontrolowane przez adres URL format obsługę usług danych ADO.NET](http://go.microsoft.com/fwlink/?LinkId=208228) przykładowego projektu z galerii kodu MSDN witryny sieci web i dodanie go do projektu usługi danych. W tym przykładzie powoduje usunięcie `$format` opcji zapytania i zmieni nagłówka Accept do `application/json`. Jeśli dołączysz próbki projektu i dodaniu `JSONPSupportBehaviorAttribute` danych klasy usługi umożliwia usłudze obsługi `$format` opcji zapytania `$format=json`. Dalszego dostosowania tego projektu próbki jest wymagany do obsługi również `$format=atom` lub inne niestandardowe formaty.  
  
## <a name="wcf-data-services-behaviors"></a>Zachowania usługi danych WCF  
 Następujące [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zachowania nie są jawnie zdefiniowane przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu:  
  
### <a name="default-sorting-behavior"></a>Domyślne zachowanie sortowania  
 Jeżeli zawiera żądanie zapytania, które są wysyłane do usługi data `$top` lub `$skip` systemu opcji zapytania i nie zawiera `$orderby` systemu opcji zapytania, zwracane źródła danych są sortowane według właściwości klucza w kolejności rosnącej. Jest to spowodowane porządkowania jest konieczne, aby zapewnić poprawne stronicowania wyników. Aby to zrobić, Usługa danych dodaje wyrażenie sortowania do zapytania. Ten problem występuje także w przypadku, gdy włączono stronicowania obsługiwanego przez serwer w usłudze danych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Aby kontrolować kolejność zwracanych źródła danych, należy uwzględnić `$orderby` zapytania identyfikatora URI.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
