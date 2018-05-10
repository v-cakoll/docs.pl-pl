---
title: Określanie zachowania środowiska uruchomieniowego usługi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 61a81e342a16bd298cbebef2dc733b5ec631839c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="specifying-service-run-time-behavior"></a>Określanie zachowania środowiska uruchomieniowego usługi
Po zaprojektowaniu kontrakt usługi ([projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md)) i realizowane umowy serwisowej ([Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)) można skonfigurować zachowanie operacji usługi czasu wykonywania. W tym temacie omówiono usługi dostarczane przez system i zachowania operacji i opisano, gdzie można znaleźć więcej informacji, aby utworzyć nowe zachowania. Podczas niektórych zachowań są stosowane jako atrybuty, wiele są stosowane przy użyciu pliku konfiguracji aplikacji lub programowo. Aby uzyskać więcej informacji na temat konfigurowania aplikacji usługi, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
## <a name="overview"></a>Omówienie  
 Kontrakt definiuje wejść, wyjść, typy danych i możliwości usługi tego typu. Implementowanie kontraktu usługi tworzy klasę, gdy skonfigurowano powiązania pod adresem spełnia implementuje kontrakt. Umownymi, powiązania i informacje o adresie są wszystkie znane przez klienta; bez obawy, klient nie można wprowadzić korzystanie z usługi.  
  
 Szczegóły operacji, takich jak wątkowość problemy lub Zarządzanie wystąpieniami, są jednak nieprzezroczysta dla klientów. Po wdrożeniu umowy serwisowej, dużą liczbę operacji właściwości można skonfigurować przy użyciu *zachowania*. Zachowania są obiekty, które modyfikują środowiska wykonawczego systemu Windows Communication Foundation (WCF), ustawiając właściwość modułu wykonawczego lub przez wstawienie typu dostosowania w czasie wykonywania. Aby uzyskać więcej informacji na temat modyfikowania środowiska uruchomieniowego, tworząc zachowania zdefiniowane przez użytkownika, zobacz [rozszerzanie elementu ServiceHost i warstwy modelu usług](../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md).  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> i <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> atrybuty są najczęściej przydatne zachowania i Ujawnij najczęściej wymagane funkcje operacji. Ponieważ są one atrybuty, należy je zastosować do wykonania operacji lub usługi. Innych zachowań, takich jak <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>, są zazwyczaj stosowane przy użyciu pliku konfiguracji aplikacji, chociaż można je programowo.  
  
 Ten temat zawiera omówienie <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów, w tym artykule opisano różne zakresy, w których zachowania może działać oraz ich opisy szybkie wielu zachowania dostarczane przez system w różnych zakresów, które mogą być odsetek do deweloperów usług WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute i OperationBehaviorAttribute  
 Najważniejsze zachowania są <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty, które służy do sterowania:  
  
-   Okresy istnienia wystąpienia  
  
-   Obsługa współbieżności i synchronizacji  
  
-   Zachowania konfiguracji  
  
-   Zachowanie transakcji  
  
-   Zachowanie serializacji  
  
-   Transformacja metadanych  
  
-   Okres istnienia sesji  
  
-   Filtrowanie adresów i przetwarzanie nagłówka  
  
-   Personifikacja  
  
-   Aby korzystać z tych atrybutów, oznacz wykonania operacji lub usługi przy użyciu atrybutu odpowiednie do tego zakresu i ustaw właściwości. Na przykład następujący przykładowy kod przedstawia implementację operacji, która używa <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> wymagają, aby wywołań tej operacji obsługuje personifikacji dla właściwości.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Wiele właściwości wymagają dodatkowej pomocy z powiązania. Na przykład operacja wymaga transakcji od klienta musi być skonfigurowana do używania powiązanie, które obsługuje przesłanej transakcji.  
  
### <a name="well-known-singleton-services"></a>Dobrze znanego pojedynczego wystąpienia usług  
 Można użyć <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybuty do kontrolowania niektórych okresy istnienia, oba <xref:System.ServiceModel.InstanceContext> i obiekty usługi, które implementują operacje.  
  
 Na przykład <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość określa, jak często <xref:System.ServiceModel.InstanceContext> wydaniu i <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> i <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> właściwości formantu, kiedy zwolniony jest obiekt usługi.  
  
 Można również samodzielnie utworzyć obiektu usługi i Utwórz hosta usługi przy użyciu tego obiektu. Aby to zrobić, należy także ustawić <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.InstanceContextMode.Single> lub jest zgłaszany wyjątek, po otwarciu hosta usługi.  
  
 Użyj <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> konstruktora w celu utworzenia takiej usługi. Zapewnia alternatywę do wdrażania niestandardowego <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> po możesz podać wystąpienie określonego obiektu do użytku przez usługi singleton. Można użyć tego przeciążenia, gdy Twoje typ implementacji usługi jest trudne do skonstruowania (na przykład, jeśli nie implementuje domyślnego konstruktora publicznego, który nie ma parametrów).  
  
 Należy pamiętać, że jeśli obiekt został dostarczony do tego konstruktora, niektóre funkcje związane z do systemu Windows Communication Foundation (WCF) wystąpień zachowanie działają inaczej. Na przykład wywołanie elementu <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> nie obowiązuje, gdy wystąpienie dobrze znane obiekty została podana. Podobnie inny mechanizm wersji wystąpienia jest ignorowana. <xref:System.ServiceModel.ServiceHost> Klasy zawsze zachowuje się tak, jakby <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> ma ustawioną wartość właściwości <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> dla wszystkich operacji.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Inne usługi, punkt końcowy, kontrakt i zachowania operacji  
 Usługa zachowań, takich jak <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu, współdziałać z całej usługi. Na przykład jeśli ustawisz <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> problemów z synchronizacją wątek wewnątrz każdej operacji w tej usłudze musi obsługiwać samodzielnie. Zachowania punktu końcowego działającego przez punkt końcowy; wiele zachowania punktu końcowego dostarczane przez system to funkcji klienta. Kontrakt zachowania działają na poziomie kontraktu i zachowania operacji modyfikowania dostarczania operacji.  
  
 Wiele z tych zachowań implementowanych w atrybutach i wprowadzisz korzystać z nich, jak <xref:System.ServiceModel.ServiceBehaviorAttribute> i <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutów — dzięki zastosowaniu ich do wykonania operacji lub klasy odpowiednią usługę. Innych zachowań, takich jak <xref:System.ServiceModel.Description.ServiceMetadataBehavior> lub <xref:System.ServiceModel.Description.ServiceDebugBehavior> obiektów, są zazwyczaj stosowane przy użyciu pliku konfiguracji aplikacji, mimo że również mogą być używane programowo.  
  
 Na przykład publikacji metadanych jest konfigurowana przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiektu. Następującego pliku konfiguracji aplikacji przedstawia najbardziej typowe obciążenie.  
  
 [!code-csharp[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.cs#1)]  
  
 W poniższych sekcjach opisano wiele najbardziej przydatne zachowania dostarczane przez system, które służy do modyfikowania dostarczania środowiska uruchomieniowego usługi lub klienta. Zobacz temat odwołania do określenia sposobu używania każdej z nich.  
  
### <a name="service-behaviors"></a>Zachowania usług  
 Następujące zachowania działają na usługi.  
  
-   <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Stosowane do usługi WCF, aby wskazać, czy usługi mogą być uruchamiane [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] w trybie zgodności.  
  
-   <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Określa, jak usługa autoryzuje oświadczenia klienta.  
  
-   <xref:System.ServiceModel.Description.ServiceCredentials>. Określa poświadczenia usługi. Ta klasa umożliwia określanie poświadczeń dla usługi, takie jak certyfikat X.509.  
  
-   <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Włącza debugowanie i pomóc funkcje informacji dla usługi WCF.  
  
-   <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Określa publikację usługi metadanych i skojarzonych informacji.  
  
-   <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Określa zachowanie inspekcji zdarzeń zabezpieczeń.  
  
-   <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje ustawienia czasu wykonywania przepływności, umożliwiające dostrojenie wydajności usługi.  
  
### <a name="endpoint-behaviors"></a>Zachowania punktu końcowego  
 Następujące zachowania działać dla punktów końcowych. Wiele z tych zachowań są używane w aplikacjach klienckich.  
  
-   <xref:System.ServiceModel.CallbackBehaviorAttribute>. Konfiguruje implementacji usługi wywołania zwrotnego w aplikacji klienckiej dupleksowych.  
  
-   <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Włącza usługę debugowania dla obiektu wywołania zwrotnego WCF.  
  
-   <xref:System.ServiceModel.Description.ClientCredentials>. Zezwala użytkownikowi na konfigurowanie poświadczeń klienta i usługi, a także ustawienia uwierzytelniania poświadczenia do użycia na kliencie usługi.  
  
-   <xref:System.ServiceModel.Description.ClientViaBehavior>. Używany przez klientów, aby określić identyfikator URI (Uniform Resource) dla której należy utworzyć kanał transportu.  
  
-   <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Powoduje, że usługi WCF, aby wyłączyć `MustUnderstand` przetwarzania.  
  
-   <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Powoduje, że środowiska uruchomieniowego do użycia synchronicznego odbierania procesu dla kanałów.  
  
-   <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optymalizuje operacji odbierania dla transportów, które otrzymuje transakcyjne pomocy technicznej.  
  
### <a name="contract-behaviors"></a>Kontrakt zachowania  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Określa wymagania funkcji, które wiązania podać implementacji usługi lub klienta.  
  
### <a name="operation-behaviors"></a>Operacja zachowania  
 Następujące zachowania operacji Określanie sterowania serializacji i transakcji dla operacji.  
  
-   <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Reprezentuje zachowanie środowiska wykonawczego <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>.  
  
-   <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Określa zachowanie środowiska wykonawczego `XmlSerializer` i kojarzy ją z operacji.  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute>. Określa poziom, w którym operacji usługi akceptuje Nagłówek transakcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md)  
 [Instrukcje: tworzenie wystąpienia usługi kontroli](../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
