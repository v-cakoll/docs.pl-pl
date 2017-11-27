---
title: "Określanie zachowania klienta w czasie wykonywania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3aebab3799af562d958eb8e3e83380e734fe9268
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-client-run-time-behavior"></a>Określanie zachowania klienta w czasie wykonywania
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]klientów, takie jak [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usług, można skonfigurować do modyfikowania zachowania w czasie wykonywania do własnych aplikacji klienckich. Atrybuty trzy są dostępne do określania zachowania klienta w czasie wykonywania. Obiekty klienta dwustronnego wywołania zwrotnego można użyć <xref:System.ServiceModel.CallbackBehaviorAttribute> i <xref:System.ServiceModel.Description.CallbackDebugBehavior> atrybuty do modyfikowania zachowania w czasie wykonywania. Ten atrybut <xref:System.ServiceModel.Description.ClientViaBehavior>, może służyć do rozdzielania logicznej docelowej z docelowego bezpośredniej sieci. Ponadto klienta dwustronnego wywołania zwrotnego typów mogą korzystać z niektórych zachowań po stronie serwera. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Przy użyciu CallbackBehaviorAttribute  
 Możesz skonfigurować lub rozszerzyć sposób wykonywania realizacji kontrakt wywołania zwrotnego w aplikacji klienta przy użyciu <xref:System.ServiceModel.CallbackBehaviorAttribute> klasy. Ten atrybut pełni podobną funkcję wywołania zwrotnego klasy jako <xref:System.ServiceModel.ServiceBehaviorAttribute> klasy, z wyjątkiem wystąpień ustawienia zachowania i transakcji.  
  
 <xref:System.ServiceModel.CallbackBehaviorAttribute> Klasy musi odnosić się do klasy, która implementuje kontrakt wywołania zwrotnego. Jeśli zastosowano implementacji obsługującej kontrakt <xref:System.InvalidOperationException> wyjątek w czasie wykonywania. Poniższy kod przedstawia przykład <xref:System.ServiceModel.CallbackBehaviorAttribute> klasy dla obiektu wywołania zwrotnego, który używa <xref:System.Threading.SynchronizationContext> obiektem, aby określić wątku do organizowania, <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> właściwość Sprawdzanie poprawności komunikatu, wymuszenie i <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> właściwości do zwrócenia Wyjątki jako <xref:System.ServiceModel.FaultException> obiektów do usługi w celu debugowania.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Aby włączyć przepływ informacji o zarządzanych wyjątku przy użyciu CallbackDebugBehavior  
 Można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania przez ustawienie <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwości `true` pliku programowo lub z konfiguracji aplikacji.  
  
 Zwraca informacje o zarządzanym wyjątku do usług może stanowić zagrożenie bezpieczeństwa, ponieważ szczegóły wyjątku ujawnienie informacji o wewnętrznego klienta można użyć implementacji nieautoryzowany usług. Ponadto mimo że <xref:System.ServiceModel.Description.CallbackDebugBehavior> również można ustawić właściwości programowo, można go łatwo Pamiętaj, aby wyłączyć <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> podczas wdrażania.  
  
 Z powodu zagadnień związanych z zabezpieczeniami zdecydowanie zalecane jest:  
  
-   Użyj pliku konfiguracji aplikacji można ustawić wartości <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> właściwości `true`.  
  
-   Czynności wykonywane tylko w kontrolowany debugowania scenariuszy.  
  
 Poniższy przykład kodu pokazuje klienta pliku konfiguracji, który powoduje, że [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Aby uzyskać informacje o zarządzanym wyjątku w kliencie obiektu wywołania zwrotnego wiadomości SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Używając zachowania ClientViaBehavior  
 Można użyć <xref:System.ServiceModel.Description.ClientViaBehavior> zachowania, aby określić jednolitego identyfikatora zasobów, dla którego należy utworzyć kanał transportu. Używanie tego zachowania, gdy docelowego bezpośredniej sieci nie jest zamierzone procesora wiadomości. Dzięki temu konwersacji z wieloma przeskokami, gdy aplikacja wywołująca nie zna ultimate docelowego lub docelowego `Via` nagłówka nie jest adresem.  
  
## <a name="see-also"></a>Zobacz też  
 [Określanie zachowania środowiska uruchomieniowego usługi](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
