---
title: 'Samouczek: Tworzenie klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 0f7f622221e6612ecdb0ea04084d81e923218a5c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634066"
---
# <a name="tutorial-create-a-windows-communication-foundation-client"></a>Samouczek: Tworzenie klienta Windows Communication Foundation

W tym samouczku opisano czwarty pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Następne zadanie do tworzenia aplikacji WCF jest można utworzyć klienta przez pobierania metadanych z usługi WCF. Dodaj odwołanie do usługi, która pobiera metadane z punktu końcowego MEX usługi przy użyciu programu Visual Studio. Program Visual Studio następnie generuje plik kodu źródłowego zarządzanych dla danego języka, który został wybrany serwer proxy klienta. Tworzy również plik konfiguracji klienta (*App.config*). Plik ten umożliwia aplikacji klienckiej nawiązać połączenie z usługą w punkcie końcowym. 

> [!NOTE]
> Jeśli usługa WCF jest wywoływana z projekt biblioteki klas w programie Visual Studio, użyj **Dodaj odwołanie do usługi** funkcji w celu automatycznego generowania serwera proxy i skojarzony plik konfiguracji. Jednak ponieważ projekty bibliotek klas nie należy używać tego pliku konfiguracji, należy dodać ustawienia w pliku wygenerowaną konfigurację, aby *App.config* pliku dla pliku wykonywalnego, który wywołuje bibliotekę klas.

> [!NOTE]
> Alternatywnie użyj [ServiceModel metadanych narzędzie](#servicemodel-metadata-utility-tool) zamiast programu Visual Studio, aby wygenerować plik klasy i konfiguracji serwera proxy.

Aplikacja kliencka używa klasy wygenerowany serwer proxy do komunikacji z usługą. Ta procedura jest opisana w [samouczka: Za pomocą klienta](how-to-use-a-wcf-client.md).

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta platformy WCF.
> - Dodaj odwołanie do usługi WCF do generowania plików klasy i konfiguracji serwera proxy usługi.


## <a name="create-a-windows-communication-foundation-client"></a>Tworzenie klienta Windows Communication Foundation

1. Utwórz projekt aplikacji konsoli w programie Visual Studio: 

    1. Z **pliku** menu, wybierz opcję **Otwórz** > **projekt/rozwiązanie** i przejdź do **GettingStarted** rozwiązania możesz wcześniej utworzony (*GettingStarted.sln*). Wybierz pozycję **Otwórz**.

    2. Z **widoku** menu, wybierz opcję **Eksploratora rozwiązań**.

    3. W **Eksploratora rozwiązań** wybierz **GettingStarted** rozwiązania (najwyższy węzeł), a następnie wybierz **Dodaj** > **nowy projekt** z menu skrótów. 
    
    4. W **Dodaj nowy projekt** oknie po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#**  lub **języka Visual Basic**. 

    5. Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie wprowadź *GettingStartedClient* dla **nazwa**. Kliknij przycisk **OK**.

2. Dodaj odwołanie w **GettingStartedClient** projekt <xref:System.ServiceModel> zestawu: 

    1.  W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedClient** projektu, a następnie wybierz **Dodaj odwołanie** z menu skrótów. 

    2. W **Dodaj odwołanie** okna, w obszarze **zestawy** w lewej części okna wybierz **Framework**.
    
    3. Znajdź i zaznacz **System.ServiceModel**, a następnie wybierz **OK**. 

    4. Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.

3. Dodaj odwołanie do usługi z usługą Kalkulatora:

   1. W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedClient** projektu, a następnie wybierz **Dodaj odwołanie do usługi**  z menu skrótów.

   2. W **Dodaj odwołanie do usługi** wybierz **odnajdź**.

      CalculatorService usługa zostanie uruchomiona i programu Visual Studio wyświetla go w **usług** pole.

   3. Wybierz **CalculatorService** aby go rozwinąć i wyświetlić kontraktów usług implementowane przez usługę. Pozostaw wartość domyślną **Namespace** i wybierz polecenie **OK**.

      Program Visual Studio dodaje nowy element w obszarze **podłączone usługi** folderu w **GettingStartedClient** projektu. 


### <a name="servicemodel-metadata-utility-tool"></a>Narzędzie narzędzie metadanych elementu ServiceModel

W poniższych przykładach pokazano sposób użycia opcjonalnie [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) można wygenerować pliku klasy serwera proxy. To narzędzie generuje plik klasy serwera proxy i *App.config* pliku. W poniższych przykładach pokazano sposób generowania serwera proxy w C# i Visual Basic, odpowiednio:

```shell
svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

```shell
svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStarted/CalculatorService
```

### <a name="client-configuration-file"></a>Plik konfiguracji klienta

Po utworzeniu klienta programu Visual Studio tworzy **App.config** plik konfiguracji w **GettingStartedClient** projektu, który powinien być podobny do poniższego przykładu:

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

W obszarze [ \<system.serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) sekcji, zwróć uwagę, [ \<punktu końcowego >](../configure-apps/file-schema/wcf/endpoint-element.md) elementu. **&lt;Punktu końcowego&gt;** element definiuje punkt końcowy, który klient używa w celu uzyskania dostępu do usługi w następujący sposób:
- Adres: `http://localhost:8000/GettingStarted/CalculatorService`. Adres punktu końcowego.
- Kontrakt usługi: `ServiceReference1.ICalculator`. Kontrakt usługi obsługuje komunikację między klienta platformy WCF a usługą. Program Visual Studio generowany ten kontrakt użycia jej **Dodaj odwołanie do usługi** funkcji. Jest zasadniczo kopią kontraktu, który zostały zdefiniowane w projekcie GettingStartedLib. 
- Powiązanie: <xref:System.ServiceModel.WSHttpBinding>. Powiązanie określa HTTP jako transportu, interoperacyjne zabezpieczeń i inne szczegóły konfiguracji.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Utwórz i skonfiguruj projekt aplikacji konsoli dla klienta platformy WCF.
> - Dodaj odwołanie do usługi WCF do generowania plików klasy i konfiguracji serwera proxy aplikacji klienckiej usługi.

Przejdź do następnego samouczka, aby dowiedzieć się, jak za pomocą wygenerowanego klienta.

> [!div class="nextstepaction"]
> [Samouczek: Za pomocą klienta WCF](how-to-use-a-wcf-client.md)


