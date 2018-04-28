---
title: Dynamiczne włączanie śledzenia danych analitycznych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d070c66eebbf1a067254c38c6e5bfc7f40742863
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamiczne włączanie śledzenia danych analitycznych
Za pomocą narzędzi, które są dostarczane z systemem operacyjnym Windows, można włączyć lub wyłączyć śledzenie dynamicznie za pomocą zdarzenia śledzenia dla systemu Windows (ETW). Dla wszystkich [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi, śledzenie analityczne mogą być włączonych i wyłączonych dynamicznie bez modyfikowania pliku Web.config aplikacji i ponowne uruchomienie usługi. Dzięki temu aplikacja, która emituje zdarzeń śledzenia, które chcesz zachować nienaruszonej.  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] opcji śledzenia można skonfigurować w podobny sposób. Na przykład można zmienić poziom ważności z **błąd** do **informacji** bez zakłócania działania aplikacji. Można to zrobić za pomocą następujących narzędzi:  
  
-   **Logman** — narzędzie wiersza polecenia do konfigurowania, kontrolowanie i badanie danych śledzenia. Aby uzyskać więcej informacji, zobacz [śledzenia utworzyć Logman](http://go.microsoft.com/fwlink/?LinkId=165426) i [śledzenia aktualizacji Logman](http://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Podglądzie zdarzeń** — Windows graficzne narzędzie do zarządzania do wyświetlania wyników śledzenia. Aby uzyskać więcej informacji, zobacz [usługi WCF i śledzenia zdarzeń dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) i [Podgląd zdarzeń](http://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** — narzędzie do zarządzania graficznego systemu Windows, które używa liczników liczniki Monitora śledzenia i wpływu śledzenie na wydajność. Aby uzyskać więcej informacji, zobacz [danych modułu zbierającego Ustaw ręcznie utworzyć](http://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Słowa kluczowe  
 Korzystając z <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> klasy .NET Framework komunikaty śledzenia zazwyczaj są filtrowane według poziom ważności (na przykład błędu, ostrzeżenia i informacje). ETW obsługuje pojęcie poziomu ważności, ale wprowadza mechanizm nowych, elastycznych filtrów słów kluczowych. Słowa kluczowe są dowolne wartości tekstowej, które pozwalają zapewnić dodatkowy kontekst o to zdarzenie oznacza zdarzenia śledzenia.  
  
 Aby uzyskać [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] analityczne śledzenia, każde zdarzenie śledzenia są dostępne dwa typy słów kluczowych. Najpierw każde zdarzenie ma co najmniej jeden scenariusz słów kluczowych. Słowa kluczowe oznaczenia scenariusze przeznaczony do obsługi tego zdarzenia. Istnieją trzy słowa kluczowe scenariusz, każdy przeznaczone do określonego celu, jak pokazano w poniższej tabeli. Filtrowanie przy użyciu słów kluczowych można zmienić dynamicznie bez zakłócania [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi. Oznacza to, że można dynamicznie zmieniać scenariuszu śledzenia i ilość informacji śledzenia, które należy zebrać. Na przykład można zmienić `HealthMonitoring` do `Troubleshooting` i zwiększenie szczegółowości śledzenia zdarzeń.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`HealthMonitoring`|Bardzo niewielka, minimalnym śledzenia, który umożliwia monitorowanie działania usługi.|  
|`EndToEndMonitoring`|Zdarzenia używane do obsługi śledzenia przepływu komunikatów.|  
|`Troubleshooting`|Bardziej szczegółowe zdarzenia wokół punktów rozszerzalności [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].|  
  
 Drugiej grupy słów kluczowych zdefiniuj którym składnikiem [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] wysyłanego zdarzenia.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`UserEvents`|Zdarzenia emitowane przez kod użytkownika i nie [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|Zdarzenia emitowane przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] środowiska wykonawczego.|  
|`ServiceHost`|Zdarzenia emitowane przez hosta usługi.|  
|`WCFMessageLogging`|[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] komunikat rejestrowania zdarzeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
