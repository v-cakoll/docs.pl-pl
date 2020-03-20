---
title: Dynamiczne włączanie śledzenia danych analitycznych
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: 22d122f802e82c2aa04d72a996cb872e06fcaeaa
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674955"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Dynamiczne włączanie śledzenia danych analitycznych
Korzystając z narzędzi dostarczanych z systemem operacyjnym Windows, można dynamicznie włączać lub wyłączać śledzenie za pomocą śledzenia zdarzeń dla systemu Windows (ETW). W [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] przypadku wszystkich usług Windows Communication Foundation (WCF) śledzenie analityczne można włączać i wyłączać dynamicznie bez modyfikowania pliku Web.config aplikacji ani ponownego uruchamiania usługi. Dzięki temu aplikacja, która emituje zdarzenia śledzenia pozostają niezakłócone.  
  
 Opcje śledzenia WCF można skonfigurować w podobny sposób. Na przykład można zmienić poziom ważności z **Błąd** na **Informacje** bez zakłócania aplikacji. Można to zrobić za pomocą następujących narzędzi:  
  
- **Logman** — narzędzie wiersza polecenia do konfigurowania, kontrolowania i wykonywania zapytań o dane śledzenia. Aby uzyskać więcej informacji, zobacz [Logman Tworzenie śledzenia](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788036(v=ws.10)) i [Śledzenia aktualizacji logmana](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc788128(v=ws.10)).  
  
- **EventViewer** - Narzędzie do zarządzania graficznego systemu Windows do przeglądania wyników śledzenia. Aby uzyskać więcej informacji, zobacz [Usługi WCF i śledzenie zdarzeń dla systemu Windows](../../samples/wcf-services-and-event-tracing-for-windows.md) i Podgląd [zdarzeń](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)).  
  
- **Perfmon** – Windows graficzny zarządzanie narzędzie ów używa liczniki wobec monitor ślad liczniki i ten wpływ od ślad u świadczenie. Aby uzyskać więcej informacji, zobacz [Ręczne tworzenie zestawu modułów zbierających dane](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766404(v=ws.11)).  
  
### <a name="keywords"></a>Słowa kluczowe  
 Podczas korzystania <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> z klasy .NET Framework komunikaty śledzenia są zazwyczaj filtrowane według poziomu ważności (na przykład Błąd, Ostrzeżenie i Informacje). ETW obsługuje koncepcję poziomu ważności, ale wprowadza nowy, elastyczny mechanizm filtrowania przy użyciu słów kluczowych. Słowa kluczowe są dowolne wartości tekstowe, które umożliwiają śledzenie zdarzeń zapewniają dodatkowy kontekst o tym, co oznacza to zdarzenie.  
  
 W przypadku śledzenia analitycznego WCF każde zdarzenie śledzenia ma dwa typy słów kluczowych. Po pierwsze każde zdarzenie ma jeden lub więcej słów kluczowych scenariusza. Te słowa kluczowe oznaczają scenariusze, które to zdarzenie jest przeznaczone do obsługi. Istnieją trzy słowa kluczowe scenariusza, każdy przeznaczony do określonego celu, jak pokazano w poniższej tabeli. Filtrowanie przy użyciu słów kluczowych można zmieniać dynamicznie bez zakłócania usługi WCF. Oznacza to, że można dynamicznie zmienić bieżący scenariusz śledzenia i ilość informacji śledzenia, które można zebrać. Na przykład można `HealthMonitoring` zmienić `Troubleshooting` i zwiększyć szczegółowość zdarzenia śledzenia.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`HealthMonitoring`|Bardzo lekkie, minimalne śledzenie, które pozwala monitorować aktywność usługi.|  
|`EndToEndMonitoring`|Zdarzenia używane do obsługi śledzenia przepływu wiadomości.|  
|`Troubleshooting`|Bardziej szczegółowe zdarzenia wokół punktów rozszerzalności WCF.|  
  
 Druga grupa słów kluczowych określa, który składnik programu .NET Framework emitował zdarzenie.  
  
|Słowo kluczowe|Opis|  
|-------------|-----------------|  
|`UserEvents`|Zdarzenia emitowane przez kod użytkownika, a nie .NET Framework.|  
|`ServiceModel`|Zdarzenia emitowane przez środowisko uruchomieniowe WCF.|  
|`ServiceHost`|Zdarzenia emitowane przez hosta usługi.|  
|`WCFMessageLogging`|Zdarzenia rejestrowania komunikatów WCF.|  
  
## <a name="see-also"></a>Zobacz też

- [Usługi i śledzenie zdarzeń programu WCF dla systemu Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
