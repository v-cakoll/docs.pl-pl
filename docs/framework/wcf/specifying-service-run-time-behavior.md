---
title: Określanie zachowania środowiska uruchomieniowego usługi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 759a5dd4cecbaf804d1ccf29fa504c2f5e1ad7f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566744"
---
# <a name="specifying-service-run-time-behavior"></a>Określanie zachowania środowiska uruchomieniowego usługi
Po zaprojektowaniu kontraktu usługi ([projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)) i realizowane umowy serwisowej ([Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)) można skonfigurować zachowanie operacji środowisko wykonawcze usług. Ten temat zawiera omówienie usług dostarczanych przez system i zachowania operacji i opisano, gdzie można znaleźć więcej informacji, aby utworzyć nowe zachowania. Podczas gdy niektóre zachowania są stosowane jako atrybuty, wiele są stosowane przy użyciu pliku konfiguracji aplikacji lub programowo. Aby uzyskać więcej informacji na temat konfigurowania aplikacji usługi, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Omówienie  
 Kontrakt definiuje danych wejściowych, danych wyjściowych, typów danych i możliwości usługi tego typu. Implementowanie kontraktu usługi tworzy klasę, gdy skonfigurowano powiązania pod adresem spełnia kontraktu implementuje. Zobowiązania umowne, powiązania oraz informacji dotyczących adresów są wszystkie znane przez klienta; bez nich, klient nie może wprowadzać korzystanie z usługi.  
  
 Szczegóły operacji, takich jak wątki problemy lub Zarządzanie wystąpieniami są jednak nieprzezroczysta dla klientów. Po wdrożeniu usługi kontraktu usługi, można skonfigurować dużą liczbę operacji właściwości, za pomocą *zachowania*. Zachowania są obiekty, które modyfikują środowiska uruchomieniowego Windows Communication Foundation (WCF), ustawiając właściwość środowiska uruchomieniowego lub przez wstawienie typu dostosowania w czasie wykonywania. Aby uzyskać więcej informacji na temat modyfikowania środowiska uruchomieniowego, tworząc zachowań zdefiniowanych przez użytkownika, zobacz [rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> i <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> atrybuty są najczęściej przydatne zachowania i udostępniają najczęściej wymagane funkcje operacji. Ponieważ są one atrybutów, można je zastosować do implementacji usługi lub operacji. Innych zachowań, takich jak <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, są zazwyczaj stosowane przy użyciu pliku konfiguracji aplikacji, chociaż można używać je programowo.  
  
 Ten temat zawiera omówienie <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów, w tym artykule opisano różne zakresy, w których może działać zachowania i zawiera krótki opis wielu dostarczane przez system zachowań w różnych zakresach, które mogą być zainteresowania deweloperów usług WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute i gdy  
 Czy najważniejszych zachowań <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów, których można użyć do sterowania:  
  
-   Okresy istnienia wystąpienia  
  
-   Obsługa współbieżności i synchronizacji  
  
-   Zachowanie konfiguracji  
  
-   Zachowanie transakcji  
  
-   Zachowanie serializacji  
  
-   Przekształcenie metadanych  
  
-   Okres istnienia sesji  
  
-   Filtrowanie adresów i przetwarzanie nagłówka  
  
-   Personifikacja  
  
-   Aby korzystać z tych atrybutów, oznacz implementacji usługi lub operacji za pomocą atrybutu odpowiednie dla danego zakresu, a następnie ustaw właściwości. Na przykład, poniższy kod przedstawia implementację operacji, która używa <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> właściwości, aby wymagać, że obiekty wywołujące tej operacji obsługuje personifikacji.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Wiele właściwości potrzebujesz dodatkowej pomocy technicznej firmy powiązania. Na przykład operacja, która wymaga transakcji od klienta musi być skonfigurowany do użycia powiązania, który obsługuje transakcje przesłanej.  
  
### <a name="well-known-singleton-services"></a>Usługami Singleton dobrze znane  
 Możesz użyć <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty kontrolować pewne okresy istnienia, oba <xref:System.ServiceModel.InstanceContext> i obiekty usługi, które implementują operacji.  
  
 Na przykład <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość określa, jak często <xref:System.ServiceModel.InstanceContext> jest zwalniana, a <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> właściwości formantu, kiedy obiekt usługi jest zwolniony.  
  
 Można również utworzyć obiekt usługi samodzielnie i Utwórz hosta usługi przy użyciu tego obiektu. Aby to zrobić, należy także ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.InstanceContextMode.Single> lub wyjątek jest zgłaszany, gdy host usługi jest otwarty.  
  
 Użyj <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> Konstruktor do tworzenia takiej usługi. Jego stanowi alternatywę dla implementacji niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> po możesz podać wystąpienie określonego obiektu do użytku przez usługi singleton. Możesz użyć tego przeciążenia danego typu wdrożenia usługi jest trudne do konstruowania (na przykład, jeśli nie implementuje domyślnego konstruktora publicznego, który nie ma parametrów).  
  
 Należy pamiętać, że jeśli obiekt znajduje się do tego konstruktora, niektóre funkcje związane z do Windows Communication Foundation (WCF) wystąpień zachowanie działają inaczej. Na przykład, wywołanie <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nie obowiązuje, gdy wystąpienie obiektu dobrze znanych została podana. Podobnie inny mechanizm wersji wystąpienia jest ignorowany. <xref:System.ServiceModel.ServiceHost> Klasy zawsze zachowuje się tak, jakby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> właściwość jest ustawiona na <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> dla wszystkich operacji.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Inne usługi, punkt końcowy, kontrakt i zachowania operacji  
 Usługa zachowań, takich jak <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu, działającego przez całą usługę. Na przykład jeśli ustawisz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> właściwość <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> problemów z synchronizacją wątku wewnątrz każdej operacji w tej usłudze musi obsługiwać samodzielnie. Zachowań punktu końcowego działającego przez punkt końcowy; wiele zachowań dostarczane przez system punktu końcowego to funkcji klienta. Kontrakt zachowania działają na poziomie kontraktu i zachowania operację Modyfikuj dostarczania operacji.  
  
 Wiele z tych zachowań są implementowane w atrybutach i wprowadzisz korzystać z nich, tak jak <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów — dzięki zastosowaniu ich do implementacji klasy lub operacji odpowiednią usługę. Innych zachowań, takich jak <xref:System.ServiceModel.Description.ServiceMetadataBehavior> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior> obiektów, są zazwyczaj stosowane przy użyciu pliku konfiguracji aplikacji, jednak również mogą być używane programowo.  
  
 Na przykład publikacji metadanych jest konfigurowana przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiektu. Następujący plik konfiguracji aplikacji przedstawia najbardziej typowe obciążenie.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 W poniższych sekcjach opisano wiele najbardziej przydatne zachowań dostarczane przez system, które służy do modyfikowania dostarczania środowiska uruchomieniowego usługi lub klienta. Zobacz temat referencyjny, aby określić sposób użycia każdej z nich.  
  
### <a name="service-behaviors"></a>Zachowania usług  
 Następujące zachowania działają w usługach.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Stosowane do usługi WCF w celu wskazania, czy usługi mogą być uruchamiane w [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] w trybie zgodności.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Określa, jak usługa autoryzuje oświadczenia klienta.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Określa poświadczenia usługi. Użyj tej klasy, aby określić poświadczenia dla usługi, takie jak certyfikat X.509.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Włącza debugowanie i Pomóż funkcje informacji dla usługi WCF.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Określa publikację usługi metadanych i skojarzonych informacji.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Określa zachowanie inspekcji zdarzeń zabezpieczeń.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje ustawienia środowiska wykonawczego przepływności, umożliwiające dostosowywanie wydajności usługi.  
  
### <a name="endpoint-behaviors"></a>Zachowań punktu końcowego  
 Następujące zachowania działają w punktach końcowych. Wiele z tych zachowań są używane w aplikacjach klienckich.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Konfiguruje implementacji usługi wywołania zwrotnego w aplikacji klienckiej dwukierunkowego.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Włącza usługę debugowania dla obiektu wywołania zwrotnego WCF.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Zezwala użytkownikowi na konfigurowanie poświadczeń klienta i usługi, a także usługi ustawienia uwierzytelniania poświadczeń do użycia na komputerze klienckim.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Używane przez klientów, aby określić identyfikator (URI) dla której należy utworzyć kanał transportu.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Powoduje, że usługi WCF w celu wyłączenia `MustUnderstand` przetwarzania.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Powoduje, że środowiska uruchomieniowego do użycia przez synchroniczny otrzymywać proces kanałów.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optymalizuje operacji odbierania dla transportu, które odbiera transakcyjnych pomocy technicznej.  
  
### <a name="contract-behaviors"></a>Zachowania kontraktu  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Określa wymagania dotyczące funkcji, które powiązania musi dostarczyć implementację usługi lub klienta.  
  
### <a name="operation-behaviors"></a>Operacja zachowania  
 Następujące zachowania operacji Określanie sterowania serializacji i transakcji, dla operacji.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Reprezentuje zachowanie środowiska wykonawczego <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Kontroluje zachowanie w czasie wykonywania `XmlSerializer` i kojarzy ją z operacją.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Określa poziom, w którym operacji usługi akceptuje Nagłówek transakcji.  
  
## <a name="see-also"></a>Zobacz także
- [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md)
- [Instrukcje: Tworzenie wystąpienia usługi kontroli](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
