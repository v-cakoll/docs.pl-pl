---
title: Określanie zachowania klienta w czasie wykonywania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: 075f62526ace1ac49d12e1bdec39d8df4b0a3ff1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321410"
---
# <a name="specifying-client-run-time-behavior"></a>Określanie zachowania klienta w czasie wykonywania
Klienci programu Windows Communication Foundation (WCF), np. usługi Windows Communication Foundation (WCF), można skonfigurować w celu zmodyfikowania zachowania w czasie wykonywania w celu dostosowania go do aplikacji klienckiej. Trzy atrybuty są dostępne do określenia zachowania klienta w czasie wykonywania. Obiekty wywołania zwrotnego klienta dupleksu mogą używać atrybutów <xref:System.ServiceModel.CallbackBehaviorAttribute> i <xref:System.ServiceModel.Description.CallbackDebugBehavior> do modyfikowania ich zachowania w czasie wykonywania. Innym atrybutem, <xref:System.ServiceModel.Description.ClientViaBehavior>, można użyć do oddzielenia logicznego miejsca docelowego od bezpośredniej lokalizacji docelowej sieci. Ponadto typy wywołania zwrotnego klienta dupleksowego mogą używać niektórych zachowań po stronie usług. Aby uzyskać więcej informacji, zobacz [Określanie zachowania usługi w czasie wykonywania](specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Korzystanie z CallbackBehaviorAttribute  
 Można skonfigurować lub zwiększyć zachowanie wykonywania implementacji kontraktu wywołania zwrotnego w aplikacji klienckiej przy użyciu klasy <xref:System.ServiceModel.CallbackBehaviorAttribute>. Ten atrybut wykonuje podobną funkcję dla klasy wywołania zwrotnego jako Klasa <xref:System.ServiceModel.ServiceBehaviorAttribute>, z wyjątkiem zachowań wystąpienia i ustawień transakcji.  
  
 Klasy <xref:System.ServiceModel.CallbackBehaviorAttribute> należy zastosować do klasy implementującej kontrakt wywołania zwrotnego. W przypadku zastosowania do implementacji kontraktu niedupleksowego w czasie wykonywania jest generowany wyjątek <xref:System.InvalidOperationException>. Poniższy przykład kodu przedstawia klasę <xref:System.ServiceModel.CallbackBehaviorAttribute> w obiekcie wywołania zwrotnego, który używa obiektu <xref:System.Threading.SynchronizationContext> do określenia wątku, do którego należy kierowanie, właściwość <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> w celu wymuszenia walidacji wiadomości i Właściwość <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> do zwracania wyjątków jako <xref:System.ServiceModel.FaultException> obiektów do Usługa do celów debugowania.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Włączanie przepływu informacji o zarządzanych wyjątkach przy użyciu CallbackDebugBehavior  
 Można włączyć przepływ informacji o zarządzanym wyjątku w obiekcie wywołania zwrotnego klienta z powrotem do usługi na potrzeby debugowania przez ustawienie właściwości <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> na `true` programowo lub z pliku konfiguracyjnego aplikacji.  
  
 Zwrócenie informacji o wyjątku zarządzanym do usług może stanowić zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku ujawniają informacje o wewnętrznej implementacji klienta, które mogą być używane przez nieautoryzowane usługi. Ponadto, mimo że właściwości <xref:System.ServiceModel.Description.CallbackDebugBehavior> można również skonfigurować programowo, można łatwo zapomnieć, aby wyłączyć <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> podczas wdrażania.  
  
 Ze względu na problemy związane z bezpieczeństwem zdecydowanie zaleca się, aby:  
  
- Użyj pliku konfiguracji aplikacji, aby ustawić wartość właściwości <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> na `true`.  
  
- Można to zrobić tylko w scenariuszach z kontrolowanym debugowaniem.  
  
 Poniższy przykład kodu przedstawia plik konfiguracji klienta, który instruuje program WCF, aby zwracał informacje o zarządzanym wyjątku z obiektu wywołania zwrotnego klienta w komunikatach protokołu SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Korzystanie z zachowania ClientViaBehavior  
 Możesz użyć zachowania <xref:System.ServiceModel.Description.ClientViaBehavior>, aby określić Uniform Resource Identifier, dla którego należy utworzyć kanał transportu. Użyj tego zachowania, gdy bezpośrednie miejsce docelowe sieci nie jest zamierzonym procesorem komunikatu. Umożliwia to konwersacje z wieloma przeskokami, gdy aplikacja wywołująca nie musi znać ostatecznego miejsca docelowego lub gdy nagłówek `Via` docelowy nie jest adresem.  
  
## <a name="see-also"></a>Zobacz także

- [Określanie zachowania środowiska uruchomieniowego usługi](specifying-service-run-time-behavior.md)
