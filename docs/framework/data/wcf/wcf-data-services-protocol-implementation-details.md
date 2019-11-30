---
title: Szczegóły implementacji protokołu usługi danych WCF
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 5cd73caf848badc058c1f6df75973e1bb0a4fad4
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568769"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Szczegóły implementacji protokołu usługi danych WCF
## <a name="odata-protocol-implementation-details"></a>Szczegóły implementacji protokołu OData  
 Protokół Open Data Protocol (OData) wymaga, aby usługa danych implementująca protokół zapewniała określony minimalny zestaw funkcji. Te funkcje są opisane w dokumentach protokołu pod warunkiem "powinien" i "musi". Inne opcjonalne funkcje są opisane w "może". W tym temacie opisano te opcjonalne funkcje, które nie są obecnie zaimplementowane przez Usługi danych programu WCF. Aby uzyskać więcej informacji, zobacz [dokumentację protokołu OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Obsługa opcji zapytania $format  
 Protokół OData obsługuje notację JavaScript (JSON) i kanały informacyjne Atom, a usługa OData udostępnia opcję kwerendy systemu `$format`, aby umożliwić klientowi zażądanie formatu kanału informacyjnego odpowiedzi. Ta opcja kwerendy systemowej, jeśli jest obsługiwana przez usługę danych, musi zastąpić wartość nagłówka Accept żądania. Usługi danych programu WCF obsługuje Zwracanie danych JSON i Atom. Jednak implementacja domyślna nie obsługuje opcji zapytania `$format` i używa tylko wartości nagłówka Accept, aby określić format odpowiedzi. Istnieją przypadki, w których usługa danych może potrzebować obsługi opcji zapytania `$format`, na przykład gdy klienci nie mogą ustawić nagłówka Accept. Aby obsługiwać te scenariusze, należy rozłożyć usługę danych w celu obsługi tej opcji w identyfikatorze URI. Możesz dodać tę funkcję do usługi danych, pobierając [obsługę formatu JSONP i z obsługą adresu URL dla ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) przykładowego projektu z witryny sieci Web galerii kodu MSDN i dodając go do projektu usługi danych. Ten przykład umożliwia usunięcie opcji zapytania `$format` i zmianę nagłówka Accept na `application/json`. Po dołączeniu przykładowego projektu i dodanie `JSONPSupportBehaviorAttribute` do klasy usługi danych umożliwia obsługę `$format` `$format=json`opcji zapytania. Dalsze dostosowanie tego przykładowego projektu jest wymagane do obsługi `$format=atom` lub innych formatów niestandardowych.  
  
## <a name="wcf-data-services-behaviors"></a>Zachowania Usługi danych programu WCF  
 Następujące zachowania Usługi danych programu WCF nie są jawnie zdefiniowane przez Protokół OData:  
  
### <a name="default-sorting-behavior"></a>Domyślne zachowanie sortowania  
 Gdy żądanie zapytania wysyłane do usługi danych zawiera `$top` lub `$skip` opcji zapytania systemowego i nie obejmuje opcji kwerendy systemu `$orderby`, zwracane źródło danych jest sortowane według właściwości klucza w kolejności rosnącej. Wynika to z tego, że kolejność jest wymagana w celu zapewnienia poprawnego stronicowania wyników. W tym celu usługa danych dodaje do zapytania wyrażenie porządkowania. To zachowanie występuje również, gdy w usłudze danych jest włączone stronicowanie oparte na serwerze. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md). Aby sterować kolejnością zwracanego kanału informacyjnego, należy uwzględnić `$orderby` w identyfikatorze URI zapytania.  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
