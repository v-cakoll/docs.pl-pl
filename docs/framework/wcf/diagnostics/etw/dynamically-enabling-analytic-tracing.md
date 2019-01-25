---
title: Dynamiczne włączanie śledzenia danych analitycznych
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 42d238c704910c2406eb580c2ce102e5e84ed0f7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54719992"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamiczne włączanie śledzenia danych analitycznych
Za pomocą narzędzia, które są dostarczane z systemem operacyjnym Windows, można włączyć lub wyłączyć śledzenie dynamicznie przy użyciu śledzenie zdarzeń dla Windows (ETW). Dla wszystkich [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] usług Windows Communication Foundation (WCF), może być śledzenie danych analitycznych, włączone i wyłączone dynamicznie bez modyfikowania pliku Web.config aplikacji i ponowne uruchomienie usługi. Umożliwia to aplikacji, który emituje zdarzenia śledzenia, aby zachować prawidłowe.  
  
 W podobny sposób można skonfigurować opcje śledzenia WCF. Na przykład można zmienić poziom ważności z **błąd** do **informacji** bez zakłócania działania aplikacji. Można to zrobić za pomocą następujących narzędzi:  
  
-   **Logman** — narzędzie wiersza polecenia do konfigurowania, kontrolowanie i wykonywanie zapytań o dane śledzenia. Aby uzyskać więcej informacji, zobacz [Logman tworzyć śledzenia](https://go.microsoft.com/fwlink/?LinkId=165426) i [śledzenia aktualizacji Logman](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Informacje w Podglądzie zdarzeń** — Windows graficzne narzędzie do zarządzania w celu wyświetlania wyników śledzenia. Aby uzyskać więcej informacji, zobacz [usługi WCF i zdarzenia śledzenia dla Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) i [Podgląd zdarzeń](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Monitora wydajności** — narzędzie do zarządzania w trybie graficznym Windows, które używa liczników, liczniki śledzenia monitora i efekty śledzenia na wydajność. Aby uzyskać więcej informacji, zobacz [danych moduł zbierający zestawu ręcznie utworzyć](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Słowa kluczowe  
 Korzystając z <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> klasy .NET Framework komunikaty śledzenia zazwyczaj są filtrowane według poziom ważności (na przykład błędu, ostrzeżenia i informacje). ETW obsługuje pojęcie poziom ważności, ale wprowadza mechanizm filtrowania nowego, elastycznego za pomocą słów kluczowych. Słowa kluczowe są dowolne wartości tekstowej, umożliwiających zdarzenia śledzenia zapewnić dodatkowy kontekst informacji na temat znaczenia tego zdarzenia.  
  
 Śledzenie danych analitycznych programu WCF, każde zdarzenie śledzenia ma dwa typy słów kluczowych. Po pierwsze każde zdarzenie ma jeden lub więcej słów kluczowych scenariusza. Te słowa kluczowe oznaczają scenariusze, to zdarzenie jest przeznaczony do obsługi. Istnieją trzy scenariusz słów kluczowych, każdy tak zaprojektowany w określonym celu, jak pokazano w poniższej tabeli. Filtrowanie przy użyciu słów kluczowych można zmienić dynamicznie bez zakłócania działania usługi WCF. Oznacza to, że będzie można dynamicznie zmieniać Twojego bieżącego scenariusza śledzenia i ilość informacji śledzenia, które zostały zebrane. Na przykład można zmienić `HealthMonitoring` do `Troubleshooting` i zwiększenie szczegółowości śledzenia zdarzeń.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`HealthMonitoring`|Bardzo lekka i minimalny śledzenia, który umożliwia monitorowanie aktywności z usługą.|  
|`EndToEndMonitoring`|Zdarzenia używane do obsługi śledzenia przepływu komunikatów.|  
|`Troubleshooting`|Bardziej szczegółowe zdarzenia wokół punkty rozszerzeń programu WCF.|  
  
 Druga grupa słowa kluczowe zdefiniować które składnik [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] emitowane zdarzenia.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`UserEvents`|Zdarzenia wyemitowane przez kod użytkownika i nie [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Zdarzenia wyemitowane przez środowisko wykonawcze programu WCF.|  
|`ServiceHost`|Zdarzenia wyemitowane przez hosta usługi.|  
|`WCFMessageLogging`|Zdarzenia rejestrowania komunikatów WCF.|  
  
## <a name="see-also"></a>Zobacz także
- [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
