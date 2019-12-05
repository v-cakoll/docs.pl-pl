---
title: Kontrolowanie zużycia zasobów i zwiększanie wydajności
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 16d6f29235455ff30e115b7aff3425412bc7ba6a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802259"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Kontrolowanie zużycia zasobów i zwiększanie wydajności
W tym temacie opisano różne właściwości w różnych obszarach architektury Windows Communication Foundation (WCF), które działają w celu kontrolowania zużycia zasobów i wpływają na metryki wydajności.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Właściwości ograniczające użycie zasobów w programie WCF
 Windows Communication Foundation (WCF) stosuje ograniczenia dotyczące niektórych typów procesów w celu zapewnienia bezpieczeństwa lub wydajności. Te ograniczenia są dostępne w dwóch głównych formularzach — przydziałach i ograniczeniach. Limity *przydziału* są limitami, które po osiągnięciu lub przekroczeniu wyzwalają natychmiastowy wyjątek w pewnym momencie w systemie. *Ograniczenia* są ograniczone, które nie powodują natychmiastowego zgłoszenia wyjątku. Zamiast tego, po osiągnięciu limitu ograniczania, przetwarzanie jest kontynuowane, ale w ramach limitów ustawionych przez wartość ograniczenia. To ograniczone przetwarzanie może wyzwolić wyjątek w innym miejscu, ale jest to zależne od aplikacji.

 Oprócz rozróżnienia między przydziałami i ograniczeniami, pewne właściwości ograniczające się na poziomie serializacji, na poziomie transportu, a także na poziomie aplikacji. Na przykład <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>przydziału, który jest implementowany przez wszystkie elementy powiązania transportu dostarczone przez system, jest domyślnie ustawiony na 65 536 bajtów, aby utrudnić złośliwym klientom zaangażowanie się w atak typu "odmowa usługi" na usługę, powodując nadmierne użycie pamięci. (Zazwyczaj można zwiększyć wydajność, obniżając tę wartość).

 Przykładem przydziału serializacji jest właściwość <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType>, która określa maksymalną liczbę obiektów serializowanych lub deserializacji serializatora w jednym wywołaniu metody <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A>. Przykładem ograniczenia poziomu aplikacji jest właściwość <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType>, która domyślnie ogranicza liczbę współbieżnych połączeń sesji do 10. (W przeciwieństwie do przydziałów, jeśli wartość tego ograniczenia zostanie osiągnięta, aplikacja kontynuuje przetwarzanie, ale nie akceptuje żadnych nowych kanałów sesji, co oznacza, że nowi klienci nie będą mogli nawiązywać połączeń do momentu zakończenia jednego z pozostałych kanałów sesji).

 Te kontrolki zostały zaprojektowane w celu zapewnienia gotowego do użycia środków zaradczych przed niektórymi typami ataków lub w celu poprawienia metryk wydajności, takich jak rozmiary pamięci, czas rozpoczęcia i tak dalej. Jednak w zależności od aplikacji te kontrolki mogą utrudniać wydajność aplikacji usług lub uniemożliwić działanie aplikacji. Na przykład aplikacja zaprojektowana na potrzeby przesyłania strumieniowego wideo może łatwo przekroczyć domyślną właściwość <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>. Ten temat zawiera omówienie różnych kontrolek stosowanych do aplikacji na wszystkich poziomach programu WCF, opis różnych sposobów uzyskania dodatkowych informacji na temat tego, czy ustawienie przeszkadza w aplikacji, oraz opisuje sposoby rozwiązywania różnych problemów. Większość ograniczania przepustowości i niektórych przydziałów są dostępne na poziomie aplikacji, nawet jeśli właściwość podstawowa jest ograniczeniem serializacji lub transportu. Na przykład można ustawić właściwość <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> przy użyciu właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> w klasie usługi.

> [!NOTE]
> W przypadku konkretnego problemu należy najpierw przeczytać [Przewodnik Szybki Start dotyczący rozwiązywania problemów z usługą WCF](wcf-troubleshooting-quickstart.md) , aby sprawdzić, czy na liście znajduje się problem (i rozwiązanie).

 Właściwości ograniczające procesy serializacji są wymienione w temacie [zagadnienia dotyczące zabezpieczeń danych](./feature-details/security-considerations-for-data.md). Właściwości ograniczające użycie zasobów związanych z transportami są wymienione w obszarze [przydziały transportu](./feature-details/transport-quotas.md). Właściwości ograniczające użycie zasobów w warstwie aplikacji są elementami członkowskimi klasy <xref:System.ServiceModel.Dispatcher.ServiceThrottle>.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Wykrywanie problemów z aplikacjami i wydajnością związanych z ustawieniami limitu przydziału
 Ustawienia domyślne powyższych wartości zostały wybrane w celu włączenia podstawowej funkcjonalności aplikacji dla szerokiego zakresu typów aplikacji, a jednocześnie zapewnia podstawową ochronę przed typowymi problemami z zabezpieczeniami. Jednak różne projekty aplikacji mogą przekroczyć jedno lub więcej ustawień ograniczania, chociaż aplikacja jest bezpieczna i będzie działała zgodnie z założeniami. W takich przypadkach należy określić, które wartości ograniczania przepustowości są przewyższane i na jakim poziomie, i podjąć decyzję o odpowiednim czasie działania, aby zwiększyć przepływność aplikacji.

 Zazwyczaj podczas pisania aplikacji i debugowania należy ustawić właściwość <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true` w pliku konfiguracyjnym lub programowo. Powoduje to zwrócenie przez program WCF śladów stosu wyjątków usługi do aplikacji klienckiej w celu wyświetlenia. Ta funkcja raportuje większość wyjątków poziomu aplikacji w taki sposób, aby wyświetlić ustawienia przydziałów, które mogą być uwzględnione, jeśli jest to problem.

 Niektóre wyjątki występują w czasie wykonywania poniżej widoczności warstwy aplikacji i nie są zwracane przy użyciu tego mechanizmu i mogą nie być obsługiwane przez niestandardową implementację <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType>. Jeśli jesteś w środowisku deweloperskim, takim jak Microsoft Visual Studio, większość z tych wyjątków jest wyświetlana automatycznie. Niektóre wyjątki mogą jednak być maskowane przez ustawienia środowiska programistycznego, takie jak [tylko mój kod](/visualstudio/debugger/just-my-code) Visual Studio.

 Niezależnie od możliwości środowiska programistycznego można używać funkcji śledzenia i rejestrowania komunikatów w programie WCF w celu debugowania wszystkich wyjątków i dostrajania wydajności aplikacji. Aby uzyskać więcej informacji, zobacz [Używanie śledzenia w celu rozwiązywania problemów z aplikacją](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Problemy z wydajnością i XmlSerializer
 Usługi i aplikacje klienckie korzystające z typów danych, które można serializować przy użyciu <xref:System.Xml.Serialization.XmlSerializer> generują i kompilują kod serializacji dla tych typów danych w czasie wykonywania, co może spowodować spowolnienie wydajności.

> [!NOTE]
> Wstępnie wygenerowany kod serializacji może być używany tylko w aplikacjach klienckich, a nie w usługach.

 [Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) może zwiększyć wydajność uruchamiania tych aplikacji, generując wymagany kod serializacji z skompilowanych zestawów dla aplikacji. Aby uzyskać więcej informacji, zobacz [How to: ulepszanie czasu uruchamiania aplikacji klienckich WCF przy użyciu elementu XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problemy z wydajnością podczas hostowania usług WCF w obszarze ASP.NET

Gdy usługa WCF jest hostowana w usługach IIS i ASP.NET, ustawienia konfiguracji usług IIS i ASP.NET mogą mieć wpływ na przepływność i ilość pamięci usługi WCF.  Aby uzyskać więcej informacji na temat wydajności ASP.NET, zobacz [Poprawianie wydajności ASP.NET](https://docs.microsoft.com/previous-versions/msp-n-p/ff647787(v=pandp.10)). Jedno ustawienie, które może mieć niezamierzone konsekwencje, jest <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, które jest właściwością <xref:System.Web.Configuration.ProcessModelSection>. Jeśli aplikacja ma ustaloną lub małą liczbę klientów, ustawienie <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> na 2 może zapewnić zwiększenie przepływności na komputerze wieloprocesorowym, który ma wykorzystanie procesora w pobliżu 100%. Ten wzrost wydajności obejmuje koszt: spowoduje to również zwiększenie użycia pamięci, co może obniżyć skalowalność.

## <a name="see-also"></a>Zobacz także

- [Administracja i diagnostyka](./diagnostics/index.md)
- [Duże ilości danych i przesyłanie strumieniowe](./feature-details/large-data-and-streaming.md)
