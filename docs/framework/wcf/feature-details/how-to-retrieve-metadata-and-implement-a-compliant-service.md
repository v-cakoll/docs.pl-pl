---
title: 'Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 6bd67ec8dcc0e73d097796b44974dce00b9a4eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601221"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi
Często ta sama osoba nie zaprojektuje i nie implementuje usług. W środowiskach, w których aplikacje współdziałające są ważne, kontrakty mogą być zaprojektowane lub opisane w Web Services Description Language (WSDL), a Deweloper musi wdrożyć usługę zgodną z podaną umową. Możesz także chcieć przeprowadzić migrację istniejącej usługi do Windows Communication Foundation (WCF), ale zachować format sieci szkieletowej. Ponadto kontrakty dupleksowe wymagają od wywołujących do zaimplementowania kontraktu wywołania zwrotnego.  
  
 W takich przypadkach należy użyć narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) (lub równoważnego narzędzia) do wygenerowania interfejsu kontraktu usługi w zarządzanym języku, który można wdrożyć w celu spełnienia wymagań kontraktu. Zazwyczaj narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) służy do uzyskiwania kontraktu usługi, który jest używany z fabryką kanałów lub typem klienta WCF oraz z plikiem konfiguracji klienta, który konfiguruje poprawne powiązanie i adres. Aby użyć wygenerowanego pliku konfiguracji, należy go zmienić w pliku konfiguracji usługi. Może być również konieczne zmodyfikowanie kontraktu usługi.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Aby pobrać dane i zaimplementować zgodną usługę  
  
1. Użyj [Narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) względem plików metadanych lub punktu końcowego metadanych, aby wygenerować plik kodu.  
  
2. Wyszukaj część pliku kodu wyjściowego, który zawiera interfejs zainteresowań (w przypadku, gdy istnieje więcej niż jeden), który jest oznaczony <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atrybutem. Poniższy przykład kodu przedstawia dwa interfejsy wygenerowane przez narzędzie do zaimplementowania [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Pierwszy ( `ISampleService` ) jest interfejsem kontraktu usługi, który jest implementowany w celu utworzenia zgodnej usługi. Drugi ( `ISampleServiceChannel` ) to interfejs pomocnika używany przez klienta, który rozszerza zarówno interfejs kontraktu usługi, jak <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> i jest używany w aplikacji klienckiej.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. Jeśli w języku WSDL nie określono akcji odpowiedzi dla wszystkich operacji, wygenerowane kontrakty operacji mogą mieć <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> ustawioną właściwość na symbol wieloznaczny (*). Usuń to ustawienie właściwości. W przeciwnym razie podczas implementowania metadanych kontraktu usługi nie można eksportować metadanych dla tych operacji.  
  
4. Implementowanie interfejsu w klasie i Hostowanie usługi. Aby zapoznać się z przykładem, zobacz [jak: Implementowanie kontraktu usługi](../how-to-implement-a-wcf-contract.md)lub zapoznaj się z prostą implementacją poniżej w sekcji przykład.  
  
5. W pliku konfiguracyjnym klienta, który generuje [Narzędzie do metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , Zmień [\<client>](../../configure-apps/file-schema/wcf/client.md) sekcję konfiguracyjną w sekcji [\<services>](../../configure-apps/file-schema/wcf/services.md) konfiguracji. (Przykład wygenerowanego pliku konfiguracyjnego aplikacji klienckiej znajduje się w sekcji "przykład").  
  
6. W [\<services>](../../configure-apps/file-schema/wcf/services.md) sekcji Konfiguracja Utwórz `name` atrybut w [\<services>](../../configure-apps/file-schema/wcf/services.md) sekcji konfiguracji dla implementacji usługi.  
  
7. Ustaw atrybut usługi `name` na nazwę konfiguracji dla implementacji usługi.  
  
8. Dodaj elementy konfiguracji punktu końcowego, które używają wdrożonego kontraktu usługi do sekcji Konfiguracja usługi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje większość pliku kodu wygenerowanego przez uruchomienie [Narzędzia do przesyłania metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) względem plików metadanych.  
  
 Poniższy kod ilustruje:  
  
- Interfejs kontraktu usługi, który w przypadku implementacji jest zgodny z wymaganiami kontraktu ( `ISampleService` ).  
  
- Interfejs pomocnika używany przez klienta, który rozszerza zarówno interfejs kontraktu usługi, jak <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> i jest używany w aplikacji klienckiej ( `ISampleServiceChannel` ).  
  
- Klasa pomocnika, która rozszerza <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> i jest używana w aplikacji klienckiej ( `SampleServiceClient` ).  
  
- Plik konfiguracji wygenerowany na podstawie usługi.  
  
- Prosta `ISampleService` Implementacja usługi.  
  
- Konwersja pliku konfiguracji po stronie klienta do wersji po stronie usługi.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Zobacz też

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
