---
title: Architektura klienta
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: c873368b82551312d203eb28d208eb6e3f50c89b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587004"
---
# <a name="client-architecture"></a>Architektura klienta
Aplikacje używają obiektów klienta Windows Communication Foundation (WCF) do wywoływania operacji usługi. Ten temat zawiera omówienie obiektów klienta WCF, kanałów klienta WCF i ich relacji z architekturą źródłową. Aby zapoznać się z podstawowymi omówieniem obiektów klienta WCF, zobacz [Omówienie klienta programu WCF](../wcf-client-overview.md). Aby uzyskać więcej informacji na temat warstwy kanału, zobacz [Rozszerzanie warstwy kanału](../extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Omówienie  
 W czasie wykonywania modelu usług tworzone są klientów WCF, które składają się z następujących elementów:  
  
- Automatycznie wygenerowana implementacja klienta kontraktu usługi, która włącza wywołania z kodu aplikacji do komunikatów wychodzących, i włącza komunikaty odpowiedzi do parametrów wyjściowych i zwracanych wartości, które aplikacja może pobrać.  
  
- Implementacja interfejsu sterowania ( <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> ), który grupuje różne interfejsy i zapewnia dostęp do funkcji kontroli, w szczególności możliwość zamykania sesji klienta i usuwania kanału.  
  
- Kanał klienta oparty na ustawieniach konfiguracji określonych przez użyte powiązanie.  
  
 Aplikacje mogą tworzyć takich klientów na żądanie przez <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> lub przez utworzenie wystąpienia <xref:System.ServiceModel.ClientBase%601> klasy pochodnej, która jest generowana przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Te gotowe klasy klienckie hermetyzują i deleguje do implementacji kanału klienta, który jest dynamicznie tworzony przez <xref:System.ServiceModel.ChannelFactory> . W związku z tym kanał klienta i fabryka kanałów, które wytwarzają je, są punktem orientacyjnym zainteresowania tej dyskusji.  
  
## <a name="client-objects-and-client-channels"></a>Obiekty klienta i kanały klienta  
 Podstawowym interfejsem klientów WCF jest <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejs, który udostępnia podstawowe funkcje klienta, a także podstawowe funkcje obiektów komunikacyjnych <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> , funkcje kontekstu <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType> i rozszerzalne zachowanie <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType> .  
  
 <xref:System.ServiceModel.IClientChannel>Jednak interfejs nie definiuje samego kontraktu usługi. Są one deklarowane przez interfejs kontraktu usługi (zwykle generowany z metadanych usługi przy użyciu narzędzia, takiego jak narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)). Typy klientów WCF umożliwiają rozbudowa <xref:System.ServiceModel.IClientChannel> i interfejs kontraktu usługi docelowej, aby umożliwić aplikacjom bezpośrednie wywoływanie operacji, a także dostęp do funkcji czasu wykonywania po stronie klienta. Tworzenie klienta WCF zapewnia <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> obiektom WCF informacje niezbędne do utworzenia czasu wykonywania, który może nawiązać połączenie i korzystać ze skonfigurowanego punktu końcowego usługi.  
  
 Jak wspomniano wcześniej, dwa typy klientów WCF muszą zostać skonfigurowane, aby można było ich używać. Najprostszym typem klienta WCF są obiekty, które pochodzą od <xref:System.ServiceModel.ClientBase%601> (lub <xref:System.ServiceModel.DuplexClientBase%601> Jeśli kontrakt usługi jest umową dupleksową). Te typy można utworzyć za pomocą konstruktora, skonfigurowanego programowo lub za pomocą pliku konfiguracji, a następnie wywołać bezpośrednio w celu wywołania operacji usługi. Aby zapoznać się z podstawowymi omówieniem <xref:System.ServiceModel.ClientBase%601> obiektów, zobacz [Omówienie klienta programu WCF](../wcf-client-overview.md).  
  
 Drugi typ jest generowany w czasie wykonywania z wywołania <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metody. Aplikacje mające ścisłą kontrolę nad danymi komunikacyjnymi zazwyczaj używają tego typu klienta, nazywanego *obiektem kanału klienta*, ponieważ umożliwia ona bardziej bezpośrednią interakcję niż podstawowy system wykonywania i kanałów w ramach klienta.  
  
## <a name="channel-factories"></a>Fabryki kanałów  
 Klasa, która jest odpowiedzialna za tworzenie bazowego czasu wykonywania, który obsługuje wywołania klienta, jest <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> klasą. Zarówno obiekty klienta WCF, jak i obiekty kanału klienta WCF używają <xref:System.ServiceModel.ChannelFactory%601> obiektu do tworzenia wystąpień; <xref:System.ServiceModel.ClientBase%601> pochodny obiekt klienta hermetyzuje obsługę fabryki kanałów, ale dla wielu scenariuszy jest doskonale rozsądna do bezpośredniego używania fabryki kanałów. Typowym scenariuszem tego jest to, że chcesz wielokrotnie tworzyć nowe kanały klienta z istniejącej fabryki. Jeśli używasz obiektu klienta, możesz uzyskać podstawową fabrykę kanałów z obiektu klienta WCF, wywołując <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> Właściwość.  
  
 Ważne jest, aby pamiętać o fabrykach kanałów, tworząc nowe wystąpienia kanałów klientów dla danej konfiguracji przed wywołaniem <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> . Po wywołaniu <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (lub <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> , <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType> lub dowolnej operacji na obiekcie klienta WCF) nie można zmodyfikować fabryki kanałów i oczekiwać na uzyskanie kanałów do różnych wystąpień usługi, nawet jeśli zmieniasz tylko docelowy adres punktu końcowego. Jeśli chcesz utworzyć obiekt klienta lub kanał klienta z inną konfiguracją, musisz najpierw utworzyć nową fabrykę kanału.  
  
 Aby uzyskać więcej informacji o różnych problemach przy użyciu obiektów klienta WCF i kanałów klienta WCF, zobacz [Uzyskiwanie dostępu do usług za pomocą klienta WCF](accessing-services-using-a-client.md).  
  
 W poniższych dwóch sekcjach opisano tworzenie i używanie obiektów kanału klienta WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Tworzenie nowego obiektu kanału klienta WCF  
 Aby zilustrować użycie kanału klienta, założono, że został wygenerowany następujący kontrakt usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Aby nawiązać połączenie z `ISampleService` usługą, użyj wygenerowanego interfejsu kontraktu bezpośrednio z fabryką kanałów ( <xref:System.ServiceModel.ChannelFactory%601> ). Po utworzeniu i skonfigurowaniu fabryki kanałów dla konkretnej kontraktu można wywołać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metodę w celu zwrócenia obiektów kanału klienta, których można użyć do komunikowania się z `ISampleService` usługą.  
  
 W przypadku używania <xref:System.ServiceModel.ChannelFactory%601> klasy z interfejsem kontraktu usługi należy rzutować do <xref:System.ServiceModel.IClientChannel> interfejsu w celu jawnego otwierania, zamykania lub przerywania kanału. Aby ułatwić pracę z programem, narzędzie Svcutil. exe generuje również interfejs pomocnika, który implementuje interfejs kontraktu usługi i umożliwia <xref:System.ServiceModel.IClientChannel> Korzystanie z infrastruktury kanału klienta bez konieczności rzutowania. Poniższy kod przedstawia definicję kanału pomocnika klienta, który implementuje poprzedni kontrakt usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Tworzenie nowego obiektu kanału klienta WCF  
 Aby użyć kanału klienta do nawiązania połączenia z `ISampleService` usługą, użyj wygenerowanego interfejsu kontraktu (lub wersji pomocnika) bezpośrednio z fabryką kanałów, przekazując typ interfejsu kontraktu jako parametr typu. Po utworzeniu i skonfigurowaniu fabryki kanałów dla danego kontraktu można wywołać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> metodę, aby zwracała obiekty kanału klienta, których można użyć do komunikowania się z `ISampleService` usługą.  
  
 Po utworzeniu obiekty kanału klienta implementują <xref:System.ServiceModel.IClientChannel> i interfejs kontraktu. Z tego względu można używać ich bezpośrednio do wywoływania operacji, które współdziałają z usługą, która obsługuje ten kontrakt.  
  
 Różnica między użyciem obiektów klienta i obiektów kanału klienta jest tylko jedną z formantów i łatwość użycia dla deweloperów. Wielu deweloperów, którzy chcą pracować z klasami i obiektami, woli użyć obiektu klienta WCF zamiast kanału klienta WCF.  
  
 Aby zapoznać się z przykładem, zobacz [How to: use an ChannelFactory](how-to-use-the-channelfactory.md).
