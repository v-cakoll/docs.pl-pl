---
title: 'Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej'
ms.date: 03/30/2017
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
ms.openlocfilehash: 5b01ddfd95db2f7e88f9481265c348f4f16fbbee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579479"
---
# <a name="how-to-exchange-messages-within-a-reliable-session"></a>Instrukcje: Wymiana komunikatów w ramach sesji niezawodnej

W tym temacie opisano kroki wymagane do umożliwienia niezawodnej sesji przy użyciu jednego z powiązań dostarczonych przez system, które obsługują taką sesję, ale nie jest to domyślnie możliwe. Niezawodna sesja jest włączana za pomocą kodu lub deklaratywnie w pliku konfiguracji. Ta procedura korzysta z plików konfiguracji klienta i usługi w celu włączenia niezawodnej sesji i określenia, że komunikaty docierają do tej samej kolejności, w jakiej zostały wysłane.

Kluczową częścią tej procedury jest to, że element konfiguracji punktu końcowego zawiera `bindingConfiguration` atrybut odwołujący się do konfiguracji powiązania o nazwie `Binding1` . [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Element konfiguracji odwołuje się do tej nazwy, aby umożliwić niezawodne sesje przez ustawienie `enabled` atrybutu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731302(v=vs.100)) elementu na `true` . Należy określić uporządkowane gwarancje dostarczania dla niezawodnej sesji przez ustawienie `ordered` atrybutu na `true` .

Aby uzyskać kopię źródła tego przykładu, zobacz temat [Niezawodna sesja WS](../samples/ws-reliable-session.md).

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie usługi za pomocą WSHttpBinding do korzystania z niezawodnej sesji

1. Zdefiniuj kontrakt usługi dla typu usługi.

   [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]

1. Zaimplementuj kontrakt usługi w klasie usługi. Należy zauważyć, że adres lub informacje o powiązaniu nie są określone w implementacji usługi. Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]

1. Utwórz plik *Web. config* , aby skonfigurować punkt końcowy dla programu `CalculatorService` , który korzysta z <xref:System.ServiceModel.WSHttpBinding> włączonej niezawodnej sesji z włączoną obsługą i uporządkowane dostarczanie komunikatów.

   [!code-xml[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]

1. Utwórz plik *usługi SVC* , który zawiera wiersz:

   ```
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```

1. Umieść plik *Service. svc* w katalogu wirtualnym Internet Information Services (IIS).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurowanie klienta z WSHttpBinding do korzystania z niezawodnej sesji

1. Użyj [Narzędzia metadanych ServiceModel (*Svcutil. exe*)](../servicemodel-metadata-utility-tool-svcutil-exe.md) z wiersza polecenia, aby wygenerować kod na podstawie metadanych usługi:

   ```console
   Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
   ```

1. Wygenerowany klient zawiera `ICalculator` interfejs, który definiuje kontrakt usługi, który musi spełniać implementacja klienta.

   [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]

1. Wygenerowana aplikacja kliencka zawiera również implementację programu `ClientCalculator` . Należy zauważyć, że informacje o adresie i powiązaniu nie są określone w dowolnym miejscu w implementacji usługi. Nie trzeba pisać kodu w celu pobrania adresu lub informacji o powiązaniu z pliku konfiguracyjnego.

   [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]

1. *Svcutil. exe* generuje również konfigurację dla klienta, który używa <xref:System.ServiceModel.WSHttpBinding> klasy. Nazwij plik konfiguracji *App. config* podczas korzystania z programu Visual Studio.

   [!code-xml[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]

1. Utwórz wystąpienie elementu `ClientCalculator` w aplikacji i Wywołaj operacje usługi.

   [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]

1. Kompiluj i uruchom klienta.

## <a name="example"></a>Przykład

Niektóre powiązania dostarczone przez system domyślnie obsługują niezawodne sesje. Należą do nich następujące elementy:

- <xref:System.ServiceModel.WSDualHttpBinding>

- <xref:System.ServiceModel.NetNamedPipeBinding>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>

Aby zapoznać się z przykładem tworzenia niestandardowego powiązania, które obsługuje niezawodne sesje, zobacz [How to: Create an Custom niezawodnej sesji powiązania z protokołem HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).

## <a name="see-also"></a>Zobacz też

- [Niezawodne sesje](reliable-sessions.md)
