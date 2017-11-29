---
title: "Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6207b526aa98fd01892b493ab5b6ad6a58abc3c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej

W tym temacie opisano kroki wymagane w celu umożliwienia niezawodnej sesji przy użyciu jednej powiązań dostarczane przez system, które obsługują sesji programu, ale nie domyślnie. Włącz niezawodnej sesji imperatively przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura wykorzystuje pliki konfiguracji klienta i usługi, aby włączyć niezawodnej sesji i określić, że komunikaty dostarczone w tej samej kolejności, w jakiej zostały wysłane.

Część klucza tej procedury jest, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `Binding1`. [  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby włączyć niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) elementu `true`. Określ gwarancje uporządkowanego dostarczenia niezawodnej sesji przez ustawienie `ordered` atrybutu `true`.

Dla źródła kopię w tym przykładzie [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Skonfiguruj usługę z WSHttpBinding do użycia niezawodnej sesji

1. Definiowanie kontraktu usługi dla typu usługi.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementowanie kontraktu usługi w klasie usługi. Należy pamiętać, że informacje powiązania lub adres nie jest określona wewnątrz implementacji usługi. Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązanie informacji o informacje z pliku konfiguracji.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Utwórz *Web.config* pliku do konfigurowania punktu końcowego dla `CalculatorService` używającą <xref:System.ServiceModel.WSHttpBinding> z niezawodnej sesji włączona i uporządkowanego dostarczenia komunikatów wymagane.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Utwórz *Service.svc* pliku, który zawiera wiersz:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Miejsce *Service.svc* pliku w katalogu wirtualnym programu Internet Information Services (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta z WSHttpBinding do użycia niezawodnej sesji

1. Użyj [narzędzie do obsługi metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Zawiera wygenerowanego klienta `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacja klienta.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Aplikacja wygenerowanego klienta zawiera również implementacja `ClientCalculator`. Należy pamiętać, że informacje adres i powiązanie nie jest określony dowolnym wewnątrz implementacji usługi. Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązanie informacji o informacje z pliku konfiguracji.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* również generuje konfigurację dla klienta, który używa <xref:System.ServiceModel.WSHttpBinding> klasy. Nazwa pliku konfiguracji *App.config* przy użyciu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Utwórz wystąpienie `ClientCalculator` w aplikacji i wywoływanie operacji usługi.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Kompilowanie i uruchamianie klienta.

## <a name="example"></a>Przykład

Domyślnie kilka powiązania dostarczane przez system obsługi niezawodnej sesji. Należą do nich następujące elementy:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Na przykład sposobu tworzenia niestandardowego powiązania, który niezawodnej sesji obsługuje zobacz [porady: Tworzenie niestandardowego wiązania niezawodnej sesji z protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Zobacz także

[Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
