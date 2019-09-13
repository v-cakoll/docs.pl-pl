---
title: 'Samouczek: Tworzenie klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: ddb5167c7f71a263377fb465ec44ee21057fbf4a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928902"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Samouczek: Tworzenie klienta Windows Communication Foundation

W tym samouczku opisano czwarte pięć zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, [zobacz Samouczek: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation.

Następnym zadaniem do tworzenia aplikacji WCF jest utworzenie klienta przez pobranie metadanych z usługi WCF. Używasz programu Visual Studio, aby dodać odwołanie do usługi, które pobiera metadane z punktu końcowego MEX usługi. Program Visual Studio generuje następnie zarządzany plik kodu źródłowego dla serwera proxy klienta w wybranym języku. Tworzy również plik konfiguracji klienta (*App. config*). Ten plik umożliwia aplikacji klienckiej łączenie się z usługą w punkcie końcowym. 

> [!NOTE]
> Jeśli wywołasz usługę WCF z projektu biblioteki klas w programie Visual Studio, użyj funkcji **Dodaj odwołanie do usługi** , aby automatycznie wygenerować serwer proxy i skojarzony plik konfiguracji. Jednak ponieważ projekty biblioteki klas nie korzystają z tego pliku konfiguracji, należy dodać ustawienia w wygenerowanym pliku konfiguracji do pliku *App. config* dla pliku wykonywalnego, który wywołuje bibliotekę klas.

> [!NOTE]
> Alternatywnie, aby wygenerować klasę i plik konfiguracji serwera proxy, użyj [Narzędzia metadanych ServiceModel](#servicemodel-metadata-utility-tool) zamiast programu Visual Studio.

Aplikacja kliencka używa wygenerowanej klasy proxy do komunikacji z usługą. Ta procedura została opisana w [samouczku: Użyj klienta](how-to-use-a-wcf-client.md)programu.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta WCF.
> - Dodaj odwołanie do usługi do usługi WCF w celu wygenerowania klasy i plików konfiguracji serwera proxy.

## <a name="create-a-windows-communication-foundation-client"></a>Tworzenie klienta Windows Communication Foundation

1. Utwórz projekt aplikacji konsolowej w programie Visual Studio: 

    1. Z menu **plik** wybierz pozycję **Otwórz** > **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted. sln*). Wybierz pozycję **Otwórz**.

    2. Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.

    3. W oknie **Eksplorator rozwiązań** wybierz rozwiązanie **GettingStarted** (górny węzeł), a następnie wybierz pozycję **Dodaj** > **Nowy projekt** z menu skrótów. 
    
    4. W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię **pulpit systemu Windows** w obszarze **Wizualizacja C#**  lub **Visual Basic**. 

    5. Wybierz szablon **aplikacja konsoli (.NET Framework)** , a następnie wprowadź *GettingStartedClient* jako **nazwę**. Kliknij przycisk **OK**.

2. Dodaj odwołanie do <xref:System.ServiceModel> zestawu w projekcie **GettingStartedClient** : 

    1. W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedClient** , a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów. 

    2. W oknie **Dodaj odwołanie** w obszarze **zestawy** po lewej stronie okna wybierz pozycję **Struktura**.
    
    3. Znajdź i wybierz **System. ServiceModel**, a następnie wybierz przycisk **OK**. 

    4. Zapisz rozwiązanie, wybierając kolejno pozycje **plik** > **Zapisz wszystko**.

3. Dodaj odwołanie do usługi kalkulatora:

   1. W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedClient** , a następnie wybierz pozycję **Dodaj odwołanie do usługi** z menu skrótów.

   2. W oknie **Dodaj odwołanie do usługi** wybierz pozycję **odkryj**.

      Zostanie uruchomiona usługa CalculatorService, a program Visual Studio wyświetli go w polu **usługi** .

   3. Wybierz pozycję **CalculatorService** , aby ją rozwinąć i wyświetlić kontrakty usługi zaimplementowane przez usługę. Pozostaw domyślną **przestrzeń nazw** i wybierz **przycisk OK**.

      Program Visual Studio dodaje nowy element w folderze **usługi połączone** w projekcie **GettingStartedClient** . 

### <a name="servicemodel-metadata-utility-tool"></a>Narzędzie do przesyłania metadanych ServiceModel

W poniższych przykładach pokazano, jak opcjonalnie użyć [Narzędzia metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) do wygenerowania pliku klasy proxy. To narzędzie generuje plik klasy serwera proxy i plik *App. config* . W poniższych przykładach pokazano, jak wygenerować serwer proxy C# w i Visual Basic odpowiednio:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Plik konfiguracji klienta

Po utworzeniu klienta program Visual Studio tworzy plik konfiguracji **App. config** w projekcie **GettingStartedClient** , który powinien być podobny do następującego przykładu:

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
            <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/GettingStarted/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <dns value="localhost" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

W sekcji [ \<](../configure-apps/file-schema/wcf/endpoint-element.md) system. [ServiceModel > Zwróć uwagę na element Endpoint >. \<](../configure-apps/file-schema/wcf/system-servicemodel.md) Element **Endpoint&gt;definiuje punkt końcowy, którego klient używa do uzyskiwania dostępu do usługi w następujący sposób: &lt;**

- Adres: `http://localhost:8000/GettingStarted/CalculatorService`. Adres punktu końcowego.
- Kontrakt usługi: `ServiceReference1.ICalculator`. Kontrakt usługi obsługuje komunikację między klientem programu WCF a usługą. Program Visual Studio wygenerował ten kontrakt, gdy użyto funkcji **Dodaj odwołanie do usługi** . Zasadniczo jest to kopia kontraktu, która została zdefiniowana w projekcie GettingStartedLib. 
- Powiązanie: <xref:System.ServiceModel.WSHttpBinding>. Powiązanie określa protokół HTTP jako Transport, zabezpieczenia interoperacyjności i inne szczegóły konfiguracji.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta WCF.
> - Dodaj odwołanie do usługi do usługi WCF w celu wygenerowania klasy serwera proxy i plików konfiguracji dla aplikacji klienckiej.

Przejdź do następnego samouczka, aby dowiedzieć się, jak korzystać z wygenerowanego klienta.

> [!div class="nextstepaction"]
> [Samouczek: Korzystanie z klienta WCF](how-to-use-a-wcf-client.md)
