---
title: Szczegóły implementacji protokołu usługi danych WCF
ms.date: 03/30/2017
ms.assetid: 712d689b-fada-4cbb-bcdb-d65a3ef83b4c
ms.openlocfilehash: 1cd4204d9e1626ac45bccf3954fdaf1c156af7f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779655"
---
# <a name="wcf-data-services-protocol-implementation-details"></a>Szczegóły implementacji protokołu usługi danych WCF
## <a name="odata-protocol-implementation-details"></a>Szczegóły implementacji protokołu OData  
 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Wymaga, aby usługa danych implementująca protokół zapewniała określony minimalny zestaw funkcji. Te funkcje są opisane w dokumentach protokołu pod warunkiem "powinien" i "musi". Inne opcjonalne funkcje są opisane w "może". W tym temacie opisano te opcjonalne funkcje, które nie są obecnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zaimplementowane przez program. Aby uzyskać więcej informacji, zobacz [dokumentację protokołu OData](https://go.microsoft.com/fwlink/?LinkID=184554).  
  
### <a name="support-for-the-format-query-option"></a>Obsługa opcji zapytania $format  
 Protokół obsługuje notację JavaScript (JSON) i kanały informacyjne Atom oraz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] udostępnia `$format` opcję zapytania systemowego, aby umożliwić klientowi zażądanie formatu kanału informacyjnego odpowiedzi. [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Ta opcja kwerendy systemowej, jeśli jest obsługiwana przez usługę danych, musi zastąpić wartość nagłówka Accept żądania. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje Zwracanie danych JSON i Atom. Jednak implementacja domyślna nie obsługuje `$format` opcji zapytania i używa tylko wartości nagłówka Accept, aby określić format odpowiedzi. Istnieją przypadki, w których usługa danych może potrzebować obsługi `$format` opcji zapytania, na przykład gdy klienci nie mogą ustawić nagłówka Accept. Aby obsługiwać te scenariusze, należy rozłożyć usługę danych w celu obsługi tej opcji w identyfikatorze URI. Możesz dodać tę funkcję do usługi danych, pobierając [obsługę formatu JSONP i z obsługą adresu URL dla ADO.NET Data Services](https://go.microsoft.com/fwlink/?LinkId=208228) przykładowego projektu z witryny sieci Web galerii kodu MSDN i dodając go do projektu usługi danych. Ten przykład umożliwia usunięcie `$format` opcji zapytania i zmianę nagłówka Accept na. `application/json` Po dołączeniu przykładowego projektu i dodanie `JSONPSupportBehaviorAttribute` do klasy usługi danych umożliwia `$format` obsługę opcji `$format=json`zapytania przez usługę. Dalsze dostosowanie tego przykładowego projektu jest wymagane do obsługi `$format=atom` lub innych formatów niestandardowych.  
  
## <a name="wcf-data-services-behaviors"></a>Zachowania Usługi danych programu WCF  
 Następujące [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zachowania nie są jawnie zdefiniowane [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] przez protokół:  
  
### <a name="default-sorting-behavior"></a>Domyślne zachowanie sortowania  
 Gdy żądanie zapytania wysyłane do usługi danych zawiera `$top` lub `$skip` opcja zapytania systemowego `$orderby` i nie obejmuje opcji zapytania systemowego, zwracane źródło jest sortowane według właściwości klucza w kolejności rosnącej. Wynika to z tego, że kolejność jest wymagana w celu zapewnienia poprawnego stronicowania wyników. W tym celu usługa danych dodaje do zapytania wyrażenie porządkowania. To zachowanie występuje również, gdy w usłudze danych jest włączone stronicowanie oparte na serwerze. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md). Aby sterować kolejnością zwracanego kanału informacyjnego, należy uwzględnić `$orderby` w identyfikatorze URI zapytania.  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
