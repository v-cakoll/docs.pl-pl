---
title: 'Porady: Pobieranie metadanych i implementowanie zgodnej usługi'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: dc7f5d97a5201698e8dc99e4523e3ab2925f6883
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185225"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Porady: Pobieranie metadanych i implementowanie zgodnej usługi
Tę samą osobę nie często, projektowania i implementacji usługi. W środowiskach, w których ważne aplikacje współpracy kontrakty mogą być zaprojektowana lub opisanego w sieci Web Services Description Language (WSDL) i deweloper musi implementować to usługa, która spełnia podane kontraktu. Można również migrować istniejącą usługę do programu Windows Communication Foundation (WCF), ale zachować format o komunikacji sieciowej. Ponadto kontrakty dwukierunkowe wymaga wywołań zaimplementować kontrakt wywołania zwrotnego, który jest również.  
  
 W takich przypadkach należy użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (lub równoważne narzędzie) do generowania interfejsu kontraktu usługi w języka zarządzanego, który można zaimplementować w celu spełnienia wymagań kontrakt. Zazwyczaj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) służy do uzyskania kontraktu usługi, który jest używany, za pomocą fabryki kanałów lub typ klienta WCF, a także za pomocą pliku konfiguracji klienta, który konfiguruje poprawne powiązanie i adres. Aby użyć pliku wygenerowaną konfigurację, możesz zmienić ją w pliku konfiguracji usługi. Również może być konieczne zmodyfikowanie kontraktu usługi.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Aby pobrać dane i implementowanie zgodnej usługi  
  
1.  Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem plików metadanych lub punkt końcowy metadanych, aby wygenerować plik kodu.  
  
2.  Wyszukaj części danych wyjściowych kodu pliku który zawiera interfejs odsetek (w przypadku występuje więcej niż jednego), która jest oznaczona za pomocą <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atrybutu. Poniższy przykład kodu pokazuje dwa interfejsy, które są generowane przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Pierwszy (`ISampleService`) jest interfejsu kontraktu usługi, który implementuje można utworzyć usługi zgodne. Drugi (`ISampleServiceChannel`) jest interfejsem pomocnika do użytku klienta, która rozszerza zarówno interfejs kontraktu usługi i <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> i jest dostępny do użycia w aplikacji klienckiej.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  W przypadku WSDL nie określa akcji odpowiedzi dla wszystkich operacji, może być kontrakty operacji wygenerowanego <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> właściwość ustawioną na symbol wieloznaczny (*). Usuń ustawienie tej właściwości. W przeciwnym razie podczas implementowania metadanych kontraktu usługi nie można wyeksportować metadane dla tych operacji.  
  
4.  Implementowanie interfejsu w klasie i obsługi usługi. Aby uzyskać przykład, zobacz [porady: Implementowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), lub zobacz proste wdrażanie poniżej w sekcji z przykładowym.  
  
5.  W konfiguracji klienta pliku, który [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje, zmień [ \<klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) sekcji konfiguracji, aby [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji konfiguracji. (Na przykład pliku konfiguracji aplikacji wygenerowanego klienta, zobacz w poniższej sekcji "Przykładowy").  
  
6.  W ramach [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfiguracji sekcji, Utwórz `name` atrybutu w [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji konfiguracji dla usługi Implementacja.  
  
7.  Ustaw usługę `name` atrybutu nazwy konfiguracji dla implementacji usługi.  
  
8.  Dodawanie elementów konfiguracji punktu końcowego, które umożliwiają kontraktu usługi zaimplementowano sekcji konfiguracji usługi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje większość wygenerowane przez uruchomienie pliku z kodem [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem plików metadanych.  
  
 Poniższy kod pokazuje:  
  
-   Kontrakt usługi interfejs, który, po wdrożeniu, spełnia wymagania umowy (`ISampleService`).  
  
-   Interfejs pomocnika do użytku klienta, która rozszerza zarówno interfejs kontraktu usługi i <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> i jest dostępny do użycia w aplikacji klienckiej (`ISampleServiceChannel`).  
  
-   Klasa pomocnika, która rozszerza <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> i jest dostępny do użycia w aplikacji klienckiej (`SampleServiceClient`).  
  
-   Plik konfiguracji, generowane przez usługę.  
  
-   Prosty `ISampleService` implementacji usługi.  
  
-   Konwersja pliku konfiguracji po stronie klienta do wersji po stronie usługi.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
