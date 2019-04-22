---
title: Określanie zachowania klienta w czasie wykonywania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: f750978eaa617a5505bb27a1535797320a76b0d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164375"
---
# <a name="specifying-client-run-time-behavior"></a>Określanie zachowania klienta w czasie wykonywania
Klienci Windows Communication Foundation (WCF), podobnie jak usługi Windows Communication Foundation (WCF), można skonfigurować do modyfikowania zachowania w czasie wykonywania do własnych aplikacji klienckiej. Trzy atrybuty są dostępne dla Określanie zachowania klienta w czasie wykonywania. Obiekty klienta dwustronnego wywołania zwrotnego można użyć <xref:System.ServiceModel.CallbackBehaviorAttribute> i <xref:System.ServiceModel.Description.CallbackDebugBehavior> atrybutów, które mają modyfikowanie ich zachowania w czasie wykonywania. Ten atrybut <xref:System.ServiceModel.Description.ClientViaBehavior>, może służyć do oddzielania logiczne miejsce docelowe z docelowym bezpośredniej sieci. Ponadto klienta dwustronnego wywołania zwrotnego typów mogą korzystać z niektórych zachowań po stronie usługi. Aby uzyskać więcej informacji, zobacz [Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Za pomocą CallbackBehaviorAttribute  
 Można skonfigurować lub rozszerzanie zachowanie wykonania implementacji kontrakt wywołania zwrotnego, w aplikacji klienckiej za pomocą <xref:System.ServiceModel.CallbackBehaviorAttribute> klasy. Ten atrybut pełni funkcję podobną do klasy wywołania zwrotnego, co <xref:System.ServiceModel.ServiceBehaviorAttribute> klasy, z wyjątkiem tworzenia wystąpienia ustawienia zachowania i transakcji.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> Klasy muszą być stosowane do klasy, który implementuje ten kontrakt wywołania zwrotnego. Jeśli stosowane do implementacji obsługującej zamówienia, <xref:System.InvalidOperationException> wyjątek w czasie wykonywania. Poniższy kod przedstawia przykład <xref:System.ServiceModel.CallbackBehaviorAttribute> klasy na obiektu wywołania zwrotnego, który używa <xref:System.Threading.SynchronizationContext> obiektu wątku do organizowania, <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> właściwości, aby wymusić komunikat sprawdzania poprawności, a <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> właściwości do zwrócenia Wyjątki jako <xref:System.ServiceModel.FaultException> obiektów do usługi w celu debugowania.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Włącz przepływ informacji o zarządzanych wyjątku przy użyciu CallbackDebugBehavior  
 Można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania, ustawiając <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwość `true` pliku albo programowo, albo z konfiguracji aplikacji.  
  
 Zwraca informacje o zarządzanym wyjątku do usług może stanowić zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku spowodować ujawnienie informacji o wewnętrznego klienta można użyć implementacji nieautoryzowane usługi. Ponadto mimo że <xref:System.ServiceModel.Description.CallbackDebugBehavior> właściwości można także programowo ustawić, można łatwo zapomnieć o wyłączenie <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> podczas wdrażania.  
  
 Ze względu na zagadnień związanych z zabezpieczeniami zdecydowanie zalecane jest:  
  
-   Przy użyciu pliku konfiguracji aplikacji można ustawić wartość <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwość `true`.  
  
-   Możesz robić tylko w kontrolowany debugowania scenariuszy.  
  
 Poniższy przykład kodu pokazuje klienta pliku konfiguracji, która instruuje usługę WCF, aby zwrócić informacje o zarządzanym wyjątku w kliencie obiektu wywołania zwrotnego w komunikaty protokołu SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Używając zachowania ClientViaBehavior  
 Możesz użyć <xref:System.ServiceModel.Description.ClientViaBehavior> zachowanie, aby określić Uniform Resource Identifier, dla którego należy utworzyć kanał transportu. Należy użyć tego zachowania, gdy docelowy bezpośredniej sieci nie jest zamierzone procesora wiadomość. Dzięki temu konwersacje wielu przeskoków, gdy aplikacja wywołująca nie zna ultimate docelowego lub miejsce docelowe `Via` nagłówka nie jest adresem.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
