---
title: Określanie zachowania środowiska uruchomieniowego usługi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5c5450ea-6af1-4b75-a267-613d0ac54707
ms.openlocfilehash: 246f16cee85633499a6a1c200e608ee7bccf133c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243105"
---
# <a name="specifying-service-run-time-behavior"></a>Określanie zachowania środowiska uruchomieniowego usługi
Po zaprojektowaniu umowy serwisowej[(Projektowanie kontraktów serwisowych)](designing-service-contracts.md)i zaimplementowaniu umowy serwisowej[(Implementowanie umów serwisowych)](implementing-service-contracts.md)można skonfigurować zachowanie operacji środowiska wykonawczego usługi. W tym temacie omówiono zachowania usługi i operacji świadczonych przez system i opisano, gdzie można znaleźć więcej informacji, aby utworzyć nowe zachowania. Podczas gdy niektóre zachowania są stosowane jako atrybuty, wiele z nich są stosowane przy użyciu pliku konfiguracji aplikacji lub programowo. Aby uzyskać więcej informacji na temat konfigurowania aplikacji usługi, zobacz [Konfigurowanie usług](configuring-services.md).  
  
## <a name="overview"></a>Omówienie  
 Kontrakt definiuje dane wejściowe, dane wyjściowe, typy danych i możliwości usługi tego typu. Implementacja umowy serwisowej tworzy klasę, która po skonfigurowaniu z powiązaniem pod adresem spełnia kontrakt, który implementuje. Informacje o umowie, oprawie i adresie są znane klientowi; bez nich klient nie może korzystać z usługi.  
  
 Jednak szczegóły operacji, takie jak problemy z wątkami lub zarządzanie wystąpieniami, są nieprzezroczyste dla klientów. Po zaimplementacji umowy serwisowej można skonfigurować dużą liczbę cech operacji przy użyciu *zachowań*. Zachowania są obiektami, które modyfikują środowisko uruchomieniowe Programu Windows Communication Foundation (WCF) przez ustawienie właściwości środowiska wykonawczego lub przez wstawienie typu dostosowywania do środowiska wykonawczego. Aby uzyskać więcej informacji na temat modyfikowania środowiska uruchomieniowego przez tworzenie zachowań zdefiniowanych przez użytkownika, zobacz [Rozszerzanie usługi ServiceHost i warstwa modelu usługi](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 I <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> <xref:System.ServiceModel.OperationBehaviorAttribute?displayProperty=nameWithType> atrybuty są najbardziej przydatne zachowania i uwidaczniają najczęściej żądane funkcje operacji. Ponieważ są one atrybuty, należy zastosować je do usługi lub implementacji operacji. Inne zachowania, takie <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> jak <xref:System.ServiceModel.Description.ServiceDebugBehavior?displayProperty=nameWithType>lub , są zazwyczaj stosowane przy użyciu pliku konfiguracji aplikacji, chociaż można ich używać programowo.  
  
 Ten temat zawiera <xref:System.ServiceModel.ServiceBehaviorAttribute> omówienie <xref:System.ServiceModel.OperationBehaviorAttribute> i atrybuty, opisuje różne zakresy, w których zachowania mogą działać i zawiera szybki opis wielu zachowań dostarczonych przez system w różnych zakresach, które mogą być interesujące dla deweloperów WCF.  
  
## <a name="servicebehaviorattribute-and-operationbehaviorattribute"></a>ServiceBehaviorAttribute i OperationBehaviorAttribute  
 Najważniejsze zachowania to <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybuty <xref:System.ServiceModel.OperationBehaviorAttribute> i, których można kontrolować:  
  
- Okresy istnienia instancji  
  
- Obsługa współbieżności i synchronizacji  
  
- Zachowanie konfiguracji  
  
- Zachowanie transakcji  
  
- Zachowanie serializacji  
  
- Transformacja metadanych  
  
- Okres istnienia sesji  
  
- Filtrowanie adresów i przetwarzanie nagłówków  
  
- Personifikacja  
  
- Aby użyć tych atrybutów, oznacz implementację usługi lub operacji atrybutem odpowiednim dla tego zakresu i ustaw właściwości. Na przykład w poniższym przykładzie kodu pokazano <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A?displayProperty=nameWithType> implementację operacji, która używa właściwości, aby wymagać, aby wywołania tej operacji obsługi personifikacji.  
  
 [!code-csharp[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/operationbehaviorattribute_impersonation/cs/services.cs#1)]
 [!code-vb[OperationBehaviorAttribute_Impersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationbehaviorattribute_impersonation/vb/services.vb#1)]  
  
 Wiele właściwości wymagają dodatkowej obsługi z powiązania. Na przykład operacja, która wymaga transakcji od klienta musi być skonfigurowana do używania powiązania, które obsługuje transakcje przepływowe.  
  
### <a name="well-known-singleton-services"></a>Dobrze znane usługi Singleton  
 Za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutów i <xref:System.ServiceModel.OperationBehaviorAttribute> do kontrolowania niektórych <xref:System.ServiceModel.InstanceContext> okresów istnienia, zarówno obiektów usługi, jak i obiektów usługi, które implementują operacje.  
  
 Na przykład <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> właściwość kontroluje, <xref:System.ServiceModel.InstanceContext> jak często <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> jest <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> zwalniany i właściwości kontroli, gdy obiekt usługi jest zwolniony.  
  
 Można jednak również utworzyć obiekt usługi samodzielnie i utworzyć hosta usługi przy użyciu tego obiektu. Aby to zrobić, należy <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> również <xref:System.ServiceModel.InstanceContextMode.Single> ustawić właściwość lub wyjątek jest zgłaszany po otwarciu hosta usługi.  
  
 Użyj <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29> konstruktora, aby utworzyć taką usługę. Stanowi alternatywę dla implementowania <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> niestandardowego, gdy chcesz podać wystąpienie określonego obiektu do użycia przez usługę singleton. Można użyć tego przeciążenia, gdy typ implementacji usługi jest trudne do skonstruowania (na przykład, jeśli nie implementuje bezwametrycznego konstruktora publicznego).
  
 Należy zauważyć, że gdy obiekt jest dostarczany do tego konstruktora, niektóre funkcje związane z Windows Communication Foundation (WCF) zachowanie instancing działać inaczej. Na przykład <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> wywołanie nie ma wpływu, gdy znajduje się dobrze znane wystąpienie obiektu. Podobnie każdy inny mechanizm zwalniania wystąpienia jest ignorowany. Klasa <xref:System.ServiceModel.ServiceHost> zawsze zachowuje się <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> tak, jakby <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> właściwość jest ustawiona dla wszystkich operacji.  
  
## <a name="other-service-endpoint-contract-and-operation-behaviors"></a>Inne zachowania usługi, punktu końcowego, kontraktu i operacji  
 Zachowania usługi, takie <xref:System.ServiceModel.ServiceBehaviorAttribute> jak atrybut, działają w całej usłudze. Na przykład jeśli <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> ustawisz <xref:System.ServiceModel.ConcurrencyMode.Multiple?displayProperty=nameWithType> właściwość, należy samodzielnie obsługiwać problemy z synchronizacją wątków wewnątrz każdej operacji w tej usłudze. Zachowania punktu końcowego działają w całym punkcie końcowym; wiele zachowań punktu końcowego dostarczonych przez system są dla funkcji klienta. Zachowania kontraktów działają na poziomie kontraktu, a zachowania operacji modyfikują dostarczanie operacji.  
  
 Wiele z tych zachowań są implementowane na atrybuty i <xref:System.ServiceModel.ServiceBehaviorAttribute> można <xref:System.ServiceModel.OperationBehaviorAttribute> z nich korzystać, jak to zrobić i atrybuty — stosując je do odpowiedniej klasy usługi lub implementacji operacji. Inne zachowania, takie <xref:System.ServiceModel.Description.ServiceMetadataBehavior> jak <xref:System.ServiceModel.Description.ServiceDebugBehavior> lub obiekty, są zazwyczaj stosowane przy użyciu pliku konfiguracji aplikacji, chociaż mogą być również używane programowo.  
  
 Na przykład publikacja metadanych jest konfigurowana przy użyciu <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiektu. Następujący plik konfiguracji aplikacji zawiera najczęściej występujące użycie.  
  
 [!code-xml[ServiceMetadataBehavior#1](../../../samples/snippets/csharp/VS_Snippets_CFX/servicemetadatabehavior/cs/hostapplication.exe.config#1)]  
  
 W poniższych sekcjach opisano wiele najbardziej przydatnych zachowań dostarczonych przez system, których można użyć do zmodyfikowania dostarczania środowiska uruchomieniowego usługi lub klienta. Zobacz temat odwołania, aby określić, jak używać każdego z nich.  
  
### <a name="service-behaviors"></a>Zachowania usług  
 Następujące zachowania działają na usługach.  
  
- <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>. Zastosowane do usługi WCF, aby wskazać, czy ta usługa może być uruchamiana w trybie zgodności ASP.NET.  
  
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>. Określa, jak usługa autoryzuje oświadczenia klientów.  
  
- <xref:System.ServiceModel.Description.ServiceCredentials>. Konfiguruje poświadczenia usługi. Ta klasa służy do określania poświadczeń dla usługi, takich jak certyfikat X.509.  
  
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>. Włącza funkcje debugowania i pomocy dla usługi WCF.  
  
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>. Steruje publikacją metadanych usługi i skojarzonych informacji.  
  
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>. Określa zachowanie inspekcji zdarzeń zabezpieczeń.  
  
- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>. Konfiguruje ustawienia przepływności w czasie wykonywania, które umożliwiają dostosowanie wydajności usługi.  
  
### <a name="endpoint-behaviors"></a>Zachowania punktów końcowych  
 Następujące zachowania działają na punktach końcowych. Wiele z tych zachowań są używane w aplikacjach klienckich.  
  
- <xref:System.ServiceModel.CallbackBehaviorAttribute>. Konfiguruje implementację usługi wywołania zwrotnego w aplikacji klienckiej dupleksu.  
  
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>. Umożliwia debugowanie usługi dla obiektu wywołania zwrotnego WCF.  
  
- <xref:System.ServiceModel.Description.ClientCredentials>. Umożliwia użytkownikowi skonfigurowanie poświadczeń klienta i usługi, a także ustawień uwierzytelniania poświadczeń usługi do użycia na kliencie.  
  
- <xref:System.ServiceModel.Description.ClientViaBehavior>. Używane przez klientów do określania jednolitego identyfikatora zasobów (URI), dla którego należy utworzyć kanał transportu.  
  
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>. Nakazuje WCF, `MustUnderstand` aby wyłączyć przetwarzanie.  
  
- <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>. Nakazuje środowiska wykonawczego, aby używać synchroniczowego procesu odbierania dla kanałów.  
  
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>. Optymalizuje operacje odbierania dla transportów, które obsługują odbiera transakcyjnych.  
  
### <a name="contract-behaviors"></a>Zachowania kontraktowe  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>. Określa wymagania funkcji, które powiązania muszą zapewnić do implementacji usługi lub klienta.  
  
### <a name="operation-behaviors"></a>Zachowania operacyjne  
 Następujące zachowania operacji określają formantów serializacji i transakcji dla operacji.  
  
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Reprezentuje zachowanie w czasie <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>wykonywania .  
  
- <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior>. Steruje zachowaniem `XmlSerializer` w czasie wykonywania i kojarzy go z operacją.  
  
- <xref:System.ServiceModel.TransactionFlowAttribute>. Określa poziom, na którym operacja usługi akceptuje nagłówek transakcji.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usług](configuring-services.md)
- [Instrukcje: tworzenie wystąpienia usługi kontroli](./feature-details/how-to-control-service-instancing.md)
