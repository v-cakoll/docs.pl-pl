---
title: 'Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 0a13d504b1c7c38ec13fee58c36913a75119271b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184858"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Instrukcje: pobieranie metadanych i implementowanie zgodnej usługi
Często ta sama osoba nie projektuje i nie wdraża usług. W środowiskach, w których aplikacje współdziałające są ważne, kontrakty mogą być projektowane lub opisane w języku WSDL opisu usług sieci Web, a deweloper musi zaimplementować usługę, która jest zgodna z dostarczoną umową. Można również przeprowadzić migrację istniejącej usługi do programu Windows Communication Foundation (WCF), ale zachować format sieci. Ponadto umowy dupleksowe wymagają od osób wywołujących zaimplementowanie umowy wywołania zwrotnego.  
  
 W takich przypadkach należy użyć [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (lub równoważne narzędzie) do generowania interfejsu umowy serwisowej w języku zarządzanym, który można zaimplementować w celu spełnienia wymagań umowy. Zazwyczaj [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jest używany do uzyskania umowy serwisowej, która jest używana z fabryki kanału lub typu klienta WCF, jak również z plikiem konfiguracji klienta, który konfiguruje poprawne powiązanie i adres. Aby użyć wygenerowanego pliku konfiguracyjnego, należy go zmienić w plik konfiguracyjny usługi. Może być również konieczne zmodyfikowanie umowy serwisowej.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Aby pobrać dane i zaimplementować zgodną usługę  
  
1. Użyj [narzędzia narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) przeciwko plikom metadanych lub punktowi końcowemu metadanych, aby wygenerować plik kodu.  
  
2. Wyszukaj część pliku kodu wyjściowego, która zawiera interfejs zainteresowania (w przypadku, <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> gdy istnieje więcej niż jeden), który jest oznaczony atrybutem. Poniższy przykład kodu przedstawia dwa interfejsy generowane przez [narzędzie narzędzia Metadane ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Pierwszy (`ISampleService`) to interfejs umowy serwisowej, który można zaimplementować w celu utworzenia zgodnej usługi. Drugi (`ISampleServiceChannel`) jest interfejs pomocnika do użytku klienta, który <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> rozszerza zarówno interfejs umowy serwisowej i jest do użytku w aplikacji klienckiej.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. Jeśli WSDL nie określa akcji odpowiedzi dla wszystkich operacji, wygenerowane <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> kontrakty operacji może mieć właściwość ustawioną na znak symbolu wieloznacznego (*). Usuń to ustawienie właściwości. W przeciwnym razie podczas implementowania metadanych umowy serwisowej metadane nie mogą być eksportowane dla tych operacji.  
  
4. Zaimplementuj interfejs w klasie i hostuj usługę. Na przykład zobacz [Jak: Implementowanie umowy serwisowej](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)lub zobacz prostą implementację poniżej w sekcji Przykład.  
  
5. W pliku konfiguracji klienta, który generuje [narzędzie servicemodel metadata Utility Tool (Svcutil.exe),](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zmień sekcję konfiguracji [ \<>klienta](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) na [ \<sekcję konfiguracji usługi>.](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) (Na przykład wygenerowanego pliku konfiguracji aplikacji klienckiej zobacz następującą sekcję "Przykład").  
  
6. W sekcji [ \<konfiguracja usług>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) utwórz `name` atrybut w sekcji [ \<konfiguracji usług>](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) dla implementacji usługi.  
  
7. Ustaw atrybut `name` usługi na nazwę konfiguracji implementacji usługi.  
  
8. Dodaj elementy konfiguracji punktu końcowego, które używają zaimplementowanego kontraktu serwisowego do sekcji konfiguracji usługi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje większość pliku kodu wygenerowanego przez uruchomienie [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) przeciwko plikom metadanych.  
  
 Następujący kod pokazuje:  
  
- Interfejs umowy serwisowej, który po wdrożeniu spełnia`ISampleService`wymagania umowy ( ).  
  
- Interfejs pomocnika do użytku klienta, który rozszerza zarówno <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interfejs umowy serwisowej,`ISampleServiceChannel`jak i jest używany w aplikacji klienckiej ( ).  
  
- Klasa pomocnika, która <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> rozszerza się i jest do`SampleServiceClient`użytku w aplikacji klienckiej ( ).  
  
- Plik konfiguracyjny wygenerowany z usługi.  
  
- Prosta `ISampleService` implementacja usługi.  
  
- Konwersja pliku konfiguracyjnego po stronie klienta do wersji po stronie usługi.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Zobacz też

- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
