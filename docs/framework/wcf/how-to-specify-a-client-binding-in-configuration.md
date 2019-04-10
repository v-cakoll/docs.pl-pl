---
title: 'Instrukcje: Określanie powiązań klienta w konfiguracji'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 633bb0feeb0f9354bd6ff8ee6637f123d3e3cbf4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295136"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Instrukcje: Określanie powiązań klienta w konfiguracji
W tym przykładzie utworzono aplikację konsolową w języku klienta do używania usługi Kalkulator i deklaratywne określono powiązania dla tego klienta w konfiguracji. Klient uzyskuje dostęp do `CalculatorService`, który implementuje `ICalculator` interfejsu i usługi oraz klienta, użyj <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Procedury opisanej przyjęto założenie, że jest uruchomiona usługa kalkulatora. Aby uzyskać informacje dotyczące sposobu tworzenia usługi, zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Korzysta również [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) , Windows Communication Foundation (WCF) zapewnia automatyczne generowanie składniki klienta. Narzędzie generuje kod klienta i konfiguracji do uzyskiwania dostępu do usługi.  
  
 Klient została stworzona w dwóch częściach. Generuje svcutil.exe `ClientCalculator` implementującej `ICalculator` interfejsu. Ta aplikacja kliencka jest następnie tworzony przez utworzenie wystąpienia `ClientCalculator`.  
  
 Jest zwykle najlepszym rozwiązaniem jest, aby określić powiązanie i informacje o adresie deklaratywnie w konfiguracji, a nie obowiązkowo w kodzie. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana. Ogólnie rzecz biorąc zachowanie wiązania i adresowanie z kodu pozwala na zmianę bez konieczności ponownego kompilowania lub ponownego wdrażania aplikacji.  
  
 Wykonaj wszystkie poniższe czynności konfiguracyjne przy użyciu [narzędzie edytora konfiguracji (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Źródło kopię w tym przykładzie można zobaczyć [element basicbinding elementem](../../../docs/framework/wcf/samples/basicbinding.md) próbki.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Określanie powiązania w konfiguracji klienta  
  
1. Umożliwia Svcutil.exe w wierszu polecenia generowanie kodu na podstawie metadanych usługi.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. Klient, który jest generowany zawiera `ICalculator` Interfejs definiujący kontrakt usługi, które muszą spełniać implementacji klienta.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Wygenerowanego klienta zawiera również implementację `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe generuje również konfigurację dla klienta, który używa <xref:System.ServiceModel.BasicHttpBinding> klasy. Korzystając z programu Visual Studio, nazwij ten plik App.config. Należy pamiętać, że adres i informacje o powiązaniu nie są określone dowolne miejsce wewnątrz implementacji usługi. Ponadto kod nie ma do zapisania, aby pobrać te informacje z pliku konfiguracji.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. Utwórz wystąpienie obiektu `ClientCalculator` w aplikacji, a następnie wywoływanie operacji usługi.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Kompilowanie i uruchamianie klienta.  
  
## <a name="see-also"></a>Zobacz także

- [Konfigurowanie usług i klientów za pomocą wiązań](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
