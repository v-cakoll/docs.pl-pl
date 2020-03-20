---
title: Określanie zachowania klienta w czasie wykonywania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f9c22d25bedc36b3515538a8785b488aaa547990
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143242"
---
# <a name="specifying-client-run-time-behavior"></a>Określanie zachowania klienta w czasie wykonywania
Klienci Programu Windows Communication Foundation (WCF), takich jak usługi Windows Communication Foundation (WCF), można skonfigurować w taki sposób, aby zmodyfikowali zachowanie w czasie wykonywania w zależności od aplikacji klienckiej. Dostępne są trzy atrybuty do określania zachowania w czasie wykonywania klienta. Obiekty wywołania zwrotnego klienta <xref:System.ServiceModel.CallbackBehaviorAttribute> <xref:System.ServiceModel.Description.CallbackDebugBehavior> dupleksu można użyć i atrybuty, aby zmodyfikować ich zachowanie w czasie wykonywania. Drugi atrybut , <xref:System.ServiceModel.Description.ClientViaBehavior>może służyć do oddzielenia logicznego miejsca docelowego od bezpośredniego miejsca docelowego sieci. Ponadto typy wywołania zwrotnego klienta dupleksu można użyć niektórych zachowań po stronie usługi. Aby uzyskać więcej informacji, zobacz [Określanie zachowania w czasie wykonywania usługi](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Korzystanie z atrybutu CallbackBehaviorAttribute  
 Można skonfigurować lub rozszerzyć zachowanie wykonywania implementacji umowy wywołania <xref:System.ServiceModel.CallbackBehaviorAttribute> zwrotnego w aplikacji klienckiej przy użyciu klasy. Ten atrybut wykonuje podobną funkcję dla klasy <xref:System.ServiceModel.ServiceBehaviorAttribute> wywołania zwrotnego jako klasa, z wyjątkiem instancing zachowanie i ustawienia transakcji.  
  
 Klasa <xref:System.ServiceModel.CallbackBehaviorAttribute> musi być stosowana do klasy, która implementuje umowy wywołania zwrotnego. Jeśli stosuje się do implementacji umowy <xref:System.InvalidOperationException> nonduplex, wyjątek jest zgłaszany w czasie wykonywania. Poniższy przykład kodu <xref:System.ServiceModel.CallbackBehaviorAttribute> pokazuje <xref:System.Threading.SynchronizationContext> klasę na obiekt wywołania zwrotnego, który używa <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> obiektu do określenia wątku <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> do marshal do, właściwość wymuszania sprawdzania poprawności wiadomości i właściwość do zwracania wyjątków jako <xref:System.ServiceModel.FaultException> obiekty do usługi do celów debugowania.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Używanie callbackDebugBehavior w celu włączenia przepływu informacji o zarządzanych wyjątkach  
 Można włączyć przepływ informacji o wyjątku zarządzanego w obiekcie wywołania zwrotnego klienta <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> z `true` powrotem do usługi do celów debugowania, ustawiając właściwość programowo lub z pliku konfiguracji aplikacji.  
  
 Zwracanie informacji o zarządzanych wyjątkach do usług może stanowić zagrożenie dla bezpieczeństwa, ponieważ szczegóły wyjątku ujawniają informacje o implementacji klienta wewnętrznego, z których mogą korzystać nieautoryzowane usługi. Ponadto chociaż <xref:System.ServiceModel.Description.CallbackDebugBehavior> właściwości można również ustawić programowo, można łatwo zapomnieć <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> o wyłączeniu podczas wdrażania.  
  
 Ze względu na związane z tym kwestie bezpieczeństwa zdecydowanie zaleca się, aby:  
  
- Plik konfiguracji aplikacji służy do ustawiania <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> wartości `true`właściwości na .  
  
- Można to zrobić tylko w scenariuszach debugowania kontrolowane.  
  
 Poniższy przykład kodu przedstawia plik konfiguracji klienta, który nakazuje WCF zwracać informacje o zarządzanym wyjątku z obiektu wywołania zwrotnego klienta w komunikatach PROTOKOŁU SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  

## <a name="using-the-clientviabehavior-behavior"></a>Korzystanie z zachowania clientviaBehavior  
 Można użyć <xref:System.ServiceModel.Description.ClientViaBehavior> tego zachowania, aby określić jednolity identyfikator zasobu, dla którego należy utworzyć kanał transportu. Użyj tego zachowania, gdy bezpośrednie miejsce docelowe sieci nie jest zamierzonym procesorem wiadomości. Umożliwia to wiele przeskoków konwersacji, gdy aplikacja wywołująca `Via` nie musi znać ostatecznego miejsca docelowego lub gdy nagłówek docelowy nie jest adresem.  
  
## <a name="see-also"></a>Zobacz też

- [Określanie zachowania środowiska uruchomieniowego usługi](specifying-service-run-time-behavior.md)
