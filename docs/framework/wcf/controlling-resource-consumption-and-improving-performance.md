---
title: Kontrolowanie zużycia zasobów i zwiększanie wydajności
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 11d1333ed0ae8b46f8f87fa6f4643d4b31fac3ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785063"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Kontrolowanie zużycia zasobów i zwiększanie wydajności
W tym temacie opisano różne właściwości w różnych obszarach architektury usług Windows Communication Foundation (WCF), współpracują w celu kontroli użycia zasobów, które mają wpływ na metryki wydajności.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Właściwości, które ograniczyć zużycie zasobów w programie WCF
 Windows Communication Foundation (WCF) mają zastosowanie ograniczenia dotyczące niektórych rodzajów procesów do celów bezpieczeństwa ani wydajności. Te ograniczenia są dostępne w dwóch głównych formularzy, limity przydziału i ograniczenia. *Przydziały* ograniczeń wyzwalających osiągnięto lub przekroczono natychmiastowego wyjątek w pewnym momencie w systemie. *Ogranicza* ograniczeń, które nie powodują natychmiastowe zgłoszenie wyjątku. Zamiast tego po osiągnięciu limitu ograniczania przetwarzania kontynuuje, ale w granicach ustawieniem tej wartości ograniczania. Ograniczone przetwarzania mogą wywołać wyjątek w innym miejscu, ale zależy to od aplikacji.

 Oprócz rozróżnienia między limity przydziału i ograniczenia niektóre właściwości ograniczający znajdują się na poziomie serializacji, niektóre na poziomie transportu i niektóre na poziomie aplikacji. Na przykład limit przydziału <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, który jest implementowany przez wszystkie elementy powiązania transportu dostarczane przez system, jest domyślnie do 65 536 bajtów utrudnić złośliwi klienci angażowania w atakach typu "odmowa usługi" wobec usługi, powodując zbyt dużej ilości pamięci zużycie. (Zazwyczaj można zwiększyć wydajność przez zmniejszenie tej wartości.)

 Na przykład przydziału serializacji <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> właściwość, która określa maksymalną liczbę obiektów, które serializator serializuje i deserializuje w jednym <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> wywołania metody. Na przykład ograniczania dodatku poziomu aplikacji <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> właściwość, która domyślnie ogranicza liczbę połączeń współbieżnych kanału sesji do 10. (W odróżnieniu od przydziały, po osiągnięciu tej wartości ograniczania aplikacji będzie kontynuował przetwarzanie ale akceptuje nowych kanałów sesji, która oznacza, że nowi klienci nie można połączyć, dopóki jeden z innych kanałów sesji zakończył się).

 Te kontrolki mają łagodzenia poza pole dla niektórych rodzajów ataków lub metryk wydajności, takich jak zużycie pamięci, czas uruchamiania i tak dalej. W zależności od aplikacji, tych kontrolek można jednak utrudniać wydajności aplikacji usługi lub uniemożliwiają pracę na wszystkich aplikacji. Na przykład aplikacji przeznaczonej do strumienia wideo łatwo może przekroczyć domyślny <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> właściwości. Ten temat zawiera omówienie różnych formantów zastosowane dla aplikacji na wszystkich poziomach WCF, w tym artykule opisano różne sposoby, aby uzyskać więcej informacji na temat tego, czy to ustawienie jest zakłócały aplikacji i w tym artykule opisano sposób, aby rozwiązać problemy z różnych. Większość limity i przydziały niektóre są dostępne na poziomie aplikacji, nawet wtedy, gdy właściwość podstawowy jest ograniczeniem serializacji lub transportu. Na przykład można ustawić <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> właściwość za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> właściwość klasy usługi.

> [!NOTE]
> Jeśli masz konkretnych problemów, warto najpierw przeczytać artykuł [Szybki Start Rozwiązywanie problemów z architekturą WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) aby zobaczyć, czy problem (i rozwiązania) widocznych na niej.

 Właściwości, które ograniczają procesy serializacji są wymienione w [zagadnienia dotyczące zabezpieczeń dla danych](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Właściwości, które ograniczyć zużycie zasobów związanych z transportami są wymienione w [przydziały dla transportu](../../../docs/framework/wcf/feature-details/transport-quotas.md). Właściwości, które ograniczają zużycie zasobów w warstwie aplikacji są członkami <xref:System.ServiceModel.Dispatcher.ServiceThrottle> klasy.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Wykrywanie, aplikacji i problemy z wydajnością związane z ustawieniami limitu przydziału
 Aby włączyć funkcję podstawową aplikację dla szerokiego zakresu typów aplikacji przy jednoczesnym zapewnieniu podstawową ochronę przed typowych problemów z zabezpieczeniami zostały wybrane wartości domyślne powyższe wartości. Jednak projekty różnych aplikacji może przekraczać co najmniej jedno ustawienie przepustowości, mimo że aplikacja, w przeciwnym razie jest bezpieczna i będzie działać zgodnie z założeniami. W takich przypadkach należy zidentyfikować przekroczeniu wartości, które ograniczenie przepustowości i w poziomie i wybrać odpowiedni tryb postępowania w celu zwiększenia przepływności aplikacji.

 Zwykle podczas pisania aplikacji i jej debugowania, możesz ustawić <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości `true` w pliku konfiguracji lub programowo. To powoduje, że usługi WCF do zwrócenia śladów stosu wyjątków usługi do aplikacji klienckiej do przeglądania. Ta funkcja raportów większość wyjątków na poziomie aplikacji w taki sposób, aby wyświetlić ustawienia limitu przydziału, które mogą być wykonywane, jeśli ten problem.

 Niektóre wyjątki się tak zdarzyć w czasie wykonywania poniżej widoczność warstwy aplikacji i nie są zwracane, za pomocą tego mechanizmu, a nie może być obsługiwane przez niestandardowy <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementacji. Jeśli pracujesz w środowisku deweloperskim, takich jak program Microsoft Visual Studio, większość z tych wyjątków są wyświetlane automatycznie. Jednak niektóre wyjątki mogą zamaskować ustawienia środowiska programowania, takich jak [tylko mój kod](/visualstudio/debugger/just-my-code) programu Visual Studio.

 Niezależnie od możliwości swojego środowiska projektowego można użyć możliwości śledzenia WCF i rejestrowania komunikatów debugowania wszystkie wyjątki i dostrajanie wydajności aplikacji. Aby uzyskać więcej informacji, zobacz [przy użyciu śledzenia do Rozwiązywanie problemów aplikacji](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Problemy z wydajnością i elementu XmlSerializer
 Usługi i aplikacje klienckie, które używają typów danych, które są możliwe do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilowanie kodu serializacji dla tych typów danych w czasie wykonywania, co może skutkować wydajności uruchamiania powolne.

> [!NOTE]
> Serializacja wstępnie wygenerowanego kodu może służyć tylko w aplikacjach klienckich, a nie w usługach.

 [Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji, generowania kodu serializacji niezbędne z skompilowanych zestawów dla aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Poprawę czasu uruchamiania programu WCF klienta aplikacji przy użyciu elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problemy z wydajnością, odnośnie do hostowania usług WCF w ramach platformy ASP.NET
 Gdy usługa WCF jest hostowana w ramach usług IIS i platformy ASP.NET, ustawienia konfiguracji programu IIS i programu ASP.NET może wpływać na przepływność i pamięć śladu usługi WCF.  Aby uzyskać więcej informacji o wydajności platformy ASP.NET, zobacz [poprawę wydajności ASP.NET](https://go.microsoft.com/fwlink/?LinkId=186462).  Jeden ustawienie może mieć niezamierzone konsekwencje jest <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, co jest właściwością <xref:System.Web.Configuration.ProcessModelSection>. Jeśli aplikacja ma stałej lub małej liczby klientów, ustawienie <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 mogą dostarczać boost przepływności na komputerze wieloprocesorowych, w którym wykorzystanie procesora CPU w prawie 100%. Ten wzrost wydajności ma swoją cenę: również spowoduje zwiększenie użycia pamięci, co może zmniejszyć skalowalności.

## <a name="see-also"></a>Zobacz także

- [Administracja i diagnostyka](../../../docs/framework/wcf/diagnostics/index.md)
- [Duże ilości danych i przesyłanie strumieniowe](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
