---
title: Kontrolowanie zużycia zasobów i zwiększanie wydajności
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: ee94ae7c570156d870b93311365ad52b815f12d5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Kontrolowanie zużycia zasobów i zwiększanie wydajności
W tym temacie opisano różne właściwości w różnych obszarach o architekturze Windows Communication Foundation (WCF), które współpracują w celu sterowania zużycia zasobów i wpływają na metryki wydajności.  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Właściwości, które ograniczyć zużycie zasobów w programie WCF  
 Windows Communication Foundation (WCF) ma zastosowanie ograniczenia dotyczące niektórych typów procesów celów zabezpieczeń i wydajności. Ograniczenia te są dostępne w dwóch głównych formularzy, przydziały i limity. *Przydziały* są limity wyzwalających osiągnięto lub przekroczono natychmiastowego wyjątek w pewnym momencie w systemie. *Ogranicza* ograniczeń, które nie powodują natychmiast wyjątków. Zamiast tego po osiągnięciu limitu ograniczania przepustowości przetwarzania nadal, ale w granicach ustawiony przez wartość tego ograniczenia. To ograniczona przetwarzanie może wyzwolić wyjątek w innym miejscu, ale zależy to od aplikacji.  
  
 Oprócz różnicy między przydziały i limity niektóre właściwości ograniczający znajdują się na poziomie serializacji, niektóre na poziomie transportu i niektóre na poziomie aplikacji. Na przykład limit przydziału <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, który jest implementowany przez wszystkie elementy powiązania transportu dostarczany przez system, jest domyślnie do 65 536 bajtów utrudnić złośliwego klientów angażowania ataku typu "odmowa usługi" Usługa powodując nadmiernego pamięci Użycie. (Zazwyczaj można zwiększyć wydajność przez zmniejszenie tej wartości.)  
  
 Na przykład limit przydziału serializacji <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> właściwość, która określa maksymalną liczbę obiektów, które serializator serializuje i deserializuje w jednej <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> wywołania metody. Na przykład ograniczania na poziomie aplikacji <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> właściwość, która domyślnie ogranicza liczbę połączeń współbieżnych podczas zamykania kanału do 10. (W przeciwieństwie do przydziałów, po osiągnięciu tej wartości ograniczania aplikacja przetwarzanie jest kontynuowane, ale akceptuje nie nowych zamykania kanałów, co oznacza, że nowych klientów nie można połączyć z aż do jednego z innych kanałów sesyjnych została zakończona.)  
  
 Formanty te zostały zaprojektowane łagodzenia poza pole przed określone typy ataków lub metryki wydajności, takich jak zużycie pamięci, czas uruchamiania i tak dalej. W zależności od aplikacji, tych kontrolek można jednak utrudniać wydajność aplikacji usługi lub uniemożliwiają pracy na wszystkich aplikacji. Na przykład, aplikacja do strumienia wideo łatwo może przekroczyć domyślny <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> właściwości. Ten temat zawiera przegląd różnych formantów zastosowane dla aplikacji na wszystkich poziomach WCF, opisano różne sposoby, aby uzyskać więcej informacji na temat tego, czy jest to ustawienie jest zakłócały aplikacji i opisano sposób, aby rozwiązać problemy z różnych. Większość limity i niektóre przydziały są dostępne na poziomie aplikacji, nawet wtedy, gdy właściwość podstawowy jest ograniczeniem serializacji lub transportu. Na przykład można ustawić <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> za pomocą właściwości <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> właściwość klasy usługi.  
  
> [!NOTE]
>  Jeśli masz konkretnych problemów, należy najpierw przeczytać [szybkiego startu WCF Rozwiązywanie problemów z](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) aby zobaczyć, czy problem (rozwiązanie) jest wyświetlany i.  
  
 Właściwości, które ograniczają procesów serializacji są wymienione w [zagadnienia dotyczące zabezpieczeń dla danych](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Właściwości, które ograniczyć zużycie zasobów związanych z transportu są wymienione w [przydziały dla transportu](../../../docs/framework/wcf/feature-details/transport-quotas.md). Właściwości, które ograniczają zużycie zasobów w warstwie aplikacji są członkami <xref:System.ServiceModel.Dispatcher.ServiceThrottle> klasy.  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Wykrywanie aplikacji i problemy z wydajnością związane z ustawieniami limitu przydziału  
 Aby włączyć funkcję aplikacji w warstwie podstawowa w szerokim zakresie typów aplikacji, zapewniając Podstawowa ochrona typowych problemów z zabezpieczeniami zostały wybrane ustawienia domyślne poprzedniej wartości. Jednak projektów innej aplikacji może przekroczyć co najmniej jednego ustawienia ograniczania, mimo że aplikacja, w przeciwnym razie jest bezpieczna i będzie działać zgodnie z założeniami. W takich sytuacjach należy wskazać przekroczenia wartości ograniczania i w poziomie i podjąć decyzję w odpowiedni sposób postępowania w celu zwiększenia przepływności aplikacji.  
  
 Zazwyczaj podczas pisania aplikacji i jej debugowanie, ustawiania <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> właściwości `true` w pliku konfiguracji lub programowo. To powoduje, że usługi WCF, aby przywrócić dane śledzenia stosu wyjątków usługi aplikacji klienta w celu wyświetlenia. Ta funkcja raporty większość wyjątków na poziomie aplikacji w taki sposób, aby wyświetlić ustawienia limitu przydziału, które mogą być wykonywane, jeżeli jest to problem.  
  
 Niektóre wyjątki wykonana w czasie wykonywania poniżej widoczność warstwy aplikacji i nie są zwracane przy użyciu tego mechanizmu i nie mogą one być obsługiwane przez niestandardowy <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementacji. Jeśli pracujesz w środowisku projektowania, takich jak program Microsoft Visual Studio, większość tych wyjątków są automatycznie wyświetlane. Jednak niektóre wyjątki można zamaskować programowanie ustawienia środowiska, takich jak [tylko mój kod](http://go.microsoft.com/fwlink/?LinkId=82174) ustawień w programie Visual Studio 2005.  
  
 Niezależnie od możliwości środowiska deweloperskiego skorzystać z możliwości śledzenia WCF oraz rejestrowanie komunikatów debugowania wszystkie wyjątki i dostrajania wydajności aplikacji. Aby uzyskać więcej informacji, zobacz [przy użyciu śledzenie, aby rozwiązać Twoja aplikacja](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="performance-issues-and-xmlserializer"></a>Problemy z wydajnością i XmlSerializer  
 Usługi i aplikacje klienckie, które używają typów danych, które są do serializacji przy użyciu <xref:System.Xml.Serialization.XmlSerializer> Generowanie i kompilacja kodu serializacji dla tych typów danych w czasie wykonywania, co może spowodować wolne uruchamiania wydajności.  
  
> [!NOTE]
>  Serializacja wstępnie wygenerowanego kodu można użyć tylko w aplikacjach klienckich, a nie w usługach.  
  
 [Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) może poprawić wydajność uruchamiania tych aplikacji przez generowania kodu serializacji niezbędne z skompilowane zestawy dla aplikacji. Aby uzyskać więcej informacji, zobacz [porady: poprawy uruchamiania czasu programu WCF aplikacje klienckie przy użyciu elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problemy z wydajnością odnośnie do hostowania usług WCF w ramach platformy ASP.NET  
 Gdy usługa WCF jest hostowana w ramach usług IIS i platformy ASP.NET, ustawienia konfiguracji usług IIS i platformy ASP.NET może mieć wpływ na przepustowość i pamięci rozmiaru usługi WCF.  Aby uzyskać więcej informacji o wydajności platformy ASP.NET, zobacz [poprawę wydajności ASP.NET](http://go.microsoft.com/fwlink/?LinkId=186462).  Jeden ustawienie może być jest niezamierzone skutki <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, która jest właściwością <xref:System.Web.Configuration.ProcessModelSection>. Jeśli aplikacja ma stały lub małej liczby klientów, ustawienie <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 może zawierać większą przepustowość na komputerze wieloprocesorowych, który ma użycie procesora CPU, bliski 100%. To zwiększenie wydajności jest dostarczany z koszt: również spowoduje zwiększenie użycia pamięci, co może zmniejszyć skalowalności.  
  
## <a name="see-also"></a>Zobacz też  
 [Administracja i diagnostyka](../../../docs/framework/wcf/diagnostics/index.md)  
 [Duże ilości danych i przesyłanie strumieniowe](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
