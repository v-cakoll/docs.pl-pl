---
title: Dynamiczne włączanie śledzenia danych analitycznych
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 68152741541fdbc048ba290cfb956babaed2e0d7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamiczne włączanie śledzenia danych analitycznych
Za pomocą narzędzi, które są dostarczane z systemem operacyjnym Windows, można włączyć lub wyłączyć śledzenie dynamicznie za pomocą zdarzenia śledzenia dla systemu Windows (ETW). Dla wszystkich [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] usług Windows Communication Foundation (WCF), może być śledzenie analityczne, włączonych i wyłączonych dynamicznie bez modyfikowania pliku Web.config aplikacji i ponowne uruchomienie usługi. Dzięki temu aplikacja, która emituje zdarzeń śledzenia, które chcesz zachować nienaruszonej.  
  
 W podobny sposób można skonfigurować opcje śledzenia WCF. Na przykład można zmienić poziom ważności z **błąd** do **informacji** bez zakłócania działania aplikacji. Można to zrobić za pomocą następujących narzędzi:  
  
-   **Logman** — narzędzie wiersza polecenia do konfigurowania, kontrolowanie i badanie danych śledzenia. Aby uzyskać więcej informacji, zobacz [śledzenia utworzyć Logman](http://go.microsoft.com/fwlink/?LinkId=165426) i [śledzenia aktualizacji Logman](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Podglądzie zdarzeń** — Windows graficzne narzędzie do zarządzania do wyświetlania wyników śledzenia. Aby uzyskać więcej informacji, zobacz [usługi WCF i śledzenia zdarzeń dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) i [Podgląd zdarzeń](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** — narzędzie do zarządzania graficznego systemu Windows, które używa liczników liczniki Monitora śledzenia i wpływu śledzenie na wydajność. Aby uzyskać więcej informacji, zobacz [danych modułu zbierającego Ustaw ręcznie utworzyć](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Słowa kluczowe  
 Korzystając z <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> klasy .NET Framework komunikaty śledzenia zazwyczaj są filtrowane według poziom ważności (na przykład błędu, ostrzeżenia i informacje). ETW obsługuje pojęcie poziomu ważności, ale wprowadza mechanizm nowych, elastycznych filtrów słów kluczowych. Słowa kluczowe są dowolne wartości tekstowej, które pozwalają zapewnić dodatkowy kontekst o to zdarzenie oznacza zdarzenia śledzenia.  
  
 Śledzenie analityczne WCF, każdego zdarzenia śledzenia ma dwa typy słów kluczowych. Najpierw każde zdarzenie ma co najmniej jeden scenariusz słów kluczowych. Słowa kluczowe oznaczenia scenariusze przeznaczony do obsługi tego zdarzenia. Istnieją trzy słowa kluczowe scenariusz, każdy przeznaczone do określonego celu, jak pokazano w poniższej tabeli. Filtrowanie przy użyciu słów kluczowych można zmienić dynamicznie bez zakłócania działania usługi WCF. Oznacza to, że można dynamicznie zmieniać scenariuszu śledzenia i ilość informacji śledzenia, które należy zebrać. Na przykład można zmienić `HealthMonitoring` do `Troubleshooting` i zwiększenie szczegółowości śledzenia zdarzeń.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`HealthMonitoring`|Bardzo niewielka, minimalnym śledzenia, który umożliwia monitorowanie działania usługi.|  
|`EndToEndMonitoring`|Zdarzenia używane do obsługi śledzenia przepływu komunikatów.|  
|`Troubleshooting`|Bardziej szczegółowe zdarzenia wokół punktów rozszerzalności programu WCF.|  
  
 Drugiej grupy słów kluczowych zdefiniuj którym składnikiem [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] wysyłanego zdarzenia.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`UserEvents`|Zdarzenia emitowane przez kod użytkownika i nie [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Zdarzenia emitowane przez środowisko wykonawcze usługi WCF.|  
|`ServiceHost`|Zdarzenia emitowane przez hosta usługi.|  
|`WCFMessageLogging`|Usługi WCF komunikat rejestrowania zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
