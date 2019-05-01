---
title: Architektura klienta
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: 4ced24f370e2ab54528c6adb2b3617d3d849e745
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781527"
---
# <a name="client-architecture"></a>Architektura klienta
Aplikacje umożliwiają wywoływanie operacji usługi obiekty klienta usługi Windows Communication Foundation (WCF). W tym temacie omówiono obiekty klienta WCF, kanały klientów usługi WCF i ich relacje w podstawowej architekturze kanału. Aby uzyskać ogólne omówienie obiekty klienta WCF, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md). Aby uzyskać więcej informacji na temat warstwy kanału, zobacz [rozszerzanie warstwy kanału](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Omówienie  
 Model usług, w czasie wykonywania tworzy klienci WCF, które składają się z następujących czynności:  
  
- Implementacja automatycznie wygenerowanego klienta kontraktu usługi, wywołania w kodzie aplikacji jest przekształcany wysyłanych wiadomości, która przekształca wiadomości odpowiedzi w danych wyjściowych parametrów i zwracanej wartości, które można pobrać aplikację.  
  
- Implementacja interfejsu kontroli (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>), grupowanie różnych interfejsów i zapewnia dostęp do kontrolowania funkcje, w szczególności możliwość zamknięcia sesji klienta i usuwania kanału.  
  
- Kanału klienta, który jest zbudowany na podstawie ustawienia konfiguracji określone przez używane powiązanie.  
  
 Aplikacje można tworzyć takich klientów na żądanie za pośrednictwem <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> lub tworząc wystąpienie <xref:System.ServiceModel.ClientBase%601> klasy pochodnej, ponieważ jest ona generowana przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). W ramach tych zajęć gotowy klienta hermetyzacji i delegować do implementacji kanału klienta, który jest dynamicznie tworzony przez <xref:System.ServiceModel.ChannelFactory>. Dlatego kanału klienta i fabryki kanałów, która je tworzy są optymalizowane znaczenie w odniesieniu do tej dyskusji.  
  
## <a name="client-objects-and-client-channels"></a>Obiekty klienta i kanały klientów  
 Podstawowy interfejs klienci WCF jest <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejs, który udostępnia podstawowe funkcje klienta, a także komunikacji podstawowe funkcje obiektu <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>, funkcje kontekstu <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>i rozszerzalny zachowanie <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.IClientChannel> Interfejsu, jednak nie definiuje kontraktu usługi, sam. Te są deklarowane przy użyciu interfejsu kontraktu usługi (zazwyczaj wygenerowany na podstawie metadanych usługi przy użyciu narzędzia, takiego jak [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)). Rozszerzanie odpowiadają typom klienta WCF, zarówno <xref:System.ServiceModel.IClientChannel> i interfejsu kontraktu usługi docelowej, aby umożliwić aplikacjom wywoływanie operacji bezpośrednio, a także mieć dostęp do funkcji wykonawczej po stronie klienta. Tworzenie klienta programu WCF zapewnia WCF<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> obiektów informacje niezbędne do utworzenia w czasie wykonywania, które umiesz nawiązywać połączenia i interakcji z skonfigurowanego punktu końcowego usługi.  
  
 Jak wspomniano wcześniej, muszą być skonfigurowane dwa typy klienta WCF, zanim będzie można ich użyć. Najprostsze typy klienta WCF są obiekty, które wynikają z <xref:System.ServiceModel.ClientBase%601> (lub <xref:System.ServiceModel.DuplexClientBase%601> przypadku kontrakt dupleksowy, kontrakt usługi). Te typy można utworzyć za pomocą konstruktora konfigurowane programowo, lub za pomocą pliku konfiguracji, a następnie wywołać bezpośrednio do wywołania operacji usługi. Aby uzyskać ogólne omówienie <xref:System.ServiceModel.ClientBase%601> obiekty, zobacz [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md).  
  
 Drugi typ jest generowany w czasie wykonywania po wywołaniu <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metody. Aplikacje, które dotyczy ścisłą kontrolę nad szczegółowe informacje na temat komunikacji zazwyczaj używają tego typu klienta o nazwie *obiektu kanału klienta*, ponieważ umożliwia bardziej bezpośrednie interakcje niż podstawowej klienta środowiska wykonawczego i kanału System.  
  
## <a name="channel-factories"></a>Fabryki kanałów  
 Klasa, która jest odpowiedzialna za tworzenie podstawowych wykonawczego obsługującego wywołania klienta jest <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> klasy. Zarówno obiekty klienta WCF, jak i klienta WCF kanału użycia obiektów <xref:System.ServiceModel.ChannelFactory%601> obiektu do utworzenia wystąpienia; <xref:System.ServiceModel.ClientBase%601> pochodnej klienta hermetyzuje obsługi fabryki kanałów, ale dla różnych scenariuszy jest idealnie do użycia Fabryka kanałów bezpośrednio. Typowy scenariusz, w tym polega na tym, jeśli chcesz regularnie tworzyć nowego klienta kanały z istniejącej fabryki. Jeśli używasz obiektu klienta podstawowej fabryki kanałów można uzyskać z obiektu klienta WCF, wywołując <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> właściwości.  
  
 Ważne jest, aby pamiętać fabryki kanałów jest kanały dla konfiguracji udostępnionych im przed wywołaniem one tworzenie nowych wystąpień klienta <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Gdy wywołujesz <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (lub <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType>, lub żadnych operacji na obiekcie klienta WCF), nie można zmodyfikować fabryki kanałów i chcą uzyskać kanałów z wystąpieniami innej usługi, nawet wtedy, gdy zmieniają się jedynie docelowy adres punktu końcowego. Jeśli chcesz utworzyć obiekt klienta lub kanałem klienta przy użyciu różnych konfiguracji należy najpierw utworzyć nowej fabryki kanałów.  
  
 Aby uzyskać więcej informacji na temat różnych problemów przy użyciu obiektów klienta WCF i kanały klientów usługi WCF zobacz [uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md).  
  
 Następujące dwie sekcje opisują stworzeniem i używaniem obiekty kanału klienta programu WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Utworzenie nowego obiektu kanału klienta WCF  
 Aby zilustrować kanału klienta, zakłada się, że następujące kontraktu usługi został wygenerowany.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Aby nawiązać połączenie `ISampleService` usługi, przy użyciu interfejsu kontraktu wygenerowanego bezpośrednio za pomocą fabryki kanałów (<xref:System.ServiceModel.ChannelFactory%601>). Po utworzeniu i skonfigurowaniu fabryki kanałów dla danego kontraktu, można wywołać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> metodę, aby zwracać obiekty kanału, służących do komunikowania się z klienta `ISampleService` usługi.  
  
 Korzystając z <xref:System.ServiceModel.ChannelFactory%601> klasy przy użyciu interfejsu kontraktu usługi, należy rzutować do <xref:System.ServiceModel.IClientChannel> interfejsu jawnie otwierać, zamknij lub Przerwij kanału. W celu ułatwienia pracy z narzędzia Svcutil.exe generuje również interfejs pomocnika, który implementuje zarówno interfejs kontrakt usługi i <xref:System.ServiceModel.IClientChannel> umożliwiające interakcję z infrastrukturą kanału klienta bez rzutowania. Poniższy kod przedstawia definicję kanału klienta pomocnika, który implementuje poprzedniego kontraktu usługi.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Utworzenie nowego obiektu kanału klienta WCF  
 Aby nawiązać połączenie przy użyciu kanału klienta `ISampleService` usługi, należy użyć interfejsu wygenerowanego kontraktu (lub wersji pomocnika) bezpośrednio za pomocą fabryki kanałów, przekazując typ interfejsu kontraktu jako parametr typu. Po utworzeniu i skonfigurowaniu fabryki kanałów dla danego kontraktu może wywołać <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> metodę, aby zwracać obiekty kanału, służących do komunikowania się z klienta `ISampleService` usługi.  
  
 Podczas tworzenia obiektów kanału klienta zaimplementować <xref:System.ServiceModel.IClientChannel> i interfejsu kontraktu. W związku z tym można ich użyć bezpośrednio do wywoływania operacji, które współdziałają z usługą, która obsługuje tej Umowy.  
  
 Różnica między obiekty klienta i kanału klienta jest tylko jeden z kontroli i łatwości użycia dla deweloperów. Wielu programistów, którzy wygodnie posługujesz się klasy i obiekty zostaną wolą używać obiektu klienta programu WCF zamiast kanału klienta programu WCF.  
  
 Aby uzyskać przykład, zobacz [jak: Używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md).
