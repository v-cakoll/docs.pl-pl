---
title: 'Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 145224655d1ec76c9deb5afc3c1a8ec9a1975f4f
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56260689"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej

W tym temacie opisano kroki wymagane w celu umożliwienia niezawodnej sesji przy użyciu jednej z powiązań dostarczanych przez system, które obsługują sesji programu, ale nie domyślnie. Włącz niezawodnej sesji obowiązkowo przy użyciu kodu lub deklaratywnie w pliku konfiguracji. Ta procedura wykorzystuje pliki konfiguracji klienta i usługi, aby umożliwić niezawodnej sesji i określać, że komunikaty zostaną dostarczone w tej samej kolejności, w jakiej zostały wysłane.

Kluczowa część tej procedury jest, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut, który odwołuje się do konfiguracji powiązania o nazwie `Binding1`. [  **\<Powiązania >** ](../../../../docs/framework/misc/binding.md) element konfiguracji odwołuje się do tej nazwy, aby umożliwić niezawodnej sesji przez ustawienie `enabled` atrybutu [  **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu `true`. Określ gwarancje dostarczenia uporządkowane w niezawodnej sesji przez ustawienie `ordered` atrybutu `true`.

Źródło kopię w tym przykładzie można zobaczyć [sesja niezawodna WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie usługi przy użyciu WSHttpBinding używać niezawodnej sesji

1. Definiowanie kontraktu usługi dla typu usługi.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Implementowanie kontraktu usługi, w klasie usługi. Należy pamiętać, że informacji adres lub powiązanie nie jest określona wewnątrz implementacji usługi. Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązania informacji z pliku konfiguracji.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Tworzenie *Web.config* pliku, aby skonfigurować punkt końcowy dla `CalculatorService` , który używa <xref:System.ServiceModel.WSHttpBinding> za pomocą niezawodnej sesji włączone i uporządkowane dostarczania wiadomości wymagane.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Tworzenie *Service.svc* pliku zawierające następujący wiersz:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1.  Miejsce *Service.svc* pliku w katalogu wirtualnego Internet Information Services (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta za pomocą WSHttpBinding używać niezawodnej sesji

1. Użyj [narzędzie do metadanych elementu ServiceModel (*Svcutil.exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z poziomu wiersza polecenia, aby wygenerować kod z metadanych usługi:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Zawiera wygenerowanego klienta `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Aplikacja wygenerowanego klienta zawiera również implementację `ClientCalculator`. Należy pamiętać, że informacje dotyczące adresów i powiązanie nie jest określona w dowolne miejsce wewnątrz implementacji usługi. Nie są wymagane, aby napisać kod, aby pobrać adres lub powiązania informacji z pliku konfiguracji.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil.exe* również generuje konfigurację dla klienta, który używa <xref:System.ServiceModel.WSHttpBinding> klasy. Nadaj plikowi konfiguracji nazwę *App.config* przy użyciu programu Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Utwórz wystąpienie obiektu `ClientCalculator` w aplikacji i wywoływanie operacji usługi.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Kompilowanie i uruchamianie klienta.

## <a name="example"></a>Przykład

Domyślnie kilka powiązania dostarczane przez system obsługuje sesji uwierzytelnianych. Należą do nich następujące elementy:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Na przykład sposobu tworzenia niestandardowego powiązania, które obsługuje niezawodne sesje zobacz [jak: Tworzenie niestandardowych wiązań niezawodnej sesji za pomocą protokołu HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Zobacz także

- [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
