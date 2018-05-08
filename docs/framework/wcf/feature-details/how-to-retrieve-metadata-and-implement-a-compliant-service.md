---
title: 'Porady: Pobieranie metadanych i implementacji usługi zgodne'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 9ae888f5a9569ef51be52b91ea019fea897597b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Porady: Pobieranie metadanych i implementacji usługi zgodne
Ta sama osoba nie często, projektowania i implementacji usługi. W środowiskach, w którym współpracy aplikacje są ważne kontrakty można zaprojektowane lub opisanego w sieci Web Services Description Language (WSDL) oraz deweloper musi implementować to usługa, która spełnia podane kontraktu. Można także migracji istniejącej usługi do usługi Windows Communication Foundation (WCF), ale zachować format danych przesyłanych w sieci. Ponadto kontrakty dwukierunkowe wymaga wywołań zaimplementować kontrakt wywołania zwrotnego, jak również.  
  
 W takich sytuacjach należy użyć [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (lub równoważne narzędzie) do generowania interfejsu kontraktu usługi w języku zarządzanych, które można zaimplementować w celu spełnienia wymagań kontrakt. Zazwyczaj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jest używany do uzyskiwania kontraktu usługi, który jest używany z fabryki kanałów lub typ klienta WCF, a także z pliku konfiguracji klienta, który konfiguruje poprawne powiązanie i adres. Aby użyć pliku konfiguracji wygenerowanego, muszą go zmienić w pliku konfiguracji usługi. Należy również zmodyfikować kontraktu usługi.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Aby pobrać dane i implementacji usługi zgodne  
  
1.  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem plików metadanych lub punkt końcowy metadanych do wygenerowania pliku kodu.  
  
2.  Wyszukaj fragment danych wyjściowych pliku kodu zawierającego interfejsu odsetek (w przypadku istnieje więcej niż jednego) oznaczonej za pomocą <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atrybutu. Poniższy przykładowy kod przedstawia dwa interfejsy generowane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Pierwszy (`ISampleService`) jest interfejsu kontraktu usługi, który implementuje można utworzyć usługi zgodne. Druga (`ISampleServiceChannel`) to interfejs pomocnika do użycia klienta, rozszerzający zarówno interfejsu kontraktu usługi i <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> i jest przeznaczona do użytku w aplikacji klienckiej.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Jeśli WSDL nie określa akcji odpowiedzi dla wszystkich działań, może być kontrakty operacji wygenerowanego <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> właściwość symbol wieloznaczny (*). Usuń ustawienie właściwości. W przeciwnym razie podczas implementowania metadane kontraktu usługi metadanych nie można wyeksportować do tych operacji.  
  
4.  Zaimplementuj interfejs dla klasy i obsługi usługi. Na przykład zobacz [porady: Implementowanie kontraktu usługi](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), lub zobacz prostych implementacji poniżej w sekcji przykładu.  
  
5.  W konfiguracji klienta pliku [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) generuje, zmień [ \<klienta >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) Sekcja konfiguracyjna do [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji konfiguracji. (Na przykład plik konfiguracji aplikacji wygenerowanego klienta Zobacz następującą sekcję "Example").  
  
6.  W ramach [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) konfiguracji sekcji, Utwórz `name` atrybutu w [ \<usługi >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) sekcji konfiguracji dla usługi Implementacja.  
  
7.  Ustaw usługę `name` atrybutu nazwy konfiguracji dla implementacji usługi.  
  
8.  Dodaj elementy konfiguracji punktu końcowego używających kontraktu usługi zaimplementowana do sekcji konfiguracji usługi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje większość plik kod wygenerowany przez uruchomienie [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) przed pliki metadanych.  
  
 Poniższy kod przedstawia:  
  
-   Kontrakt usługi interfejsem, implementując jest zgodny z wymaganiami kontraktu (`ISampleService`).  
  
-   Interfejs pomocnika do użycia klienta, rozszerzający zarówno interfejsu kontraktu usługi i <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> i jest przeznaczona do użytku w aplikacji klienckiej (`ISampleServiceChannel`).  
  
-   Klasa pomocy, rozszerzający <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> i jest przeznaczona do użytku w aplikacji klienckiej (`SampleServiceClient`).  
  
-   Plik konfiguracji generowany przez usługę.  
  
-   Prosty `ISampleService` implementacji usługi.  
  
-   Konwersja pliku konfiguracji po stronie klienta do wersji po stronie serwera.  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
