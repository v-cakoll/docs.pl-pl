---
title: 'Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 58a392fc6295e82f41e08c80a3343b4059afad7e
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141678"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej

W tym temacie opisano kroki wymagane do umożliwienia niezawodnej sesji przy użyciu jednego z powiązań dostarczonych przez system, które obsługują taką sesję, ale nie jest to domyślnie możliwe. Niezawodna sesja jest włączana za pomocą kodu lub deklaratywnie w pliku konfiguracji. Ta procedura korzysta z plików konfiguracji klienta i usługi w celu włączenia niezawodnej sesji i określenia, że komunikaty docierają do tej samej kolejności, w jakiej zostały wysłane.

Kluczową częścią tej procedury jest to, że element konfiguracji punktu końcowego zawiera atrybut `bindingConfiguration`, który odwołuje się do konfiguracji powiązania o nazwie `Binding1`. Element konfiguracji [ **> powiązania\<** ](../../configure-apps/file-schema/wcf/bindings.md) odwołuje się do tej nazwy, aby umożliwić niezawodne sesje przez ustawienie atrybutu `enabled` elementu [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) w `true`. Aby określić uporządkowane gwarancje dostarczania dla niezawodnej sesji, należy ustawić atrybut `ordered` na `true`.

Aby uzyskać kopię źródła tego przykładu, zobacz temat [Niezawodna sesja WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie usługi za pomocą WSHttpBinding do korzystania z niezawodnej sesji

1. Zdefiniuj kontrakt usługi dla typu usługi.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Zaimplementuj kontrakt usługi w klasie usługi. Należy zauważyć, że adres lub informacje o powiązaniu nie są określone w implementacji usługi. Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Utwórz plik *Web. config* , aby skonfigurować punkt końcowy dla `CalculatorService`, który używa <xref:System.ServiceModel.WSHttpBinding> z włączonymi niezawodnymi sesjami i zamówioną dostawą komunikatów.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Utwórz plik *usługi SVC* , który zawiera wiersz:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Umieść plik *Service. svc* w katalogu wirtualnym Internet Information Services (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta z WSHttpBinding do korzystania z niezawodnej sesji

1. Użyj [Narzędzia metadanych ServiceModel (*Svcutil. exe*)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Wygenerowany klient zawiera interfejs `ICalculator`, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Wygenerowana aplikacja kliencka zawiera również implementację `ClientCalculator`. Należy zauważyć, że informacje o adresie i powiązaniu nie są określone w dowolnym miejscu w implementacji usługi. Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil. exe* generuje również konfigurację dla klienta, który używa klasy <xref:System.ServiceModel.WSHttpBinding>. Nazwij plik konfiguracji *App. config* podczas korzystania z programu Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Utwórz wystąpienie `ClientCalculator` w aplikacji i Wywołaj operacje usługi.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Kompiluj i uruchom klienta.

## <a name="example"></a>Przykład

Niektóre powiązania dostarczone przez system domyślnie obsługują niezawodne sesje. Należą do nich następujące elementy:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Aby zapoznać się z przykładem tworzenia niestandardowego powiązania, które obsługuje niezawodne sesje, zobacz [How to: Create an Custom niezawodnej sesji powiązania z protokołem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Zobacz także

- [Niezawodne sesje](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
