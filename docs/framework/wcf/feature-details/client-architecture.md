---
title: Architektura klienta
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 12db0d4f5717287439b66810e6354b12a4c68b77
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="client-architecture"></a>Architektura klienta
Aplikacje używają [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] obiekty klienta do wywołania operacji usługi. W tym temacie omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanały klienta i ich relacji z podstawową architekturę kanału. Aby uzyskać ogólne omówienie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty klienta, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Aby uzyskać więcej informacji o warstwie kanału, zobacz [rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Omówienie  
 Tworzy model usługi czasu wykonywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, które składają się z następujących czynności:  
  
-   Implementacja automatycznie wygenerowanego klienta kontraktu usługi, która włącza wywołań w kodzie aplikacji w komunikatach wychodzących i zamienia wiadomości odpowiedzi w danych wyjściowych, parametrów i zwracanych wartości, które można pobrać aplikacji.  
  
-   Implementacja interfejsu kontroli (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>) czy grupowanie różnych interfejsów i zapewnia dostęp do funkcji, głównie możliwość zamknięcia sesji klienta i usuwania kanału kontroli.  
  
-   Kanału klienta, który jest oparty na podstawie konfiguracji ustawień określonych przez używane powiązanie.  
  
 Aplikacje można tworzyć takich klientów na żądanie, za pośrednictwem <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> lub przez tworzenie wystąpienia <xref:System.ServiceModel.ClientBase%601> klasie pochodnej, ponieważ jest ona generowana przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Te klasy klienta wbudowane gotowe Hermetyzowanie i delegować do implementacji kanału klienta, który dynamicznie jest tworzony przez <xref:System.ServiceModel.ChannelFactory>. W związku z tym kanałem klienta i fabryki kanałów, która je tworzy są centralny punkt istotnej dla tej dyskusji.  
  
## <a name="client-objects-and-client-channels"></a>Obiekty klienta i kanały klienta  
 Podstawowy interfejs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów jest <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejsu, który udostępnia podstawowe funkcje klienta, a także komunikacji podstawowe funkcje obiektu <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, funkcje kontekstu <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>i rozszerzalny zachowanie <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.IClientChannel> Interfejsu, jednak nie definiuje kontrakt usługi. Te są zadeklarowane przy użyciu interfejsu kontraktu usługi (zwykle generowane na podstawie metadanych usługi za pomocą narzędzia, takiego jak [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typy klientów rozszerzyć zarówno <xref:System.ServiceModel.IClientChannel> i interfejsu kontraktu usługi docelowej, aby umożliwić aplikacjom wywoływanie operacji bezpośrednio, a także zapewnia dostęp do funkcji środowiska wykonawczego po stronie klienta. Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient poda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> obiektów informacje niezbędne do utworzenia w czasie wykonywania, które można połączyć i interakcyjnie skonfigurowanego punktu końcowego usługi.  
  
 Jak wspomniano wcześniej, dwa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] typy klientów należy skonfigurować przed ich użyciem. Najprostszą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienckich typy obiektów, które pochodzą z <xref:System.ServiceModel.ClientBase%601> (lub <xref:System.ServiceModel.DuplexClientBase%601> Jeśli kontraktu usługi jest kontraktu dwukierunkowego). Można utworzyć te typy, za pomocą konstruktora, skonfigurować programowo, lub za pomocą pliku konfiguracji, a następnie wywołać bezpośrednio do wywołania operacji usługi. Aby uzyskać ogólne omówienie <xref:System.ServiceModel.ClientBase%601> obiekty, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 Drugi typ jest generowany w czasie wykonywania w wyniku wywołania <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metody. Aplikacje zajęto się ścisłej kontroli charakterystyki komunikacji zazwyczaj używają tego typu klienta, nazywany *obiektu kanału klienta*, ponieważ umożliwia ona więcej bezpośredniej interakcji niż podstawowy klienta środowiska wykonawczego i kanału System.  
  
## <a name="channel-factories"></a>Fabryk kanałów  
 Klasa, która jest odpowiedzialna za tworzenie podstawowych wykonawczego, który obsługuje wywołań klientów jest <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> klasy. Zarówno [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału klienta obiekty użyj <xref:System.ServiceModel.ChannelFactory%601> obiekt do tworzenia wystąpień; <xref:System.ServiceModel.ClientBase%601> obiektu pochodnego klienta hermetyzuje obsługi fabryki kanałów, ale dla różnych scenariuszach to doskonale uzasadnione korzystać bezpośrednio fabryki kanałów. Typowy scenariusz, w tym jest, jeśli chcesz wielokrotnie tworzenia nowych klientów kanałów z istniejącą fabrykę. Jeśli używasz obiektu klienta, możesz uzyskać podstawowej fabryki kanałów z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu klienta przez wywołanie metody <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> właściwości.  
  
 Ważne jest, aby pamiętać fabryk kanałów, które jest kanałów dla konfiguracji podano przed wywołaniem ich tworzyć nowe wystąpienia klasy klienta <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Po wywołaniu <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (lub <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, lub żadnej operacji na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu klienta), nie można zmodyfikować fabryki kanałów i założyć kanały do wystąpień innej usługi, nawet jeśli zmieniasz tylko element docelowy adres punktu końcowego. Jeśli chcesz utworzyć obiekt klienta lub kanału klienta z innej konfiguracji, musi najpierw utwórz nowy fabryki kanałów.  
  
 Aby uzyskać więcej informacji o różnych problemów przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanałów klienta, zobacz [dostęp do usług za pomocą klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 W poniższych dwóch sekcjach opisano tworzenie i używanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiekty kanału klienta.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Tworzenie nowego obiektu kanału klienta WCF  
 Aby zilustrować kanału klienta, przyjęto założenie, że został wygenerowany następujący kontraktu usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Aby nawiązać połączenie `ISampleService` usługi, należy użyć interfejsu kontraktu wygenerowanego bezpośrednio z fabryki kanałów (<xref:System.ServiceModel.ChannelFactory%601>). Po utworzeniu i skonfigurowaniu fabryki kanałów dla danego kontraktu, należy wywołać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metody zwracać klienta obiekty kanału, używanych do komunikowania się z `ISampleService` usługi.  
  
 Korzystając z <xref:System.ServiceModel.ChannelFactory%601> klasy przy użyciu interfejsu kontraktu usługi, należy rzutować do <xref:System.ServiceModel.IClientChannel> interfejsu jawnie otworzyć, zamknij lub przerwania kanału. Aby ułatwić pracy z narzędzia Svcutil.exe generuje również interfejs pomocnika, który implementuje zarówno interfejs kontrakt usługi i <xref:System.ServiceModel.IClientChannel> umożliwiają interakcję z infrastrukturą kanału klienta bez konieczności rzutowania. Poniższy kod przedstawia definicję pomocnika kanału klienta, który implementuje poprzedniego kontraktu usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Tworzenie nowego obiektu kanału klienta WCF  
 Do korzystania z kanału klienta do nawiązania połączenia `ISampleService` usługi, należy użyć interfejsu kontraktu wygenerowanego (lub wersji pomocnika) bezpośrednio z fabryki kanałów, przekazanie typu interfejsu kontraktu jako parametr typu. Po utworzeniu fabryki kanałów dla danego kontraktu i skonfigurowany, należy wywołać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> metody zwracać klienta obiekty kanału, używanych do komunikowania się z `ISampleService` usługi.  
  
 Podczas tworzenia obiektów kanału klienta zaimplementować <xref:System.ServiceModel.IClientChannel> i interfejsu kontraktu. W związku z tym użyciem bezpośrednio do wywoływania operacji wchodzących w interakcję z usługą, która obsługuje tej Umowy.  
  
 Różnica między przy użyciu obiektów klienta i obiekty kanału klienta jest tylko jeden formant i łatwość użycia dla deweloperów. Wielu deweloperów, którzy są doświadczenia w pracy z klas i obiektów zostanie wolą używać [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu klienta zamiast [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału klienta.  
  
 Na przykład zobacz [porady: używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
