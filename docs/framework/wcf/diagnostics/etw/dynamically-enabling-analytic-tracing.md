---
title: Dynamiczne włączanie śledzenia danych analitycznych
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: bea64ac9a9312d17b7f47e72a46d876552e20a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798097"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamiczne włączanie śledzenia danych analitycznych
Korzystając z narzędzi dostarczanych z systemem operacyjnym Windows, można dynamicznie włączać lub wyłączać śledzenie przy użyciu funkcji śledzenia zdarzeń systemu Windows (ETW). W przypadku [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] wszystkich usług Windows Communication Foundation (WCF) Śledzenie analityczne można włączyć i wyłączyć dynamicznie bez modyfikowania pliku Web. config aplikacji ani ponownego uruchamiania usługi. Dzięki temu aplikacja, która emituje zdarzenia śledzenia, pozostaje niezakłócona.  
  
 Opcje śledzenia WCF można skonfigurować w podobny sposób. Na przykład można zmienić poziom ważności z **błędu** na **informacje** bez zakłócania działania aplikacji. Można to zrobić przy użyciu następujących narzędzi:  
  
- **Logman** — narzędzie wiersza polecenia służące do konfigurowania, kontrolowania i wykonywania zapytań dotyczących danych śledzenia. Aby uzyskać więcej informacji, zobacz [Logman Create Trace](https://go.microsoft.com/fwlink/?LinkId=165426) and [logman update Trace](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
- **Podglądzie zdarzeń** — narzędzie do graficznego zarządzania systemem Windows do wyświetlania wyników śledzenia. Aby uzyskać więcej informacji, zobacz [usługi WCF i śledzenie zdarzeń dla systemu Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) i [Podgląd zdarzeń](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
- **Perfmon** — narzędzie do zarządzania graficznego systemu Windows korzystające z liczników do monitorowania liczników śledzenia i efektów śledzenia wydajności. Aby uzyskać więcej informacji, zobacz [Ręczne tworzenie zestawu modułów zbierających dane](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>słowa kluczowe  
 Korzystając z <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> klasy, .NET Framework komunikaty śledzenia są zwykle filtrowane według poziomu ważności (na przykład błędu, ostrzeżenia i informacji). Funkcja ETW obsługuje koncepcję poziomu ważności, ale wprowadza nowy, elastyczny mechanizm filtrowania przy użyciu słów kluczowych. Słowa kluczowe to dowolne wartości tekstowe, które umożliwiają śledzenie zdarzeń zapewniają dodatkowy kontekst dotyczący tego, co oznacza to zdarzenie.  
  
 W przypadku śledzenia analitycznego WCF każde zdarzenie śledzenia ma dwa typy słów kluczowych. Najpierw każde zdarzenie zawiera jedno lub więcej słów kluczowych scenariusza. Te słowa kluczowe oznaczają scenariusze, które mają być obsługiwane przez to zdarzenie. Istnieją trzy słowa kluczowe scenariusza, z których każdy jest przeznaczony do określonego celu, jak pokazano w poniższej tabeli. Filtrowanie przy użyciu słów kluczowych może być zmieniane dynamicznie bez zakłócania działania usługi WCF. Oznacza to, że można dynamicznie zmienić bieżący scenariusz śledzenia i ilość zbieranych informacji śledzenia. Na przykład można zmienić `HealthMonitoring` `Troubleshooting` i zwiększyć stopień szczegółowości zdarzeń śledzenia.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`HealthMonitoring`|Bardzo lekkie, minimalne śledzenie umożliwiające monitorowanie aktywności usługi.|  
|`EndToEndMonitoring`|Zdarzenia używane do obsługi śledzenia przepływu komunikatów.|  
|`Troubleshooting`|Bardziej szczegółowe zdarzenia wokół punktów rozszerzalności WCF.|  
  
 Druga grupa słów kluczowych definiuje, który składnik .NET Framework emituje zdarzenie.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`UserEvents`|Zdarzenia emitowane przez kod użytkownika, a nie .NET Framework.|  
|`ServiceModel`|Zdarzenia emitowane przez środowisko uruchomieniowe WCF.|  
|`ServiceHost`|Zdarzenia emitowane przez hosta usługi.|  
|`WCFMessageLogging`|Zdarzenia rejestrowania komunikatów WCF.|  
  
## <a name="see-also"></a>Zobacz także

- [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
